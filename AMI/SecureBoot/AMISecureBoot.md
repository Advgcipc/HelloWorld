<div align=center><img src="https://www.advantech.tw/css/css-img/advantech-logo-notagl.svg" width="400"></div>

AMI Secure Boot
===============

Agenda
------
## AMI Secure Boot

* Customer Default Key Provision
* Secure Boot Varable
* Secure Boot Setup and Tokens
* Secure Boot Default Key Provision
* Update Secure Boot Key Module 

### Customer Default Key Provision

* BIOS include public keys PK, KEK, DB, DBX using "Certificates eModule" 
* BIOS default set "DEFAULT_PROVISION_SECURE_VARS" to 1
* BIOS enroll keys at DXE phase via "SecureBootDXE" driver during SetupMode == 1

### Secure Boot Varable

* AMI defined variable ==> AMI_SECURE_BOOT_SETUP_VAR  L"SecureBootSetup"
* The "SecureBootSetup" variable only could be modified in Admin mode of BIOS Setup.
* The "SecureBootSetup" variable default would be reserved during flashing BIOS.

typedef struct{
    UINT8 SecureBootSupport;   ///< Setup control
    UINT8 SecureBootMode;      ///< Setup control
    UINT8 DefaultKeyProvision; ///< Setup control
    UINT8 Reserved;            ///< reserved
    UINT8 Load_from_OROM;      ///< Setup control
    UINT8 Load_from_REMOVABLE_MEDIA; ///< Setup control
    UINT8 Load_from_FIXED_MEDIA; ///< Setup control
} SECURE_BOOT_SETUP_VAR;


### Secure Boot Setup and Tokens
* SecureBootSupport of SECURE_BOOT_SETUP_VAR is control by Secure Boot item
* "DEFAULT_SECURE_BOOT_ENABLE" token is Secure Boot item default setting
* SecureBootMode of SECURE_BOOT_SETUP_VAR is control by Secure Boot Mode item
* "DEFAULT_SECURE_BOOT_MODE" token is Secure Boot Mode item default setting

![SecureBoot1](image-1.png)

* DefaultKeyProvision of SECURE_BOOT_SETUP_VAR is control by Factory Key Provision item

* "DEFAULT_PROVISION_SECURE_VARS" token is Factory Key Provision item default setting

![SecureBoot2](image-2.png)

* Restore Factory Keys is interactive item to reload default keys 

* Reset to Setup Mode is interactive item to remove keys 

* Enroll EFI image is interactive item to add hash EFI image data and let it load in Secure Boot mode 

### Secure Boot Default Key Provision

* BIOS add "Certificates eModule" to include PK, KEK, DB, DBX keys 
* "Certificates eModule" can support public key (cer or der format) to Authenticated variable
![Cert7](image-7.png)

### Update Secure Boot Key Module 

* Customer using Owner GUID 

![Cert0](image-3.png)

* "Certificates eModule" need to update

* Add Customer's Owner GUID

![Cert5](image-5.png)

* Update makefile to match keyname and re-define "Owner GUID"

![Cert3](image-6.png)

* Update makefile to support Authenticated Variable
![Cert8](image-8.png) 
![Cert9](image-9.png)

* Update SDL file
![Cert11](image-11.png)
![Cert10](image-10.png)