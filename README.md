# 🖥️ Two-Pass Assembler — System Programming

A Python-based implementation of a **Two-Pass Assembler** developed as a System Programming project.

The project demonstrates how an assembler processes assembly language source code in two major phases:

1. **Pass 1** — analyzes the source program, assigns addresses, builds the Symbol Table, and generates an intermediate representation.
2. **Pass 2** — uses the generated Symbol Table and intermediate representation to resolve operands and generate machine-level object code.

The implementation focuses on fundamental assembler concepts including **location counters, symbol tables, instruction formats, opcodes, directives, addressing modes, hexadecimal address calculation, and object-code generation**.

---

## 📌 Project Overview

An assembler translates assembly language instructions into machine-readable object code.

A traditional two-pass assembler separates this process into two stages.

### Pass 1

Pass 1 scans the source program and:

- Maintains the Location Counter (LOCCTR)
- Identifies labels
- Builds the Symbol Table
- Calculates instruction addresses
- Processes assembler directives
- Generates an intermediate file for Pass 2

### Pass 2

Pass 2 uses the information generated during Pass 1 to:

- Resolve symbolic operands
- Retrieve instruction opcodes
- Calculate object-code addresses
- Handle immediate operands
- Handle indexed addressing
- Generate machine/object code
- Produce the final output

---

## 🎯 Objectives

The project was designed to demonstrate the internal workflow of an assembler and apply System Programming concepts including:

- Two-pass assembler architecture
- Symbol table construction
- Location counter management
- Opcode lookup
- Address calculation
- Assembly directives
- Object-code generation
- Immediate addressing
- Indexed addressing
- Hexadecimal conversion
- File-based intermediate processing

---

## 🏗️ System Architecture

