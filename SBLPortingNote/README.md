
![Alt text](https://www.advantech.tw/css/css-img/advantech-logo-notagl.svg "Advantech-SBL")

SBL Setup and Build
===================
# Setup Sofware
## Install VSCode
*        \\biosserver.advantech.corp\Utility\SBL\VSCodeUserSetup-x64-1.81.1.exe

## Install Microsoft Visual Studio 2017 Community
*         \\biosserver.advantech.corp\Utility\SBL\vs_community_2017__76894b434db54df38dd05fd23360e222.exe
* 勾選使用C++的桌面開發

## Install Git (ex. GitBash)
*          \\biosserver.advantech.corp\Utility\SBL\Git-2.42.0.2-64-bit.exe

## Install Python
*           \\biosserver.advantech.corp\Utility\SBL\ASL\ C:\Python36

## Install NASM 2.12.02

*           \\biosserver.advantech.corp\Utility\SBL\Nasm\ 到 C:\Nasm

## Install IASL 20190509

*           \\biosserver.advantech.corp\Utility\SBL\ASL\ 到 C:\ASL

## Install OpenSSL

*           \\biosserver.advantech.corp\Utility\SBL\Openssl\ 到 C:\openssl

Get SBL Source code
====================
# Get SBL Source code
*           git clone https://github.com/Advgcipc/slimbootloader.git

## Switch SBL to Project branch
*           git checkout ADV

Build SBL Source code 
=====================
# Run command.exe from Win+R
*           slim.bat
### Run "slim.bat -a" to build SBL code
*           slim.bat -a
### Run "slim.bat -h" to other function
*           slim.bat -h

SBL Binary Output
===================
* $(SOURCE_DIR)\Build\XXX.bin

SBL Source Commit
=================
* New Project used new branch
* 當要Checkin 到Ghub 時要使用SSH 來做Checkout 相關金鑰 請洽管理者
*           git@github.com:Advgcipc/slimbootloader.git

![Alt text](https://git-scm.com/images/logo@2x.png "Git")

Git Check In Github
===================
# Add all of source codes in local resp
*           git add .
# Commit and update message
*           git commit -m "Update code."
# Push local resp to remote resp with password
*           git push

## create new branch
*           git branch newproject
## swtich branch
*           git checkout branch
## swtich branch
*           git checkout branch
## swtich branch
*           git tag 
## Show revsion at one line
*           git log --pretty=oneline
## Show branch revsion
*           git rev-parse master
## Show branch short revsion
*           git rev-parse --short HEAD




