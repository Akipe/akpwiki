---
title: API REST
description: 
published: true
date: 2024-05-21T16:29:45.595Z
tags: 
editor: markdown
dateCreated: 2024-05-21T16:29:45.595Z
---

# API REST

## URLs

| API | Description | Corps de la demande | Response body |
|---|---|---|---|
| GET /api/todoitems | Obtenir toutes les tâches | Aucune | Tableau de tâches
| GET /api/todoitems/{id} | Obtenir un élément par ID | Aucune | tâches
| POST /api/todoitems | Ajouter un nouvel élément | Tâche | Tâche
| PUT /api/todoitems/{id} | Mettre à jour un élément existant (toute la donnée doit être envoyé) | Tâche | Aucune
| PATCH /api/todoitems/{id} | Mettre à jour un élément existant (uniquement les nouvelles données envoyé) | Tâche | Aucune
| DELETE /api/todoitems/{id} | Supprimer un élément | Aucune | Aucune


## Liste des retours HTTP
<https://www.restapitutorial.com/lessons/httpmethods.html>

## IDE

Pour faire des API en C#, nous allons utilisé un ORM : **Entity Framework**.

### Visual Studio

### Ajout d'un projet

> Nouveau projet > (rechercher *API Web*) API Web ASP.NET Core

Tutoriel pour apprendre à faire des APIs : [https://docs.microsoft.com/en-us/aspnet/core/tutorials/first-web-api?view=aspnetcore-6.0&tabs=visual-studio](https://docs.microsoft.com/en-us/aspnet/core/tutorials/first-web-api?view=aspnetcore-6.0&tabs=visual-studio)

Installation de dépendances Nuget :

1. interface Visual Studio
Tools > Nuget Package Manager > Manage Nuget for project...

Séléctionner les modules suivants :
- EntityFrameworkCore
- EntityFrameworkCore.SqlServer
- EntityFrameworkCore.Design

### Modèle

Un modèle correspond à la modélisation des données.

Ajouter un dossier nommé `Models` dans le projet,  
Ajouter une class au nom de la table.

```c#
namespace TodoApi.Models
{
    public class TodoItem
    {
        public long Id { get; set; } // Identifiant de la table
        public string? Name { get; set; }
        public bool IsComplete { get; set; }
    }
}
```

### Database context

C'est la classe principal qui coordonne les fonctionnalités d'Entity Framework, notamment pour les entités.
Classe dérivé : [https://docs.microsoft.com/en-us/dotnet/api/microsoft.entityframeworkcore.dbcontext?view=efcore-6.0](https://docs.microsoft.com/en-us/dotnet/api/microsoft.entityframeworkcore.dbcontext?view=efcore-6.0)

Paquets NuGet à installer :
- Microsoft.EntityFrameworkCore.InMemory

Ajouter un database context :  
Ajouter une classe dans `Models` > TodoContext

```c#
using Microsoft.EntityFrameworkCore;
using System.Diagnostics.CodeAnalysis;

namespace TodoApi.Models
{
    public class TodoContext : DbContext
    {
        public TodoContext(DbContextOptions<TodoContext> options)
            : base(options)
        {
        }

        public DbSet<TodoItem> TodoItems { get; set; } = null!;
    }
}
```

### Ajouter du Database Context dans Program.cs
```c#
// Début ajout
using Microsoft.EntityFrameworkCore;
using TodoApi.Models;
// Find ajout


var builder = WebApplication.CreateBuilder(args);

// Add services to the container.

builder.Services.AddControllers();
// Début ajout
builder.Services.AddDbContext<TodoContext>(opt =>
    opt.UseInMemoryDatabase("TodoList"));
//builder.Services.AddSwaggerGen(c =>
//{
//    c.SwaggerDoc("v1", new() { Title = "TodoApi", Version = "v1" });
//});
// Fin ajout

var app = builder.Build();

// Configure the HTTP request pipeline.
if (builder.Environment.IsDevelopment())
{
    app.UseDeveloperExceptionPage();
  	// Début ajout
    //app.UseSwagger();
    //app.UseSwaggerUI(c => c.SwaggerEndpoint("/swagger/v1/swagger.json", "TodoApi v1"));
  	// Fin ajout
}

app.UseHttpsRedirection();

app.UseAuthorization();

app.MapControllers();

app.Run();
```

### Controlleur

Clique droit sur Controller > New Scaffolded Item > API Controller with actions, using Entity Framework > Add
> TodoItem as Model class
> TodoContext as Data context class
> Add

### DTO (Data Transfer Object)

C'est un sous ensemble d'un modèle, qui permet de limiter les entrées et sorties de données par rapport à un modèle.  
Le DTO existe car le modèle doit rester similaire à cette de la base de données.
- Empécher la re-enregistrement de données.
- Cacher les propriétés que les clients ne doivent pas avoir accés.
- Retirer certaines propriétés pour réduire la taille des variables.

#### Example

Entité :
```c#
namespace TodoApi.Models
{
    public class TodoItem
    {
        public long Id { get; set; }
        public string? Name { get; set; }
        public bool IsComplete { get; set; }
        public string? Secret { get; set; }
    }
}
```

Modèle DTO, sans l'accès au secret :
```c#
namespace TodoApi.Models
{
    public class TodoItemDTO
    {
        public long Id { get; set; }
        public string? Name { get; set; }
        public bool IsComplete { get; set; }
    }
}
```

Controlleur :
```c#
// GET: api/TodoItems
[HttpGet]
public async Task<ActionResult<IEnumerable<TodoItemDTO>>> GetTodoItems()
{
	return await _context
      	.TodoItems
		.Select(x => ItemToDTO(x))
		.ToListAsync();
}
// ...
private static TodoItemDTO ItemToDTO(TodoItem todoItem) =>
  new TodoItemDTO
  {
  	Id = todoItem.Id,
  	Name = todoItem.Name,
  	IsComplete = todoItem.IsComplete
  };
```

### Web frontend inside Visual studio

Créer un dossier **wwwroot** à la racine du projet.

Ajouter au fichier `Program.cs` :
```c#
app.UseDefaultFiles();
app.UseStaticFiles();
```

### Astuces

### ActionResult

Utilisé comme type de retour pour les API (json) : `ActionResult<T> type`.  
Exemple de méthodes de retours :
- GetTodoItem : retourn 200 avec JSON avec un **item**. 404 si pas d'item. 

#### Changer path API

Dans *Properties\launchSettings.json* :
```json
"launchUrl": "swagger",
```
Par contre swagger sera supprimer.


#### Commandes terminal NuGet

| Commande | Information
|---|---
|Get-Help entityframework |	Displays information about entity framework commands.
|Add-Migration <migration name> |	Creates a migration by adding a migration snapshot.
|Remove-Migration |	Removes the last migration snapshot.
|Update-Database |	Updates the database schema based on the last migration snapshot.
|Script-Migration |	Generates a SQL script using all the migration snapshots.
|Scaffold-DbContext |	Generates a DbContext and entity type classes for a specified database. This is called reverse engineering.
|Get-DbContext |	Gets information about a DbContext type.
|Drop-Database |	Drops the database.

## Outils

### OpenAPI

Norme concernant la présentation et la documentation pour les API REST.

### PostMan

Outil pour faire du débug d'API.