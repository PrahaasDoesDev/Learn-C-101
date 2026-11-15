# Chapter 0: Installing and Setting Up a C Environment

To write and run C programs, you need a compiler, an editor, and a terminal. A debugger is useful when you want to inspect a program as it runs. This guide uses Visual Studio Code, but any editor can be used with a C compiler.

## Windows: Visual Studio Code and GCC

1. Install [Visual Studio Code](https://code.visualstudio.com/).
2. Install [MSYS2](https://www.msys2.org/), then open the **MSYS2 UCRT64** terminal.
3. Update MSYS2 with `pacman -Syu`. If asked to close the terminal, reopen UCRT64 and follow the update prompt.
4. Install GCC, GDB, and make:

   ```sh
   pacman -S --needed mingw-w64-ucrt-x86_64-gcc mingw-w64-ucrt-x86_64-gdb mingw-w64-ucrt-x86_64-make
   ```

5. Add `C:\msys64\ucrt64\bin` to your Windows user `Path` (adjust it if MSYS2 is installed elsewhere), then restart VS Code and terminals.
6. In VS Code, install Microsoft's **C/C++** extension. It provides editor and debugger support; it does not install a compiler.
7. Verify the tools in a new terminal:

   ```powershell
   gcc --version
   gdb --version
   ```

## Linux

Install GCC and GDB with your distribution's package manager. On Ubuntu or Debian:

```sh
sudo apt update
sudo apt install build-essential gdb
```

Install VS Code if desired, then install Microsoft's **C/C++** extension. Check `gcc --version` and `gdb --version`.

## macOS

Install Apple's command-line developer tools:

```sh
xcode-select --install
```

This provides Clang. Install VS Code and Microsoft's **C/C++** extension if desired, then verify with `clang --version`.

## Compile and run a test program

Create `hello.c`:

```c
#include <stdio.h>

int main(void)
{
    puts("Hello, C!");
    return 0;
}
```

Compile and run it with GCC:

```sh
gcc -std=c17 -Wall -Wextra -Wpedantic hello.c -o hello
./hello
```

On Windows, name the executable `hello.exe` and run `.\hello.exe` in PowerShell. With Clang, replace `gcc` with `clang`.

## Common setup problems

| Problem | Check |
|---|---|
| `gcc` or `clang` is not recognized | Confirm that the compiler is installed; on Windows, check `Path` and reopen the terminal. |
| VS Code cannot find a compiler | The C/C++ extension is not a compiler. Install a toolchain and configure the compiler path. |
| A build task points to a missing executable | Update the compiler path in `.vscode/tasks.json`, or build from the terminal. |
| IntelliSense disagrees with a successful build | Check the selected compiler, include paths, and C language standard in the VS Code configuration. |

Continue with [Chapter 1: Introduction to C](<../Chapter 1/Introduction to C.md>).

