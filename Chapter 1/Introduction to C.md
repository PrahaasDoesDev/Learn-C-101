# Introduction to C

C is a compiled, general-purpose programming language. A C source file is plain text; a compiler translates it into an executable program.

## Your first program

```c
#include <stdio.h>

int main(void)
{
    puts("Hello, world!");
    return 0;
}
```

- `#include <stdio.h>` makes declarations for standard input/output functions such as `puts` available.
- `main` is the program's entry point. `int` is its return type; returning `0` conventionally reports success to the operating system.
- Statements usually end with a semicolon. Braces group a function's statements.
- `puts` prints a string followed by a newline.
- `void` in `main(void)` says the function takes no arguments.

Compile with `gcc -std=c17 -Wall -Wextra -Wpedantic hello.c -o hello`.

## Comments

```c
// A single-line comment (C99 and later)

/*
   A block comment can span multiple lines.
   Block comments do not nest.
*/
```

Comments document intent; they are ignored by the compiler. Avoid commenting out large sections with nested `/* ... */`, because C block comments cannot be nested.

## Errors and warnings

- **Compile-time errors** prevent an object file or executable from being produced. Examples include a missing semicolon, undeclared identifier, incompatible types, or a call with the wrong number of arguments.
- **Linker errors** happen after compilation when a referenced function or object has no matching definition.
- **Runtime errors** occur while the program runs. Examples include invalid memory access, division by zero for integers, and non-terminating loops.
- **Warnings** identify suspicious code that may still compile, such as unused variables, format-string mismatches, or conversions that may lose information.

Use compiler warnings while learning:

```sh
gcc -std=c17 -Wall -Wextra -Wpedantic main.c -o main
```

C has no exceptions, classes, templates, or `new`/`delete`. Memory errors and invalid operations still need to be prevented, and undefined behavior can make a program's result unpredictable.

## Console input and output

### Output with `printf` and `puts`

`printf` formats values according to a format string. `puts` writes a string and a newline.

```c
#include <stdio.h>

int main(void)
{
    int count = 3;
    double price = 2.50;

    printf("Count: %d, price: %.2f\n", count, price);
    puts("Done");
    return 0;
}
```

Format specifiers must match the types of the arguments. For example, `%d` is for `int`, `%f` is for `double` in `printf`, and `%s` is for a null-terminated character string. A mismatch can cause undefined behavior.

### Input with `scanf` and `fgets`

For simple formatted input, `scanf` needs the address of each destination:

```c
int age;
if (scanf("%d", &age) == 1) {
    printf("Age: %d\n", age);
} else {
    puts("Please enter a whole number.");
}
```

Check `scanf`'s return value. For whole lines, `fgets` is usually easier to control:

```c
char name[80];
if (fgets(name, sizeof name, stdin) != NULL) {
    printf("Hello, %s", name);
}
```

`fgets` reads at most the buffer size minus one and adds a terminating `'\0'`. It may keep the newline if there is room. Input handling should account for invalid or overly long input.

## How a C program runs

1. **Preprocessing:** processes directives such as `#include` and `#define`.
2. **Compilation:** checks and translates C source into lower-level code.
3. **Assembly:** creates object files from assembly instructions.
4. **Linking:** combines object files and libraries into an executable.
5. **Loading and execution:** the operating system starts the program; execution begins at `main`.

The exact toolchain steps vary, but this model helps distinguish compiler errors from linker errors.

## Variables, lifetime, and memory

A declaration gives an object a type and a name:

```c
int total = 10;
```

The type determines how the value is represented and which operations are valid. A block-scope automatic variable generally exists while execution is in that block. Objects with static storage duration exist for the whole program. C does not automatically initialize ordinary uninitialized automatic variables; initialize them before reading them.

Pointers store addresses, not the objects themselves. Only access an object through a valid pointer with the correct lifetime and type. A pointer can be compared with a null pointer using `NULL` or, in C23, `nullptr`.

## C language and standard library

The **C language** defines syntax, types, expressions, and control flow. The **C standard library** provides declared functions and types through headers such as `<stdio.h>`, `<stdlib.h>`, `<string.h>`, and `<math.h>`. Include the correct header before using a library function.

Unlike C++, C has no STL, classes, namespaces, references, or stream objects. C programs commonly use functions, structures, pointers, arrays, and standard library routines.

## Summary

- A C program starts in `main`; statements are executed in order unless control flow changes that order.
- Include standard headers for the functions you use.
- Use `printf`/`puts` for output and check input function results.
- Treat compiler warnings seriously and avoid undefined behavior.
- Compile and link C source with a C compiler such as GCC or Clang.

