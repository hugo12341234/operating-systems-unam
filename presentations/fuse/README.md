# How FUSE Works Internally

Class presentation for the Operating Systems course about **FUSE (Filesystem in Userspace)**: the kernel module and framework that lets unprivileged users build and mount their own file systems in user space, without modifying the kernel.

Topics covered:

- What FUSE is and the problem it solves (writing file systems without kernel programming)
- Internal architecture: user application, FUSE kernel module and user-space daemon
- Request flow: system call → kernel VFS → FUSE module → `/dev/fuse` → user-space daemon → response
- The FUSE API (`getattr`, `readdir`, `open`, `read`, `write`, `mkdir`, `unlink`)
- Advantages and drawbacks, kernel file systems vs. FUSE, and security

Files:

- [Slides (PDF)](fuse-internals-slides.pdf)
- [Summary handout (PDF)](fuse-internals-summary.pdf)

*Presented by José Manuel Ferrer Cordero and Hugo Emmanuel Chacón Jaral.*
