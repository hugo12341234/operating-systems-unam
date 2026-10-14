# Mini Shell in Python

A small Unix shell that reads commands from an interactive prompt and runs them as child processes using the same system calls a real shell uses.

## What it does

- Shows an interactive prompt (`mi_minishel$`).
- Creates a child process with **`fork()`** for each command.
- Replaces the child with the requested program using **`execvp()`**, so real commands like `ls`, `pwd` or `whoami` work with their arguments.
- The parent waits with **`waitpid()`**, which prevents zombie processes.
- Prints a clear message when a command does not exist.
- Handles **`SIGINT` (Ctrl+C)** so the shell does not die; type `exit` to quit.
- Ignores empty input.

## Run it

Requires Python 3 on a Unix-like system (Linux or macOS), since `fork()` is not available on Windows.

```bash
python3 minishell.py
```

```text
--- Bienvenido al Mini-Shell Sistop 2026-2 ---
mi_minishel$ pwd
/home/user
mi_minishel$ foo
Error: El comando 'foo' no fue encontrado.
mi_minishel$ exit
Saliendo del shell...
```

## Challenges

- Some commands initially failed because the input was not split correctly into the command and its arguments.
- Pressing Enter on an empty line tried to execute an empty command; we now skip empty input.
- Unknown commands ended the child without a useful message; exception handling now reports the error clearly.

*Authors: Hugo Chacón, Sebastián Valdez.*
