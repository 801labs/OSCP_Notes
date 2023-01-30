BOF Basics - Windows 32 Bit

**Anatomy of the Stack:**

ESP (Extended Stack Pointer) - is the top of the stack
Buffer - is the space the stores the information from the stack
EBP (Extended Base Pointer) - is the bottom of the stack
EIP (Extended Instruction Pointer) - is an instruction set that can be overwritten if there is potential for a Buffer Overflow

**7 Steps to finding and executing a successful buffer overflow:**

Spiking
Fuzzing
Finding the Offset
Overwriting the EIP
Finding Bad Characters
Finding the Right Module
Generating Shellcode and Gaining Access

**Tools needed on Victim and Attacker Machines:**

**Victim Machine:**

Vulnserver - can be obtained from Github Repo
Immunity Debugger (https://debugger.immunityinc.com/ID_register.py)
Mona (will need to have mona.py placed into C:\Program Files\Immunity Debugger\PyCommands)

**Attacker Machine:**

Kali Linux

**SPECIAL NOTES**

**YOU WILL NEED TO RUN VULNSERVER AND IMMUNITY DEBUGGER AS AN ADMIN WHEN GOING THROUGH ALL OF THESE PROCESSES.**

**YOU WILL ALSO NEED TO MANUALLY START VULNSERVER AND IMMUNITY DEBUGGER EACH TIME YOU CRASH THE VULNERABLE APPLICATION AND REATTACH THE VULNERABLE APPLICATION.**

**VIEW THE YOUTUBE VIDEO SERIES BY TCM SECURITY FOR FURTHER EXPLAINATIONS**

**Custom Template for use on BufferOverflows**

https://github.com/B0rk/BufferOverflowEasyScripts

**Github Files Referenced Above:**

https://github.com/stephenbradshaw/vulnserver

https://github.com/corelan/mona
