# packer

HashiCorp Packer repo for creating CentOS 7 AIM's for Genesis

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
