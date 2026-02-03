<div align=center><img src="https://www.advantech.tw/css/css-img/advantech-logo-notagl.svg" width="400"></div>

Agenda
======

* SBL Source Setup and Build

* EDK2 Source Setup and build
  
SBL Setup and Build
-------------------

## Install VSCode for code editor
## Install Microsoft Visual Studio 2022 Community

## Install VSCode for code editor
*   https://code.visualstudio.com/download

## Install Microsoft Visual Studio 2022 Community

* https://visualstudio.microsoft.com/downloads/

* Download VisualStudio2022setup
* Select C++ Desktop develop

## Install Git (ex. GitBash)

*  \\\biosserver.advantech.corp\Utility\SBL\Git-2.42.0.2-64-bit.exe
*   https://github.com/git-for-windows/git/releases/download/v2.52.0.windows.1/Git-2.52.0-64-bit.exe
  
## Install Python

* \\\biosserver.advantech.corp\Utility\SBL\ASL\ to C:\Python36
* https://www.python.org/ftp/python/3.14.2/python-3.14.2-amd64.exe
  
## Install NASM 2.12.02

* \\\biosserver.advantech.corp\Utility\SBL\Nasm\ to C:\Nasm
* https://www.nasm.us/pub/nasm/releasebuilds/3.01/nasm-3.01.zip
  
## Install IASL 20190509

* \\\biosserver.advantech.corp\Utility\SBL\ASL\ to C:\ASL
* https://www.intel.com/content/www/us/en/download/774881/acpi-component-architecture-downloads-windows-binary-tools.html
* 
## Install OpenSSL

* \\\biosserver.advantech.corp\Utility\SBL\Openssl\ to C:\openssl


EDK2 Build Process
------------------

### Change Code Page to UTF-8
### Set Python default redirect out to UTF-8
### Get EDK2 Source code
### Update EDK2 submodule
### Setup EDK2 envir
### Build Basetool
### Build Platform File
### Build Error

### Change Code Page to UTF-8

*   chcp 65001

### Set Python default redirect out to UTF-8

*   set PYTHONIOENCODING=utf8

* Fix Python error: ’cp950′ codec can’t encode character ‘\u8bfa’ in position 161: illegal multibyte sequence

### Get EDK2 Source code

* get EDK2 source from Github

*    git clone https://github.com/tianocore/edk2.git

     * Switch to Commit ID: 2522020ee12b42fabd8b1353b4f89854455d6325

     *    git checkout 2522020ee12b42fabd8b1353b4f89854455d6325

* Or get EDK2 source from Advantech Github

*    git clone https://github.com/tianocore/edk2.git


### Update EDK2 submodule

*   cd edk2
*   git submodule update --init

### Checkout EDK2 revision

*   git checkout edk2-stable202511

### Setup EDK2 environment

*   edksetup.bat

### Build EDK2 BaseTools

*   cd BaseTools

*   toolsetup.bat ForceRebuild VS2022

### Build Platform File (UefiPayloadPkg\UefiPayloadPkg.dsc)

*   build -a IA32 -a X64 -b DEBUG -t VS2022 -D BOOTLOADER=SBL -p UefiPayloadPkg\UefiPayloadPkg.dsc

### Setup UEFI UniversalPayload

  - UniversalPayload.elf
    - Install elf dump tools 
    - https://github.com/llvm/llvm-project/releases/download/llvmorg-21.1.8/LLVM-21.1.8-win64.exe

#### Build UEFI UniversalPayload Default debug mode

    *   python UefiPayloadPkg/UniversalPayloadBuild.py -t VS2022

#### Release mode

    *   python UefiPayloadPkg/UniversalPayloadBuild.py -t VS2022 -b RELEASE

### Build Error
*   MdePkg/Include/IndustryStandard/SmBios.h            --> CP950 error
*         modified:/// Unless otherwise specified, when referring to another structure's handle, the value
*   UefiPayloadPkg/UefiPayloadEntry/UefiPayloadEntry.c  --> Data type error
*         modified:*HobMemBase = (UINTN)MemoryMapEntry->Base;  

#### Reference Link
        https://uefi.org/sites/default/files/resources/Using%20Python%203%20in%20the%20UEFI%20Shell%20for%20Platform%20Security%20Analysis_Final%208.15.2022.pdf

