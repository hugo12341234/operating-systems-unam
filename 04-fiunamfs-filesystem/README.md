# FiUnamFS — Multithreaded Micro File System

A Python tool that reads and modifies **FiUnamFS**, a simple educational file system stored in a disk image (`fiunamfs.img`). It works directly with bytes and offsets, just like a real file system driver.

## Features

Interactive menu with five operations:

1. **Analyze the superblock** — read and validate the file system metadata (identifier, version, label, cluster size, directory clusters, total clusters).
2. **List the directory** — show valid entries with name, size, starting cluster, and creation and modification dates.
3. **Copy from FiUnamFS to the computer** — locate a file in the image and rebuild it on the local system.
4. **Copy from the computer to FiUnamFS** — find enough **contiguous free clusters** and a free directory entry, then write the file into the image.
5. **Delete a file** — logical deletion: the directory entry is marked as free so its space can be reused.

## Operating systems concepts

- **Storage layout:** superblock in cluster 0, directory in clusters 1–8 (64-byte entries), data from cluster 9 on; 2,048-byte clusters.
- **Binary parsing:** `struct` with little-endian 32-bit integers (`<I`) at fixed offsets.
- **Concurrency:** a dedicated **logger thread** consumes messages from a thread-safe FIFO `queue.Queue`.
- **Synchronization:** a `threading.Lock` protects every read and write on the shared disk image.

Only the Python standard library is used (`struct`, `threading`, `queue`, `os`, `math`, `datetime`).

## Run it

Requires Python 3. The program expects the disk image **one level above** the `src` folder, so place [`fiunamfs.img`](https://github.com/unamfi/sistop-2026-2/blob/main/proyectos/1/fiunamfs.img) from the course repository here:

```text
04-fiunamfs-filesystem/
├── fiunamfs.img      ← disk image (not included)
└── src/
    └── LeerArchivo.py
```

```bash
cd 04-fiunamfs-filesystem/src
python3 LeerArchivo.py
```

> Work on a copy of the image: options 4 and 5 modify it.

Example (listing the directory):

```text
================ DIRECTORIO ================
Nombre           | Tamaño     | Cluster    | Creación             | Modificación
-----------------------------------------------------------------------------------------------
README.org       | 31094      | 10         | 2026-05-12 21:32:40  | 2026-05-12 21:32:40
logo.png         | 126423     | 26         | 2026-05-12 21:32:40  | 2026-05-12 21:32:40
mensaje.jpg      | 180808     | 88         | 2026-05-12 21:32:40  | 2026-05-12 21:32:40
```

*Authors: Hugo Chacón, Sebastián Valdez.*
