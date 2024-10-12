# Vulnerability-inspection-with-GDB
## Some basic concepts about assembly language and registers
### What is Assembly Language?
Assembly language is a low-level programming language that provides a direct interface with a computer's hardware. 
It is much closer to machine code (binary) than high-level languages like Python or C which makes it more powerful and complex.
Each assembly language instruction corresponds to a specific machine code instruction making it architecture-dependent.
In assembly you write instructions that the CPU executes directly. 
Each instruction performs a basic operation like moving data, performing arithmetic or managing control flow
### Common instructions 
`mov`: Move data from one location to another.

`add`: Add two numbers.

`sub`: Subtract one number from another.

`jmp`: Jump to a different part of the program.

### Registers in Assembly
Registers are small fast storage locations within the CPU. 
They are used to hold data temporarily during computations. 
Different architectures have different registers
but let’s focus on some common x86 registers:


- General-Purpose Registers :

`EAX`: Often used to store return values from functions or results of arithmetic operations.

`EBX`: Can be used as a base pointer for memory addressing.

`ECX`: Commonly used as a counter in loops.

`EDX`: Used in operations involving division or multiplication.

| In 64-bit assembly, these registers are extended to RAX, RBX, RCX, and RDX |

- Index and Pointer Registers : They help  with memory access

`ESI/EDI`: Source and destination index registers used for operations that involve moving data between memory locations.
`EBP/ESP`: Base pointer and stack pointer registers used to manage the call stack (function parameters, local variables).
`EIP`: Instruction pointer that holds the address of the next instruction to be executed.

- Segment Registers
In older x86 architectures segment registers (like CS, DS, ES, SS) were used to handle different memory segments.
They play a less significant role in modern programming

![image](https://github.com/user-attachments/assets/d3ee511a-a49d-48d0-a529-86f4e91bfe4d)

source: https://microcontrollerslab.com/8086-microprocessor-architecture/

### The Stack
The stack is a region of memory used for storing temporary data such as function parameters, return addresses and local variables:

Push: Adds data to the top of the stack (decreases ESP).
Pop: Removes data from the top of the stack (increases ESP).

The stack grows downward in memory (towards lower addresses) meaning that when data is pushed onto the stack, the stack pointer (ESP) decreases.

### Memory Addressing Modes
- Immediate Addressing: The operand is a constant value `mov eax, 5`

- Register Addressing: The operand is a register `mov eax, ebx`

- Direct Addressing: Access memory directly by specifying an address `mov eax, [0x00400000]`

- Indirect Addressing: Use a register to point to a memory address `mov eax, [ebx]`

### Control Flow  
Control flow instructions determine the order in which code is executed:
`jmp`: Unconditional jump to a specified address.
`call`: Calls a function, pushing the return address onto the stack.
`ret`: Returns from a function by popping the return address off the stack.
