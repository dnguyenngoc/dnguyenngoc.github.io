---
title: Escaping strings in Bash
date: 2020-10-06
draft: true
aliases:
    - /notes/escaping-strings-in-bash.html
---

A couple of days ago,
An interesting thread came up on HN about [escaping string in Bash using !:q](https://news.ycombinator.com/item?id=24659282).

As [Pascal Hirsch](https://twitter.com/phphys/status/1311727268398465029) describes on Twitter,
the idea is simple: after an expression, use `!:q` to escape the given string.

```bash
$ # This string 'has single' "and double" quotes and a $
$ !:q
'# This string '\''has single'\'' "and double" quotes and a $'
bash: # This string 'has single' "and double" quotes and a $: command not found
```

### How does this work?

It starts with the history expansion character `!` (`!cmd` expands to the last `cmd` executed) followed by the quote modifier (`:q`).
A clever use of [history expansion](https://www.gnu.org/software/bash/manual/html_node/History-Interaction.html#History-Interaction) and [modifiers](https://www.gnu.org/software/bash/manual/html_node/Modifiers.html).

### Command Not Found

The `p` modifier will print the command without execution, avoiding the `command not found` error.

```bash
$ !:q:p
'# This string '\''has single'\'' "and double" quotes and a $'
```