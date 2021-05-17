#### Chocolatey Commands

choco source

choco source list

choco source add -n=bob -s="https://somewhere/out/there/api/v2/"

choco source add -n=bob -s "'https://somewhere/out/there/api/v2/'" -cert=\Users\bob\bob.pfx

choco source add -n=bob -s "'https://somewhere/out/there/api/v2/'" -u=bob -p=12345

choco source disable -n=bob

choco source enable -n=bob

choco source remove -n=bob

choco source add -n=energy-dev-choco -s="https://siemens.jfrog.io/artifactory/api/nuget/energy-dev-choco" -u="yifei.song@siemens.com" -p=YOURACCESSTOKEN

choco install <chocoPackageName>
  
choco list -local
  
更改choco的proxy
C:\ProgramData\chocolatey\config

#### PowerShell Commands

Get-InstalledModule

