<div align=center><img src="https://www.advantech.tw/css/css-img/advantech-logo-notagl.svg" width="400"></div>

# ACPI Declaim Device Node


## ACPI Method _HID _CID _DSD
*   _HID    Object that evaluates to a device’s Plug and Play hardware ID.

*   _CID    Object that evaluates to a device’s Plug and Play-compatible ID list.

*   _DSD 
    4444


## Linux Kernel Doc
![LinuxKernelDoc](./DeviceID/Pics/DeviceTreenamelinkDeviceid.png)
* https://docs.kernel.org/firmware-guide/acpi/enumeration.html

## Sample ASL code

  *   Scope(\_SB.PC00.I2C1) {
        Device (ADI2) {
            Name (_CID, "PRP0001")
            Name (_DDN, "Analog Device Inc, MAX6958")
            Name (_CRS, ResourceTemplate () {
                I2CSerialBus(0x0038, ControllerInitiated, 400000, AddressingMode7Bit, "\\_SB.PC00.I2C1", 0x00,  ResourceConsumer,,)
            })
        
            Name (_DSD, Package () {
                ToUUID("daffd814-6eba-4d8c-8a91-bc9bbf4aa301"),
                Package () {
                  Package () {"compatible", "maxim,max6959"},
                }
             })
        
            Method(_STA, 0, NotSerialized) { Return(0x0F) }
        }
    }

