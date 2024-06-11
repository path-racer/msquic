Modified to compile with Intel compiler and MSVC 2022.

Powershell:

`./scripts/prepare-machine.ps1`

Then:

`./scripts/build.ps1 -Config Release -Arch x64 -Static -Tls schannel -DisableLogs -DisableTools -DisablePerf -DisableTest -StaticCRT -PGO -Clean`
