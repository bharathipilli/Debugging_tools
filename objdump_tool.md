# OBJDUMP Tool - Detailed Guide

## 1. Introduction
`objdump` is a GNU Binary Utilities (binutils) tool used for displaying information from object files, executables, shared libraries, and core dumps. It can show headers, sections, symbols, disassembly, and much more.

## 2. Common Uses
- Inspect ELF headers and section tables
- Disassemble binaries into assembly code
- View symbol tables (functions, variables)
- Debugging with static analysis
- Reverse engineering compiled code
- Checking relocation and dynamic linking info

## 3. Syntax
```bash
objdump [options] <object-file>
```

## 4. Common Options
| Option | Description |
|--------|-------------|
| `-d` | Disassemble the executable sections |
| `-D` | Disassemble all sections |
| `-S` | Disassemble and intermix source code (if available) |
| `-x` | Display all headers |
| `-h` | Display section headers |
| `-t` | Display the symbol table |
| `-r` | Display relocation entries |
| `-s` | Display full contents of sections |
| `-j <name>` | Display only the named section |
| `-C` | Demangle C++ symbol names |

## 5. Examples
### Example 1: Disassemble an executable
```bash
objdump -d a.out
```
Shows disassembly of executable sections.

### Example 2: Disassemble with source code
```bash
objdump -S a.out
```
Shows disassembly along with original source (if debug info is present).

### Example 3: View symbol table
```bash
objdump -t a.out
```

### Example 4: View section headers
```bash
objdump -h a.out
```

### Example 5: Dump specific section
```bash
objdump -s -j .rodata a.out
```

---

# OBJDUMP Interview Questions and Answers

## Basic Questions
1. **What is objdump?**  
   A command-line tool in GNU binutils used to display various information about object files, executables, and libraries.

2. **How does objdump differ from GDB?**  
   `objdump` is a static analysis tool (no execution), while GDB is an interactive debugger for runtime analysis.

3. **What does `objdump -d` do?**  
   Disassembles executable sections of the file.

4. **How to disassemble all sections of a binary?**  
   Use `objdump -D <file>`.

5. **How to see both source code and assembly?**  
   Use `objdump -S <file>` (requires debug symbols).

6. **How to view ELF section headers?**  
   Use `objdump -h <file>`.

7. **How to view symbol table?**  
   Use `objdump -t <file>`.

8. **How to demangle C++ names in objdump output?**  
   Use `-C` option.

9. **What is `.text` section in objdump output?**  
   It contains the executable machine code.

10. **What is `.data` section?**  
    Contains initialized global and static variables.

## Intermediate Questions
11. **How to examine relocation entries?**  
    Use `objdump -r <file>`.

12. **What is `.rodata` section?**  
    Read-only data section, usually string literals.

13. **What does `.bss` section contain?**  
    Uninitialized global and static variables.

14. **How to dump raw bytes of a section?**  
    Use `objdump -s -j <section>`.

15. **How to analyze shared library symbols?**  
    Use `objdump -T libfile.so`.

16. **How to check file architecture?**  
    Use `objdump -f <file>`.

17. **What is the difference between `-t` and `-T`?**  
    `-t` shows static and global symbols from symbol table, `-T` shows dynamic symbols.

18. **How can objdump help in reverse engineering?**  
    It can reveal assembly code and function boundaries from compiled binaries.

19. **What does `-M intel` do in objdump?**  
    Formats disassembly output in Intel syntax.

20. **How to limit disassembly to specific section?**  
    Use `-j <section>` option.

## Advanced Questions
21. **How can objdump help detect compiler optimizations?**  
    By comparing expected assembly patterns with actual output.

22. **What is the `.plt` section?**  
    Procedure Linkage Table for dynamic function calls.

23. **What is the `.got` section?**  
    Global Offset Table used for dynamic linking.

24. **How to identify inline functions in objdump output?**  
    Look for code blocks without separate symbol table entries.

25. **Can objdump modify binaries?**  
    No, it's read-only for analysis.

26. **What is `.eh_frame` section?**  
    Contains exception handling and stack unwinding info.

27. **What does `.comment` section contain?**  
    Compiler version and build information.

28. **What is `.init` and `.fini`?**  
    Sections run before main() and after program exit.

29. **What is `.symtab`?**  
    Symbol table for static linking.

30. **What is `.dynsym`?**  
    Symbol table for dynamic linking.

## Practical Usage
31. **How to check entry point address?**  
    `objdump -f <file>`.

32. **How to find a specific function's assembly?**  
    `objdump -d <file> | grep -A20 <function>`.

33. **How to extract string constants?**  
    `objdump -s -j .rodata`.

34. **How to check if binary is stripped?**  
    If `objdump -t` shows no symbols, it's stripped.

35. **How to see relocation in shared libraries?**  
    `objdump -R libfile.so`.

36. **How to check ARM binary with objdump?**  
    Use `arm-none-eabi-objdump`.

37. **How to output assembly to a file?**  
    `objdump -d file > disassembly.txt`.

38. **Can objdump disassemble firmware images?**  
    Yes, if given correct architecture.

39. **What is `.text.startup` section?**  
    Contains startup routines before main().

40. **What is `.ctors` and `.dtors`?**  
    Constructor and destructor function tables.

## Expert-Level
41. **How to view dynamic linking info?**  
    `objdump -p file`.

42. **What is `.debug_info` section?**  
    Contains debug symbol information (DWARF).

43. **What is `.debug_line`?**  
    Maps assembly instructions to source lines.

44. **How to see opcode bytes with objdump?**  
    It's included in disassembly output.

45. **How to switch disassembly syntax?**  
    `objdump -M intel` or `objdump -M att`.

46. **What is `.rel.plt`?**  
    Relocation entries for PLT.

47. **What is `.gnu.version`?**  
    Versioning info for dynamic linking.

48. **How to identify syscalls?**  
    Look for `int 0x80` or `syscall` instructions.

49. **What is `.note.ABI-tag`?**  
    Identifies OS/ABI compatibility.

50. **How to check endian format of binary?**  
    `objdump -f` output.

51. **What is `.interp`?**  
    Path to dynamic linker.

52. **What is `.dynamic`?**  
    Dynamic linking information.

53. **What is `.hash` and `.gnu.hash`?**  
    Symbol hash tables for faster lookups.

---
