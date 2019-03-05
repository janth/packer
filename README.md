# packer

HashiCorp Packer repo for creating CentOS 7 AIM's for Genesis

## Overview

packer reads vbox.json
which pulls down CentOS 7 minimal iso (or uses previous fetched iso)
and defines the vbox machine
boot the vbox-vm
uses [packer_httpd/ks.cfg](packer_httpd/ks.cfg) to kickstart the CentOS install
then calls install-ansible.sh
halts the vbox-vm and place a vdi file in [ami-builds/](ami-builds/)

This VM has only single disk.
To resemble our current EC2's, add more disks which terraform,
or VirtualBox / Hyper-V using script.


## TODO
* Hyper-V in addition to vbox, or switch to only Hyper-V?
* use the packer ansible provider to run our ansible scripts
* push to AWS


## Installl packer

https://www.packer.io/downloads.html


## Howto build

**NB! This has to be done __outside__ WSL!!!**
```
packer validate vbox.json
packer inspect vbox.json
packer build vbox.json
packer build --force vbox.json
```

## Debug
How to debug packer: https://www.packer.io/docs/other/debugging.html

PowerShell: 
```
env:PACKER_LOG=1
$env:PACKER_LOG_PATH="packerlog.txt"
```
