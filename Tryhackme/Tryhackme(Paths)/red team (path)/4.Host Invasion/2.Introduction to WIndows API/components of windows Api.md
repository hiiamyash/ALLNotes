
|                         |                                                                                                                                                                              |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Layer**               | **Explanation**                                                                                                                                                              |
| API                     | A top-level/general term or theory used to describe any call found in the win32 API structure.                                                                               |
| Header files or imports | Defines libraries to be imported at run-time, defined by header files or library imports. Uses pointers to obtain the function address.                                      |
| Core DLLs               | A group of four DLLs that define call structures. (KERNEL32, USER32, and ADVAPI32). These DLLs define kernel and user services that are not contained in a single subsystem. |
| Supplemental DLLs       | Other DLLs defined as part of the Windows API. Controls separate subsystems of the Windows OS. ~36 other defined DLLs. (NTDLL, COM, FVEAPI, etc.)                            |
| Call Structures         | Defines the API call itself and parameters of the call.                                                                                                                      |
| API Calls               | The API call used within a program, with function addresses obtained from pointers.                                                                                          |
| In/Out Parameters       | The parameter values that are defined by the call structures.                                                                                                                |


**Simple Example: Displaying a Message Box**

Let's say a program wants to show a simple "Hello!" message on the screen. It would use the `MessageBox` function from `USER32.DLL`.

1. **API:** The program is using the Win32 API.
2. **Header File:** The program includes a header file (like `windows.h`) which acts as the catalog and tells it about the `MessageBox` function and where to find it in `USER32.DLL`.
3. **Core DLL:** The `MessageBox` function is located inside the `USER32.DLL` (the user interface tools compartment).
4. **Call Structure:** The `MessageBox` function "blueprint" says it needs certain information:
    - Where the message box should appear (e.g., on top of another window, or just on the screen).
    - The text of the message ("Hello!").
    - The title of the message box ("Greeting").
    - What kind of buttons should be on it (e.g., an "OK" button).
5. **API Call:** The program makes the `MessageBox` API call, providing the necessary information.
6. **In/Out Parameters:** The "in parameters" are the text "Hello!", the title "Greeting", and the instruction to show an "OK" button. The "out parameter" might be a value indicating which button the user clicked (in this simple case, it would likely just be "OK").