#### Flash Map Information

  - SPI Flash rom Layout
    ```
	+------------------------------------------------------------------------+
	|                            SPI FLASH  MAP                              |
	|                         (RomSize = 0x02000000)                         |
	+------------------------------------------------------------------------+
	+------------------------------------------------------------------------+
	|   NAME   |     OFFSET  (BASE)     |    SIZE    |       Detail          |
	+----------+------------------------+------------+-----------------------+
	|   DESC   |  0x000000 (no map)     |  0x001000  |  Descriptor Region    |
	+----------+------------------------+------------+-----------------------+
	|   GBE    |  0x001000 (no map)     |  0x002000  |  GBE Region           |
	+----------+------------------------+------------+-----------------------+
	|   CSME   |  0x1000000 (no map)    |  0x1000000 |  CSE Region           |
	+----------+------------------------+------------+-----------------------+
	|   PAD    |  0x1003000 (no map)    |  0x3FD000  |  Region 9             |
	+----------+------------------------+------------+-----------------------+
	|   BIOS   |  0x1400000 (0xFF400000)|  0xC00000  |  BIOS Region          |
	+----------+------------------------+------------+-----------------------+

    ```

  - Slim BootLoader Image
    ```
	+------------------------------------------------------------------------+
	|                              FLASH  MAP                                |
	|                         (RomSize = 0x00D00000)                         |
	+------------------------------------------------------------------------+
	|   NAME   |     OFFSET  (BASE)     |    SIZE    |         FLAGS         |
	+----------+------------------------+------------+-----------------------+
	+------------------------------------------------------------------------+
	|                              NON VOLATILE                              |
	+------------------------------------------------------------------------+
	|   RSVD   |  0x098000(0xFF398000)  |  0x001000  |  Uncompressed,  NV    |
	|   EMTY   |  0x000000(0xFF300000)  |  0x098000  |  Uncompressed,  NV    |
	+----------+------------------------+------------+-----------------------+

	+------------------------------------------------------------------------+
	|                             NON REDUNDANT                              |  <-------------------+
	+------------------------------------------------------------------------+                      |
	|   PYLD   |  0x42a000(0xFF72A000)  |  0x030000  |  Compressed  ,  NR    |                      |
	|   UVAR   |  0x3ea000(0xFF6EA000)  |  0x040000  |  Uncompressed,  NR    |                      |
	|   EPLD   |  0x1aa000(0xFF4AA000)  |  0x240000  |  Uncompressed,  NR    |                      |
	|   MRCD   |  0x19a000(0xFF49A000)  |  0x010000  |  Uncompressed,  NR    |                      |
	|   VARS   |  0x198000(0xFF498000)  |  0x002000  |  Uncompressed,  NR    |                      |
	|   IPFW   |  0x196000(0xFF496000)  |  0x002000  |  Uncompressed,  NR    |                      |
	|   EMTY   |  0x099000(0xFF399000)  |  0x0fd000  |  Uncompressed,  NR    |                      |
	+------------------------------------------------------------------------+                      |

	+------------------------------------------------------------------------+                      |
	|                              REDUNDANT B                               |  <---+               |
	+------------------------------------------------------------------------+      |               |
	|   SG1B   |  0x62d000(0xFF92D000)  |  0x200000  |  Uncompressed, R_B    |      |               |
	|   KEYH   |  0x62c000(0xFF92C000)  |  0x001000  |  Uncompressed, R_B    |      |               |
	|   CNFG   |  0x628000(0xFF928000)  |  0x004000  |  Uncompressed, R_B    |      |               |
	|   FWUP   |  0x608000(0xFF908000)  |  0x020000  |  Compressed  , R_B    |      |               |
	|   SG02   |  0x546000(0xFF846000)  |  0x0c2000  |  Compressed  , R_B    |  >-------------------+ 
	|   UCOD   |  0x45a000(0xFF75A000)  |  0x0ec000  |  Uncompressed, R_B    |      |               |
	+------------------------------------------------------------------------+      |               |

	+------------------------------------------------------------------------+      |               |
	|                              REDUNDANT A                               |  <-----------+       |
	+------------------------------------------------------------------------+      |       |       |
	|   SG1B   |  0xa00000(0xFFD00000)  |  0x200000  |  Uncompressed, R_A    |      |       |       |
	|   KEYH   |  0x9ff000(0xFFCFF000)  |  0x001000  |  Uncompressed, R_A    |      |       |       |
	|   CNFG   |  0x9fb000(0xFFCFB000)  |  0x004000  |  Uncompressed, R_A    |      |       |       |
	|   FWUP   |  0x9db000(0xFFCDB000)  |  0x020000  |  Compressed  , R_A    |      |       |       |
	|   SG02   |  0x919000(0xFFC19000)  |  0x0c2000  |  Compressed  , R_A    |  >-------------------+ 
	|   UCOD   |  0x82d000(0xFFB2D000)  |  0x0ec000  |  Uncompressed, R_A    |      |       |
	+------------------------------------------------------------------------+      |       |

	+------------------------------------------------------------------------+      |       |
	|                               TOP SWAP B                               |      |       |
	+------------------------------------------------------------------------+      |       |
	|   SG1A   |  0xc65000(0xFFF65000)  |  0x01b000  |  Uncompressed, TS_B   |  >---+       |
	|   ACM0   |  0xc00000(0xFFF00000)  |  0x065000  |  Uncompressed, TS_B   |  BP1         |       
	+------------------------------------------------------------------------+              |

	+------------------------------------------------------------------------+              |
	|                               TOP SWAP A                               |              |
	+------------------------------------------------------------------------+              |
	|   SG1A   |  0xce5000(0xFFFE5000)  |  0x01b000  |  Uncompressed, TS_A   |  >-----------+
	|   ACM0   |  0xc80000(0xFFF80000)  |  0x065000  |  Uncompressed, TS_A   |  BP0
	+------------------------------------------------------------------------+


    ```

#### SBL Boot Flow

##### After platform reset, CPU run Stage 1A depend on Intel TOPSWAP.
    
- Boot Path 0: 
    Stage 1A(TOP SWAP A) -> Stage 1B(REDUNDANT A) -> Stage 2(REDUNDANT A) -> Payload (PYLD or EPLD default: EPLD)

- Boot Path 1:
    Stage 1A(TOP SWAP B) -> Stage 1B(REDUNDANT B) -> Stage 2(REDUNDANT B) -> Payload (PYLD or EPLD default: EPLD)

##### Stage 1A

- After coming out of reset, Stage 1A sets up the initial exectution environment.

##### Stage 1B

- The primary purpose of Stage1B is to bring up the system memory.

## Stage 2

- Stage 2 is the “post-memory” stage and is responsible for completing system initialization after main memory is available.
- Initialize the chipset and I/O controllers.

## Payload
- PYLD: Internal Payload default inlcuded Osloader.efi
- EPLD: External Payload default inlcuded Uefipauload.efl
    External Custom Payload support 
        Boot Ubuntu
        Boot VxWorks
        Boot MicroPython
        Boot Linux as a Payload
        Boot Linux with U-Boot Payload
        PXE Boot Through U-Boot Payload
        Boot ACRN Hypervisor


