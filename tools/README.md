# Host debugging tools for Prusa MK3 firmware

## Tools

### ``dump_eeprom``

Dump the content of the entire EEPROM using the D3 command.
Requires ``printcore`` from [Pronterface].

### ``dump_sram``

Dump the content of the entire SRAM using the D2 command.
Requires ``printcore`` from [Pronterface].

### ``elf_mem_map``

Generate a symbol table map starting directly from an ELF firmware with DWARF2 debugging information (which is the default using the stock board definition).

When used along with a memory dump obtained from the D2 g-code, show the value of each symbol which is within the address range.

This assumes the running firmware generating the dump and the elf file are the same.
Requires Python3 and the [pyelftools](https://github.com/eliben/pyelftools) module.

### ``update_eeprom``

Given one EEPROM dump, convert the dump to update instructions that can be sent to a printer.

Given two EEPROM dumps, produces only the required instructions needed to update the contents from the first to the second. This is currently quite crude and assumes dumps are aligned (starting from the same address or same stride).

Optionally writes the instructions to the specified port (requires ``printcore`` from [Pronterface]).

### ``noreset``

Set the required TTY flags on the specified port to avoid reset-on-connect for *subsequent* requests (issuing this command might still cause the printer to reset).


[Pronterface]: https://github.com/kliment/Printrun