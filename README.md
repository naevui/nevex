# Nevex

Nevex is a register-based instruction set architecture (ISA) designed from scratch, together with a virtual machine, an assembler and, as a later step, a compiler for a small C-like language. The long-term goal is to move the ISA onto real hardware (FPGA) and run a simple operating system on it.

[Türkçe](README.tr.md)

> The project was first planned as "Vex". The name was changed to Nevex because of collisions with VexRiscv and the HP VEX ISA.

## Why

Most hobby VMs stop at a stack machine. Nevex uses a register architecture instead, closer to the design philosophy of RISC-V and ARM, so that the same specification can later be implemented in hardware without redesign. It serves as a testbed for ISA design decisions that can be checked on a VM first and on silicon later.

## Design constraints

- **Register-based**, RISC-V/ARM style, not stack-based.
- **Flat memory.** No MMU, no virtual memory.
- **Two privilege levels:** user mode and kernel mode, and nothing beyond that.

The constraints are deliberate. The architecture is kept minimal so that the VM and a future FPGA implementation can behave identically.

## Components

| Component | Source | Status |
|---|---|---|
| ISA specification | `ISA.md`, `isa.h` | In repo |
| Virtual machine (C) | `nevex.c` | In repo |
| Assembler | `nevexas.c` | In repo |
| Compiler (C-like language) | none yet | Planned |
| Nevex OS | none yet | Planned |
| FPGA implementation (Verilog/VHDL) | none yet | Planned |

`nevexas.asm` is a sample assembly program, and `examples/` holds further programs.

## Build

```sh
git clone https://github.com/naevui/nevex.git
cd nevex
make
```

## Roadmap

1. Freeze the ISA specification (register count, instruction formats, opcode table)
2. VM: fetch-decode-execute loop
3. Assembler
4. Compiler for a small C-like language
5. Nevex OS: user/kernel separation, basic syscall interface
6. FPGA port

## Contributing

The project is at an early stage. Issues and discussion about ISA design and architectural decisions are welcome.

## License

Not yet chosen. The project is intended to be open source.
