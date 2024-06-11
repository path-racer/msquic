Fork of: https://github.com/microsoft/msquic

Modified to compile for Path with Intel compiler and MSVC 2022.

Powershell:

`./scripts/prepare-machine.ps1`

Then:

`./scripts/build.ps1 -Config Release -Arch x64 -Static -Tls schannel -DisableLogs -DisableTools -DisablePerf -DisableTest -StaticCRT -PGO -Clean`

Access .sln in build folder, change projects to use Intel compiler, enable all optimizations as well as Whole Program Optimization.
