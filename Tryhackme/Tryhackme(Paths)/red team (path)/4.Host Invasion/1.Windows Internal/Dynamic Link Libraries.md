
a library that contains code and data that can be used by more than one program at the same time

the operating system and the programs load faster, run faster, and take less disk space on the computer.

```cpp
#include "stdafx.h"
#define EXPORTING_DLL
#include "sampleDLL.h"
BOOL APIENTRY DllMain( HANDLE hModule, DWORD ul_reason_for_call, LPVOID lpReserved
)
{
    return TRUE;
}

void HelloWorld()
{
    MessageBox( NULL, TEXT("Hello World"), TEXT("In a DLL"), MB_OK);
}
```


Below is the header file for the DLL; i

```cpp
#ifndef INDLL_H
    #define INDLL_H
    #ifdef EXPORTING_DLL
        extern __declspec(dllexport) void HelloWorld();
    #else
        extern __declspec(dllimport) void HelloWorld();
    #endif

#endif
```

The DLL has been created, but that still leaves the question of how are they used in an application?

DLLs can be loaded in a program using _load-time dynamic linking_ or _run-time dynamic linking_.

When loaded using _load-time dynamic linking_, explicit calls to the DLL functions are made from the application. You can only achieve this type of linking by providing a header (_.h_) and import library (_.lib_) file. Below is an example of calling an exported DLL function from an application.



When loaded using _run-time dynamic linking_, a separate function (`LoadLibrary` or `LoadLibraryEx`) is used to load the DLL at run time. Once loaded, you need to use `GetProcAddress` to identify the exported DLL function to call. Below is an example of loading and importing a DLL function in an application.

```cpp
...
typedef VOID (*DLLPROC) (LPTSTR);
...
HINSTANCE hinstDLL;
DLLPROC HelloWorld;
BOOL fFreeDLL;

hinstDLL = LoadLibrary("sampleDLL.dll");
if (hinstDLL != NULL)
{
    HelloWorld = (DLLPROC) GetProcAddress(hinstDLL, "HelloWorld");
    if (HelloWorld != NULL)
        (HelloWorld);
    fFreeDLL = FreeLibrary(hinstDLL);
}
...
```

