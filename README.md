# Lexical Analyzer for Custom Programming Language

## Introduction
This project implements a lexical analyzer for a custom programming language. The analyzer is built in Java and uses automata theory (NFAs/DFAs) to tokenize source code. It classifies tokens into various categories (keywords, identifiers, numbers, operators, etc.), maintains a symbol table for scope management, and reports lexical errors. This solution strictly adheres to the language constraints defined in the assignment.

## Features
- **Language Constraints:**  
  - **Data Types:** Boolean, Integer, Decimal, and Character  
  - **Identifiers:** Only lowercase letters (a–z) are allowed (with digits allowed after the first letter)  
  - **Arithmetic Operators:** Support for addition, subtraction, multiplication, division, modulus, and exponentiation  
  - **Decimal Precision:** Decimal numbers are processed and can be rounded to five decimal places if needed  
  - **Whitespace & Comments:** Handles extra spaces, single-line, and multi-line comments  
  - **Scope Management:** Supports both global and local variables via a symbol table
- **Error Handling:**  
  Lexical errors (e.g., unrecognized tokens, invalid identifiers) are captured and reported.
- **Transition Table Reporting:**  
  For each token type, the DFA transition table and state counts (total and unique) are displayed for debugging and validation purposes.

## Setup & Compilation

### Prerequisites
- Java Development Kit (JDK) 8 or later
- Eclipse IDE (or your favorite Java IDE)

### Build Instructions
1. Clone or download the project repository.
2. Import the project into Eclipse (or your preferred IDE).
3. Compile all files in the package `test1`.
4. Place your source file (e.g., `program.mylang`) in the designated directory (as specified in Main.java).
5. Run `Main.java`.

## File Structure
- **Main.java**  
  Reads the source file, invokes the lexical analyzer, prints tokenized output, symbol table, and displays DFA state information for each token type.
- **LexicalAnalyzer.java**  
  Uses the dk.brics.automaton library to build DFAs for each token type from regular expressions, tokenizes the source code using a longest-match strategy, and builds the symbol table.
- **Conversion.java**  
  Converts Java regex patterns (e.g., `\b`, `\d`) into an automaton-compatible format.
- **ErrorHandler.java**  
  Collects and displays lexical errors.
- **Token.java**  
  Defines the token structure.
- **SymbolTable.java**  
  Maintains a symbol table for variable declarations and scope management.

## Language Syntax & Rules

### Keywords
| Keyword  | Example         |
|----------|-----------------|
| int      | `int counter = 100;` |
| decimal  | `decimal pi = 3.14159;` |
| bool     | `bool flag = true;`  |
| char     | `char letter = 'a';`  |
| string   | `string name = "hello";` |
| if/else  | `if (x > 5) { ... }` |
| print    | `print("Hello World");` |
| input    | `input("Enter a number: ");` |

### Variable Naming Rules
- Must contain **only lowercase** letters (after the first character, digits are allowed).
- Example: `var`, `counter`

### Operators
| Operator | Meaning          |
|----------|------------------|
| +        | Addition         |
| -        | Subtraction      |
| *        | Multiplication   |
| /        | Division         |
| %        | Modulus          |
| ^        | Exponentiation   |
| =        | Assignment       |

### Delimiters
| Delimiter      | Example            |
|----------------|--------------------|
| Parentheses    | `(x + y)`          |
| Curly Braces   | `{ code }`         |
| Semi-Colon     | `statement;`       |
| Comma          | `a, b, c`          |

### Comments
| Comment Type          | Symbol     | Example                       |
|-----------------------|------------|-------------------------------|
| Single-Line Comment   | `//`       | `// This is a comment`        |
| Multi-Line Comment    | `/* ... */`| `/* This is a multi-line comment */` |

## Example Program
```c
int counter = 100;             
decimal value = 123.45678;      
bool flag = true;              
char letter = 'a';             

int main() {
    int sum = counter + 50;         
    int diff = counter - 30;        
    decimal prod = value * 2;       
    decimal quot = value / 2;       
    int modResult = counter % 3;    
    int powerint = 2^3;             
    decimal powerDec = value^2;     
    int spaced = 42;

    /*
     This is a multi-line comment.
     It includes extra spaces and blank lines.
    */

    if (counter > 50) {
        int localvar = counter + 10;
        print("Local variable value: " + localvar);
        if (flag == true) {
            decimal nestedval = 0.00001;
            print("Nested local decimal: " + nestedval);
        }
    }

    int invalid = 5;
    bool errorVar = false;

    int user_input = read("Enter a number: ");
    print("You entered: " + user_input);
}
