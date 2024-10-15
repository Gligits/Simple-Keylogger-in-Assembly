# Project Overview

This project is a basic keylogger written in assembly language for the Windows operating system. The keylogger captures keystrokes on the system and writes them to a log file. It demonstrates how to interact with the Windows API at a low level using assembly, providing insights into system calls, memory management, and low-level programming on the Windows platform.

The project extends beyond simple keystroke logging by including additional features such as:
- Stealth mode operation (running in the background without a visible window)
- Periodic logging to a file
- Optionally configuring the program to start automatically with Windows
- Encrypting the log file for added security

## Features

1. **Capture Keystrokes:** The keylogger records all keystrokes, including special keys (e.g., Enter, Shift, Ctrl), and stores them in a log file.
2. **Stealth Mode:** The program runs in the background without displaying a window or console to avoid detection.
3. **Active Window Logging:** Logs the name of the active window to provide context for the captured keystrokes.
4. **Periodic File Writing:** Writes the captured data to a log file every few seconds to ensure data is saved.
5. **Encryption:** Optionally encrypts the log file to prevent unauthorized access to the logged data.
6. **Auto Startup:** The keylogger can be configured to start automatically with Windows.

## Prerequisites

Before running the keylogger, ensure the following tools are installed:
- **Microsoft Macro Assembler (MASM)** or **Flat Assembler (FASM)**
- **Linker (`link.exe`)** that comes with Visual Studio Build Tools
- **Debugger (x64dbg or OllyDbg)** for debugging
- **Text editor** 

## How It Works

1. **Capture Keystrokes Using `GetAsyncKeyState`:**
   - The Windows API function `GetAsyncKeyState` is used to detect whether a key is pressed.
   - The keylogger continuously checks the state of each key on the keyboard to see if it is pressed.
   
2. **Write Data to a File Using `CreateFile`, `WriteFile`, and `CloseHandle`:**
   - The logged keystrokes are stored in memory and periodically written to a log file using Windows API functions.
   - A new log file is created if it does not already exist.
   
3. **Run in Stealth Mode:**
   - The program uses linker options to prevent a console window from appearing when the keylogger runs.
   - This ensures the keylogger runs in the background, minimizing the chance of detection.

4. **Active Window Tracking:**
   - The keylogger uses `GetForegroundWindow` and `GetWindowText` functions to capture the name of the currently active window.
   - This provides context for the recorded keystrokes by indicating which application was active when the keys were pressed.

5. **Encrypt the Log File (Optional):**
   - For added security an encryption mechanism can be implemented to obfuscate the log file's contents.
   - A simple XOR encryption can be used to prevent unauthorized access to the captured data.

6. **Auto Startup (Optional):**
   - The program can add an entry to the Windows registry to start the keylogger automatically when Windows boots.
   - **Note:** Modifying the registry can be considered intrusive so only use this feature for demonstration purposes.

**Disclaimer**: This keylogger is intended for educational purposes only. Do not use it for illegal activities or without consent.

