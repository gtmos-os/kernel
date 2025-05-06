# GT-MOS Operating System
GT-MOS is an x86_64 POSIX-compliant operating system in C. This is a fork of [cavOS](https://github.com/malwarepad/cavOS) by MalwarePad with a customised userspace.

[![GitHub top language](https://img.shields.io/github/languages/top/gtmos-os/kernel?logo=c&label=)](https://github.com/gtmos-os/kernel/blob/master/src/kernel/Makefile)
[![GitHub license](https://img.shields.io/github/license/gtmos-os/kernel)](https://github.com/gtmos-os/kernel/blob/master/LICENSE)
[![GitHub contributors](https://img.shields.io/github/contributors/gtmos-os/kernel)](https://github.com/gtmos-os/kernel/graphs/contributors)
[![GitHub commit activity](https://img.shields.io/github/commit-activity/m/gtmos-os/kernel)](https://github.com/gtmos-os/kernel/commits)

<details><summary>Original cavOS readme</summary>

## Preview of the OS
![Preview of the OS](https://raw.malwarepad.com/cavos/images/preview4.png)
![Preview of the OS](https://raw.malwarepad.com/cavos/images/preview5.png)

## Kernel status
The cavOS kernel is a monolithic x86_64 one written in relatively simple C with a few bits of Intel assembly here and there. It uses the Limine bootloader and leverages the FAT32 filesystem for booting along with Ext2 for the root partition. I try to keep the code structure clean and fairly easy to understand, while avoiding too much abstraction. Hence, code quality and clarity are sometimes prioritized over performance gains.

- x86_64 pre-emptive kernel that is Unix-like and POSIX-compliant
- Architecture features fully supported (GDT, IDT, ISR, (I/O)APIC, SSE, LAPIC timer, RTC clock, `syscall` instruction)
- ACPI mode, using I/O APIC redirects for interrupts
- PCI scanning and various PCI device drivers
- Full network stack (including TCP and DHCP) with network interface support (Realtek RTL8139/RTL8169)
- Two-way pipes, Unix domain sockets (AF_UNIX) and signal support (with some BSD extensions)
- FAT32, Ext2 and virtual file systems (/proc, /sys, /dev, etc)
- PS/2 Keyboard/Mouse drivers along with serial port (COM1, COM2, etc) output
- ELF64 binary loading, dynamic linking and shared libraries
- Musl libc, Linux system call layer, pre-emptive multitasking
- Primitive kernel tty with 8-bit color, some basic ANSI codes and psf1 fonts
- BIOS/UEFI framebuffer utilization and exposure to userland via /dev/fb0

## Userspace status
Userspace is my primary focus at the time being, with the kernel being *quite* stable. I'm trying to make this OS as close to Linux as I can, while adding my own stuff on top of it. This is visible with the system calls that are exactly like Linux's. That isn't random, I want cavOS to be as binary compatible with it as possible!

As far as the actual implementation goes, I'm using the `apk` package manager from Alpine Linux and their respective repositories for userspace assembly. Alpine's & musl's philosophy align with the cavOS one and I really see no point in recompiling stuff myself if I don't necessarily have to.

## Is this a Linux distribution?
No! The cavOS kernel does not share source code or headers with Linux. Some header definitions are obviously present but that is just to support the userspace. Internally the cavOS kernel doesn't have much in common with Linux other than the fact that it's monolithic. This layout may change in the future with cavOS-specific extensions being added as well.

</details>

## Documentation
- **Contributing:** Information about contribution guidelines & suggestions [docs/contributing.md](docs/contributing.md)
- **Compiling:** Information about building the OS correctly & cleaning unused binaries [install.md](docs/install.md)

## Credits
- [cavOS](https://github.com/malwarepad/cavOS): Amd64 operating system in C. Trying to make a full OS, with a simple and readable codebase!
- [Limine](https://github.com/limine-bootloader/limine): Modern, advanced, portable, multiprotocol bootloader and boot manager
- [uACPI](https://github.com/uACPI/uACPI): A portable and easy-to-integrate implementation of the ACPI
- [Alpine Package Keeper](https://wiki.alpinelinux.org/wiki/Alpine_Package_Keeper): Alpine Linux's package management solution and official repositories
- [lwIP](https://savannah.nongnu.org/projects/lwip/): A small independent implementation of the TCP/IP protocol suite 
- [dlmalloc](https://gee.cs.oswego.edu/pub/misc/): Doug Lea's Memory Allocator, a good all purpose memory allocator that is widely used and ported
- [eyalroz/printf](https://github.com/eyalroz/printf): Tiny, fast(ish), self-contained, fully loaded printf, sprinf etc. implementation
- [G-9](https://nr9.online/): Made the ASCII art for the kernel shell's `fetch` command

## License
This project is licensed under GPL v3 (GNU General Public License v3.0). For more information go to the [LICENSE](LICENSE) file.
