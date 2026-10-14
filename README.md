# Operating Systems — Projects & Assignments

![Python](https://img.shields.io/badge/Python-3-3776AB?logo=python&logoColor=white)
![C++](https://img.shields.io/badge/C++-00599C?logo=cplusplus&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?logo=linux&logoColor=black)

Hands-on work from the **Operating Systems** course (Faculty of Engineering, UNAM · Semester 2026-II): processes, concurrency and synchronization, CPU scheduling and file systems.

| # | Project | Topic | Language |
|---|---|---|---|
| 1 | [Mini Shell](01-mini-shell) | Process creation with `fork()`, `execvp()`, `waitpid()` and signal handling | Python |
| 2 | [Students & Advisor](02-advisor-synchronization) | Thread synchronization with semaphores (sleeping-advisor problem) | Python |
| 3 | [CPU Scheduling Simulator](03-cpu-scheduling) | FCFS, Round Robin (q=1, q=4), SPN and multilevel feedback, compared on random workloads | C++ |
| 4 | [FiUnamFS File System](04-fiunamfs-filesystem) | Multithreaded tool that reads and writes a FiUnamFS disk image: superblock, directory, copy in/out, delete | Python |
| — | [How FUSE works internally](presentations/fuse) | Class presentation on Filesystem in Userspace | Slides (PDF) |

Each folder has its own README explaining the problem, the approach and how to run it.

> Source code comments and program output are in Spanish, as the work was developed for a course at UNAM.

## Highlights

- **Processes:** a working Unix shell that creates child processes, runs real commands, reports unknown commands and survives `Ctrl+C`.
- **Concurrency:** a classic synchronization problem solved with a mutex and counting semaphores to avoid race conditions.
- **Scheduling:** a simulator that generates random process loads and compares turnaround time (T), waiting time (E) and penalty ratio (P) across five algorithms, with an execution timeline for each.
- **File systems:** byte-level parsing of a disk image with `struct` (little-endian offsets), contiguous cluster allocation, logical deletion, and a logger thread fed through a thread-safe queue with a lock protecting the image.

## Team

- **Hugo Emmanuel Chacón Jaral** — [@hugo12341234](https://github.com/hugo12341234)
- **Sebastián Valdez** — co-author of projects 1–4
- **José Manuel Ferrer Cordero** — co-presenter of the FUSE talk

Course: *Sistemas Operativos*, taught by Gunnar Wolf. The original submissions live in the course repository, [unamfi/sistop-2026-2](https://github.com/unamfi/sistop-2026-2).
