# How C++ Works: From Source Code to Executable

This document provides an overview of the process of turning C++ source code into a runnable program.


## The Basic Pipeline

The fundamental workflow for creating a C++ program is as follows:

1.  **Source Files:** You write your code in plain text files, typically with a `.cpp` extension.
2.  **Compiler:** A compiler takes your source files and translates them into an intermediate format.
3.  **Binary:** The final output is a binary file, which can be either an **executable program** (`.exe` on Windows) or a **library** (`.dll` or `.lib` on Windows).


## The Compilation Process in Detail

### 1. Pre-processing

Before the compiler does its main work, it first runs a **pre-processor**.

*   Any line starting with a `#` is a pre-processor directive.
*   The most common directive is `#include`.
*   `#include <iostream>` finds the `iostream` file (a **header file**) and pastes its entire content into your source file. This is necessary to use things like `std::cout`.


### 2. Compilation

After pre-processing, the compiler transforms your C++ code into machine code.

*   Each `.cpp` source file is compiled **individually**.
*   The output of compiling a single `.cpp` file is an **object file** (e.g., `main.obj`).
*   Header files (`.h` or no extension) are **not** compiled directly. They are included into `.cpp` files and compiled as part of them.

### 3. Linking

The **linker** is the final step. Its job is to take all the individual object files and "link" them together into a single, final executable.

*   It resolves references between files. For example, if `main.cpp` calls a function defined in `log.cpp`, the linker is responsible for connecting the call to the actual function.

## Declarations vs. Definitions

This is a crucial concept when working with multiple files.

*   **Definition:** This is the actual implementation of a function (the code inside the curly braces `{}`). A function can only be **defined once**.
*   **Declaration (or Prototype):** This is a promise to the compiler that a function exists somewhere else. It specifies the function's name, return type, and parameters, but not the body. You can have **multiple declarations** for the same function.

**Example:**

Let's say we have a `log` function in `log.cpp`:

```cpp
// log.cpp

#include <iostream>

// This is the DEFINITION of the log function
void log(const char* message) {
    std::cout << message << std::endl;
}
```

To use this `log` function in `main.cpp`, we must provide a declaration for it.

```cpp
// main.cpp

#include <iostream>

// This is a DECLARATION for the log function
void log(const char* message);

int main() {
    log("Hello from main!"); // The linker will connect this call to the definition in log.obj
    return 0;
}
```

## Common Errors

*   **Compiler Error:** Often a syntax error, like a missing semicolon. Or, if you forget to provide a *declaration* for a function you are trying to use, the compiler will complain that the function is not found.
*   **Linker Error:** This happens when the linker cannot find the *definition* for a symbol that has been declared. The most common linker error is an **"unresolved external symbol"**. This means you declared a function (made a promise) but the linker couldn't find its actual implementation anywhere in the object files.

## Build Configurations: Debug vs. Release

In IDEs like Visual Studio, you typically have at least two build configurations:

*   **Debug:**
    *   Compiler optimizations are **disabled**.
    *   This makes the code run slower, but it makes debugging much easier because the compiled code directly maps to your source code.
*   **Release:**
    *   Compiler optimizations are **enabled** (e.g., "Maximize Speed").
    *   This results in a faster, smaller executable, which is what you would distribute to users. Debugging is much harder.

You can switch between these configurations to build your project for different purposes.
