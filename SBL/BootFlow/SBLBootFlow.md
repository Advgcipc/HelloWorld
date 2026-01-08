
![Alt text](https://www.advantech.tw/css/css-img/advantech-logo-notagl.svg "Advantech-SBL")

SBL Boot Flow
=============

> https://slimbootloader.github.io/developer-guides/boot-flow.html

# 
![alt text](image.png)  

## Stage 1A

### After coming out of reset, Stage 1A sets up the initial exectution environment.

## Stage 1B

### The primary purpose of Stage1B is to bring up the system memory.

## Stage 2

### Stage 2 is the ¡§post-memory¡¨ stage and is responsible for completing system initialization after main memory is available.
### Initialize the chipset and I/O controllers.

## Payload

### run internal Payload (Os Loader)

SBL Payload type
================

>https://slimbootloader.github.io/how-tos/index.html
  
## Os Loader (Built-in)

### Firmware Update Payload (Built-in)

## Multiple Payload Support

### UEFI Payload (External)

### Boot Windows with UEFI Payload
### Netboot / PXE boot with UEFI Payload (not implemented)
  
## Custom Payload (not implemented)

### Boot Ubuntu
### Boot VxWorks
>https://slimbootloader.github.io/how-tos/boot-vxworks.html
  
### Boot MicroPython
### Boot Linux as a Payload
### Boot Linux with U-Boot Payload
### PXE Boot Through U-Boot Payload
### Boot ACRN Hypervisor


