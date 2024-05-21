---
title: Ratchet
description: 
published: true
date: 2024-05-21T18:47:19.173Z
tags: 
editor: markdown
dateCreated: 2024-05-21T18:47:19.173Z
---

# Ratchet

Server de websocket écrit en PHP.

## Exemple

```php
<?php
// WebChat.php

namespace App\Service;

use Exception;
use Ratchet\MessageComponentInterface;
use Ratchet\ConnectionInterface;
use SplObjectStorage;

class WebChat implements MessageComponentInterface
{
    protected SplObjectStorage $clients;

    public function __construct()
    {
        $this->clients = new SplObjectStorage();
    }

    public function onOpen(ConnectionInterface $connection)
    {
        $this->clients->attach($connection);

        echo "New connection! ($connection->resourceId)\n";
    }

    public function onMessage(ConnectionInterface $clientSender, $message)
    {
        $numberClients = count($this->clients) - 1;

        echo "Connection $clientSender->resourceId";
        echo " sending message $message to";
        echo " $numberClients other connection(s)\n";

        foreach ($this->clients as $client) {
            // Send to all clients but not me
            if ($clientSender !== $client) {
                $client->send(
                    "id $clientSender->resourceId: $message");
            }
        }
    }

    public function onClose(ConnectionInterface $connection)
    {
        // The connection is closed, remove it, as we can no longer send it messages
        $this->clients->detach($connection);

        echo "Connection {$connection->resourceId} has disconnected\n";
    }

    public function onError(ConnectionInterface $connection, Exception $e)
    {
        echo "An error has occurred: {$e->getMessage()}\n";

        $connection->close();
    }
}
```

```php
<?php
// WebSocket.php
  
namespace App\Service;

use Ratchet\Server\IoServer;
use App\Service\WebChat;
use Ratchet\Http\HttpServer;
use Ratchet\WebSocket\WsServer;

class WebSocket
{
    public function __construct()
    {
        $server = IoServer::factory(
            new HttpServer(
                new WsServer(new WebChat())
            ),
            8080
        );

        $server->run();

    }
}
```

```js
// websocket.js
'use strict'

let websocketURL = '127.0.0.1:8080';

let elementConnectionStatus = document.getElementById('websocket-connection-status')
let elementMessageReceive = document.getElementById('websocket-message-receive')
let elementForm = document.getElementById('form-message-sender')
let elementMessageSend = document.getElementById('websocket-message-send')

let websocket = new WebSocket('ws://' + websocketURL)

websocket.onopen = () => {
    //websocket.send('Hello')

    elementConnectionStatus.innerHTML = "Connected !"
};

websocket.onmessage = (event) => {
    elementConnectionStatus.innerHTML = "Connected - Message receive"
    elementMessageReceive.innerHTML += event.data + "<br \>"
};

websocket.onclose = () => {
    elementConnectionStatus.innerHTML = "Connection closed"
};

websocket.onerror = () => {
    elementConnectionStatus.innerHTML = "An error occured!"
};

elementForm.addEventListener('submit', (event) => {
    event.preventDefault();
    
    websocket.send(elementMessageSend.value)
});
```

```html
{# webchat.html.twig #}
{% extends 'base.html.twig' %}

{% block body %}
  <div class="container">
    <h1>Test WebSockets and Symfony</h1>

    <dl>
        <dt>Status de la connexion :</dt>
        <dd id="websocket-connection-status">Non connecté</dd>
        <dt>Message reçu :</dt>
        <dd id="websocket-message-receive"></dd>
    </dl>

    <form id="form-message-sender">
        <input type="text" id="websocket-message-send" name="websocket-message-send" placeholder="Message to send">
        <button type="submit">Send message</button>
    </form>
  </div>
{% endblock %}

{% block javascripts %}
    <script src="websocket.js" defer></script>
{% endblock %}
```
