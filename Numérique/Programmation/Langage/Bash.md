---
title: Bash
description: 
published: true
date: 2024-05-21T18:16:38.768Z
tags: 
editor: markdown
dateCreated: 2024-05-21T18:16:38.768Z
---

# Bash

## Modèle de script

- <https://gitnet.fr/deblan/shell-base/src/branch/main/script>

## Wildcard

For easely navigate with files.

- `*` : all string

```bash
ls a* # all files begin with 'a'
ls *.txt # all files ended with '.txt'
```

- `?` : any char, but only one

```bash
ls t?t? # for example : titi, toto, tata
ls hello.??? # all files with name "hello"
```

- `[]` : a pattern of char
	- `[0-9]` : all digit
    - `[057]` : digit 0, or 5, or 7
```bash
ls [0-9]*.txt # all files with digits
ls [a-p0-5]*.* # files with char 'a' to 'p' & digit '0' to '5'
```

Some helpers :

| class | Purpose
|---|---
| [:alpha:] | It is used to match with any uppercase and lowercase letter and equivalent to [a-zA-Z].
| [:digit:] | It is used to match with any digits and is equivalent to [0-9].
| [:alnum:] | It is used to match any alphabet and digit. It is equivalent to [a-zA-Z].
| [:upper:] | It is used to match with uppercase latter only and equivalent to [A-Z]
| [:lower:] | It is used to match with uppercase latter only and equivalent to [a-z]
| [:blank:] | It is used to match with space and tab.
| [:print:] | It is used to match with printable characters.
| [:cntrl:] | It is used to match with non-printable characters.
| [:space:] | It is used to match with while-space.
| [:xdigit:] | It is used to match with hexadecimal digits.
| [:ascii:] | It is used to match with ASCII characters.
| [:word:] | It is used to alphanumeric characters including underscore(_).

Example :

```bash
cat /sys/devices/system/cpu/cpu[[:digit:]]*/power/energy_perf_bias
# cpu{0,1,2,3,4...}
```