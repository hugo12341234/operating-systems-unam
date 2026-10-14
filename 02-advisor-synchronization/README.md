# Students & Advisor — Thread Synchronization

A solution to a variant of the *sleeping barber* problem using Python threads and semaphores.

## The problem

A professor holds office hours for several students:

- The office has **x chairs**. When nobody is waiting, the professor takes a nap.
- Students may knock at any time, but no more than **x** can be inside; if all chairs are taken, the student leaves.
- To avoid confusing the professor, **only one student asks a question at a time** while the others wait for their turn.

## Synchronization strategy

| Primitive | Type | Purpose |
|---|---|---|
| `mutex` | Binary semaphore | Mutual exclusion on the shared counter `sillas_disponibles`, avoiding race conditions when students sit down or the advisor frees a chair |
| `alumnos_esperando` | Counting semaphore (starts at 0) | Signals the advisor that someone needs help; the advisor sleeps on it while nobody is waiting |
| `asesor_disponible` | Binary semaphore | Hands the turn to exactly one student, so only one is served at a time |

The program prints a live event table (event, advisor state, free chairs). Press `Ctrl+C` to stop it.

## Run it

Requires Python 3 (any OS).

```bash
python3 asesor.py
```

```text
=================================================================
ALUMNO / EVENTO           | ESTADO ASESOR        |  SILLAS LIBRES
=================================================================
Alumno 0 se sienta        | ---                  |        2
Atendiendo alumno         | OCUPADO              |        3
Terminó asesoría          | DURMIENDO...         |        3
Alumno 2 se sienta        | ---                  |        2
```

## Possible improvements

- Refresh the table in place instead of printing new rows indefinitely.

*Authors: Hugo Chacón, Sebastián Valdez.*
