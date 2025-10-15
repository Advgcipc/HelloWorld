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

*  chcp 65001

# Get EDK2 Source code
* git clone https://github.com/tianocore/edk2.git

* https://github.com/tianocore/edk2.git
* faeee00490bc23b147f1d4b6e70b190d3eb80583 MdeModulePkg/FvSimpleFileSystemDxe: Remove Iso639Language

* https://github.com/tianocore/edk2-libc.git
* 27545cb7cf32077331bcac0e008115467f5e4c53 edk2-libc: Add manual dispatch for the Python UEFI build actions

# Update EDK2 submodule
* cd edk2
* git submodule update --recursive

# Setup EDK2 envir
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

# Build Platform File (AppPkg\AppPkg.dsc)
* https://github.com/tianocore/edk2-libc.git
* commit 27545cb7cf32077331bcac0e008115467f5e4c53
* build -a X64 -b RELEASE -t VS2019 -p AppPkg\AppPkg.dsc
* build -a X64 -b DEBUG -t VS2022 -D BUILD_PYTHON368 -p AppPkg\AppPkg.dsc
* build -a X64 -b RELEASE -t VS2022 -D BUILD_PYTHON368 -p AppPkg\AppPkg.dsc

# Build Platform File (AppPkg\AppPkg.dsc with Python)
>Override PyMod-3.6.8 to Python-3.6.8 directory

    Python AppPkg\Applications\Python\Python-3.6.8\srcprep.py

>Build Python-3.6.8 Environment
  
    AppPkg\Applications\Python\Python-3.6.8\create_python_pkg.bat  VS2019 RELEASE X64 .\build\py

>Build Python-3.6.8 AppPkg\AppPkg.dsc 
    
    build -a X64 -b DEBUG -t VS2019 -D BUILD_PYTHON368 -p AppPkg\AppPkg.dsc
    
    build -a X64 -b RELEASE -t VS2019 -D BUILD_PYTHON368 -p AppPkg\AppPkg.dsc

# Build Error
*         modified:   MdePkg/Include/IndustryStandard/SmBios.h            --> CP950 error
*         modified:   UefiPayloadPkg/UefiPayloadEntry/UefiPayloadEntry.c  --> Data type error
