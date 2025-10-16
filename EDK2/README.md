<div align=center><img src="https://www.advantech.tw/css/css-img/advantech-logo-notagl.svg" width="400"></div>

EDK2 **B**uild Process
========================

Agenda
------
*   EDK2 Source and build
    *   Change Code Page to UTF-8
    *   Get EDK2 Source code
    *   Update EDK2 submodule
    *   Setup EDK2 envir
    *   Build Basetool
    *   Build Platform File
    *   Build Error


# Change Code Page to UTF-8

        chcp 65001

# Get EDK2 Source code
*       git clone https://github.com/tianocore/edk2.git

* https://github.com/tianocore/edk2-libc.git
* commit 27545cb7cf32077331bcac0e008115467f5e4c53

# Update EDK2 submodule
*         cd edk2
*         git submodule update --init
*         git submodule update --recursive

# Checkout EDK2 revision
*         git checkout 2522020ee1

# Setup EDK2 environment
* edksetup.bat

# Build EDK2 Basetool
* cd BaseTools
* toolsetup.bat ForceRebuild VS2022

# Build Platform File (default:EmulatorPkg\EmulatorPkg.dsc)
* build

# Build Platform File (UefiPayloadPkg\UefiPayloadPkg.dsc)
* build -a IA32 -a X64 -b DEBUG -t VS2022 -D BOOTLOADER=SBL -p UefiPayloadPkg\UefiPayloadPkg.dsc

# Build Platform File (ShellPkg\ShellPkg.dsc)
* build -a X64 -b DEBUG -t VS2022 -p ShellPkg\ShellPkg.dsc
* build -a X64 -b RELEASE -t VS2022 -p ShellPkg\ShellPkg.dsc
* build -a IA32 -b RELEASE -t VS2022 -p ShellPkg\ShellPkg.dsc

# Get EDK2-LibC Source code
*         git clone https://github.com/tianocore/edk2-libc.git

# Checkout EDK2-LibC revision
*         git checkout 27545cb7

# Build Platform File (AppPkg\AppPkg.dsc)
* build -a X64 -b RELEASE -t VS2019 -p AppPkg\AppPkg.dsc
* build -a X64 -b DEBUG -t VS2022 -D BUILD_PYTHON368 -p AppPkg\AppPkg.dsc
* build -a X64 -b RELEASE -t VS2022 -p AppPkg\AppPkg.dsc
* build -a IA32 -b RELEASE -t VS2022 -p AppPkg\AppPkg.dsc

# Build Platform File (AppPkg\AppPkg.dsc with Python)

>Override PyMod-3.6.8 to Python-3.6.8 directory

    cd AppPkg\Applications\Python\Python-3.6.8

    Python srcprep.py

    cd ..\..\..\..

>Build Python-3.6.8 Environment
  
    AppPkg\Applications\Python\Python-3.6.8\create_python_pkg.bat VS2022 RELEASE X64 .\build\python

>Build Python-3.6.8 AppPkg\AppPkg.dsc 
    
    build -a X64 -b RELEASE -t VS2022 -D BUILD_PYTHON368 -p AppPkg\AppPkg.dsc
    
    build -a X64 -b DEBUG -t VS2022 -D BUILD_PYTHON368 -p AppPkg\AppPkg.dsc

# Build Error
*         MdePkg/Include/IndustryStandard/SmBios.h            --> CP950 error
*         modified:/// Unless otherwise specified, when referring to another structure's handle, the value
*   UefiPayloadPkg/UefiPayloadEntry/UefiPayloadEntry.c  --> Data type error
*         modified:*HobMemBase = (UINTN)MemoryMapEntry->Base;  