```text
                 Assembly Source Program
                           │
                           ▼
                    ┌─────────────┐
                    │   Pass 1    │
                    └─────────────┘
                           │
              ┌────────────┴────────────┐
              ▼                         ▼
       Symbol Table              Intermediate File
              │                         │
              └────────────┬────────────┘
                           ▼
                    ┌─────────────┐
                    │   Pass 2    │
                    └─────────────┘
                           │
                           ▼
                  Object Code Output



🔄 Pass 1

Pass 1 is implemented primarily in Pass1.py.

The program reads the intermediate representation and processes assembly statements while maintaining the current memory address.

Main responsibilities
Initialize the location counter
Process assembly statements
Detect labels
Add symbols to the Symbol Table
Increment the location counter
Process instructions
Process RESB
Process RESW
Process BYTE
Process WORD
Process END
Generate Pass 1 output

The project uses hexadecimal addresses for memory calculations.

📋 Symbol Table

The Symbol Table maps assembly labels to their corresponding addresses.

Example concept:

LABEL       ADDRESS
-------------------
LOOP        1000
VALUE       1010
RESULT      1020

The table allows Pass 2 to resolve symbolic operands.

For example:

LDA VALUE

can be translated by looking up the address associated with VALUE.

🔢 Location Counter

The Location Counter (LOCCTR) keeps track of the memory address of the current instruction or data element.

The counter is updated according to the type of statement being processed.

Examples include:

Format 1 instruction
Format 3 instruction
RESB
RESW
BYTE
WORD

This allows the assembler to determine where each instruction and data element will be placed in memory.

⚙️ Supported Instruction Formats

The implementation handles different instruction formats.

Format 1

The project includes mappings for instructions such as:

FIX
FLOAT
HIO
NORM
SIO
TIO
Format 3

The implementation includes instructions such as:

ADD
AND
COMP
DIV
J
JEQ
JGT
JLT
JSUB
LDA
LDCH
LDL
LDX
MUL
OR
RD
RSUB
STA
STCH
STL
STSW
STX
SUB
TD
TIX
WD

These instructions are converted into object code during Pass 2.

🎯 Addressing Modes

The assembler supports symbolic and immediate operands.

Immediate Addressing

Example:

LDA #5

The # prefix indicates an immediate operand.

Indexed Addressing

Example:

LDA TABLE,X

The ,X notation represents indexed addressing.

Symbolic Addressing

Example:

J LOOP

The assembler resolves LOOP through the Symbol Table.

🧮 Pass 2 Object-Code Generation

Pass2.py performs the second stage of assembly.

The program uses:

Instruction → Opcode
Operand → Address

and combines these values to generate object code.

The process can be represented as:

Assembly Instruction
        │
        ▼
Identify Opcode
        │
        ▼
Resolve Operand
        │
        ▼
Find Symbol Address
        │
        ▼
Calculate Object Code
        │
        ▼
Generate Output
📦 Assembly Directives

The implementation processes several assembler directives.

WORD

Allocates a word-sized data value.

WORD value
BYTE

Allocates byte data and supports character/hexadecimal constants.

BYTE ...
RESB

Reserves a specified number of bytes.

RESB ...
RESW

Reserves a specified number of words.

RESW ...
END

Marks the end of the source program.

📂 Project Structure
2-Pass-assembler-System-Programming/
│
├── HTE.py
├── Intermediate.py
├── Pass1.py
├── Pass2.py
├── SymbolTable.py
│
├── hte.txt
├── in.txt
├── intermediate.txt
├── out_pass1.txt
├── out_pass2.txt
├── symbTable.txt
│
├── systems_Project.pdf
│
└── README.md
🧩 Main Components
Pass1.py

Responsible for the first assembly pass.

Main responsibilities include:

Location counter management
Label processing
Symbol Table generation
Directive processing
Intermediate output generation
Pass2.py

Responsible for object-code generation.

Main responsibilities include:

Opcode resolution
Symbol resolution
Operand processing
Address calculation
Object-code generation
SymbolTable.py

Provides functionality related to Symbol Table processing.

Intermediate.py

Handles intermediate assembly information used between the two passes.

HTE.py

Handles HTE-related output processing used by the project.

📄 Input and Output Files

The project includes several text files representing different stages of the assembler.

Input
in.txt

Contains assembly-related input.

Intermediate Representation
intermediate.txt

Stores information generated between assembly passes.

Pass 1 Output
out_pass1.txt

Contains the output generated during Pass 1.

Symbol Table
symbTable.txt

Contains generated symbol/address mappings.

Pass 2 Output
out_pass2.txt

Contains the generated output from Pass 2.

HTE Output
hte.txt

Contains HTE-related output generated by the project.

🛠️ Technologies
Technology	Purpose
Python	Main implementation language
Pandas	Processing tabular/intermediate data
File I/O	Reading and generating assembler files
Hexadecimal arithmetic	Address and object-code calculations
System Programming	Core project domain
🧠 Concepts Demonstrated

This project demonstrates practical understanding of:

Assemblers
Two-pass processing
Symbol Tables
Location Counters
Opcode Tables
Instruction formats
Machine-code generation
Addressing modes
Immediate addressing
Indexed addressing
Assembly directives
File processing
Hexadecimal representation
Compiler/system-programming concepts
▶️ Running the Project
Requirements
Python 3.x
Pandas

Install Pandas:

pip install pandas
Run Pass 1
python Pass1.py
Run Pass 2
python Pass2.py

The generated intermediate, Symbol Table, and object-code files can then be inspected.

🔍 Example Workflow

A simplified assembly workflow is:

Source Code
     │
     ▼
Pass 1
     │
     ├── Calculate Addresses
     ├── Build Symbol Table
     └── Generate Intermediate File
     │
     ▼
Pass 2
     │
     ├── Resolve Symbols
     ├── Lookup Opcodes
     ├── Generate Object Code
     └── Generate Output
📚 Documentation

The repository also contains:

systems_Project.pdf

which provides additional project documentation.

🚀 Future Improvements

Potential extensions include:

Improved assembler error reporting
Duplicate-symbol detection
Undefined-symbol detection
More instruction formats
More addressing modes
Automatic opcode-table loading
Better input validation
Support for larger assembly programs
Structured object-code records
Automated test cases
Command-line arguments for input/output files
More robust assembler syntax validation
⚠️ Limitations

This implementation is an educational System Programming project rather than a complete production assembler.

The supported instructions, formats, directives, and addressing modes are limited to those implemented by the project.

👨‍💻 Author

Youssef Mahmoud

Computer Engineering Graduate
Arab Academy for Science, Technology & Maritime Transport

⭐ Project Focus

This project demonstrates how a two-pass assembler transforms assembly instructions into machine-level object code while resolving symbols and memory addresses across multiple processing stages.

