# Learn C

Beginner-friendly notes for learning C, following the same chapter flow as the C++ notes in this repository. The examples use standard C, primarily C17; notes call out where a feature requires C99 or C23.

## Lessons

0. [Install and set up a C environment](<./Chapter 0/Install.md>)
1. [Introduction to C](<./Chapter 1/Introduction to C.md>)
2. [Variables and data types](<./Chapter 2/1. Variables and Data Types.md>)
   1. [Integer modifiers](<./Chapter 2/2. Integer Modifiers.md>)
   2. [Fractional numbers](<./Chapter 2/3. Fractional Numbers.md>)
   3. [Booleans](<./Chapter 2/4. Booleans.md>)
   4. [Characters and text](<./Chapter 2/5. Characters and Text.md>)
   5. [The `auto` keyword in C](<./Chapter 2/6. Auto Keyword.md>)
   6. [Assignments](<./Chapter 2/7. Assignments.md>)
3. [Data operations](<./Chapter 3/1. Introduction on Data Operations.md>)
   1. [Compound operators](<./Chapter 3/2. Compound Operators.md>)
   2. [Relational operators](<./Chapter 3/3. Relational Operators.md>)
   3. [Logical operators](<./Chapter 3/4. Logical Operators.md>)
   4. [Output formatting](<./Chapter 3/5. Output Formatting.md>)
   5. [Numeric limits](<./Chapter 3/6. Numeric Limits.md>)
   6. [Math functions](<./Chapter 3/7. Math Functions.md>)
   7. [Integral promotions](<./Chapter 3/8. Weird Integral Types.md>)
4. [Flow statements](<./Chapter 4/1. Introduction To Flow Statements.md>)
   1. [Conditional flow statements](<./Chapter 4/2. Flow Statements.md>)
5. [Loops](<./Chapter 5/1. Loops.md>)

## Compile a program

Save a lesson example as `main.c` and compile it with a C compiler:

```sh
gcc -std=c17 -Wall -Wextra -Wpedantic main.c -o main
./main
```

On Windows PowerShell, run `.\main.exe` after compiling with `-o main.exe`. A C program must be compiled as C (for example with `gcc` or `clang`), not as C++ with `g++`.

