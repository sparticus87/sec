**Buffer Overflow Common Terms**
**Heap**
Memory that can be allocated and deallocated
**Stack**
A contiguous section of memory used for passing arguments
**Registers**
Storage elements as close as possible to the central processing unit (CPU)
**Instruction Pointer (IP)**
a.k.a Program Counter (PC), contains the address of next instruction to be executed
**Stack Pointer (SP)**
Contains the address of the next available space on the stack (points to the top)
**Base Pointer (BP)**
The base of the stack  (points to the bottom)
**Function**
Code that is separate from the main program that is often used to replace code the repeats in order to make the program smaller and more efficient
**Shellcode**
The code that is executed once an exploit successfully takes advantage of a vulnerability
''' ''' ''' ''' ''' ''' ''' ''' ''' ''' '''
**Buffer Overflow Defenses**
    **Non executable (NX) stack**
      a stack that is marked as non-executable, meaning that it cannot be utilized to store or execute code
    **Address Space Layout Randomization (ASLR)**
      randomize the memory addresses where a program's code, data, and heap are loaded
    **Data Execution Prevention (DEP)**
      marks certain areas of your computer's memory as non-executable, preventing code from running from those areas.
    **Stack Canaries**
      are a secret value placed on the stack which changes every time the program is started
    **Position Independent Executable (PIE)**
      executable binaries made entirely from position-independent code

**Utilizing tools such as:**
    IDA, GHIDRA
    GDB, MONA, IMMUNITY
    BASH, PYTHON

**GDB Uses**
Installation of Peda Plugin
git clone https://github.com/longld/peda.git ~/peda
echo "source ~/peda/peda.py" >> ~/.gdbinit
**Common Commands**
disass <FUNCTION>   #   Disassemble portion of the program
info <...>  #   Supply info for specific stack areas
x/256c $<REGISTER>  #   Read characters from specific register
break <address>  #   Establish a break point


























































































