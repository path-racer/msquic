Fork of: https://github.com/microsoft/msquic

To merge with latest msquic, use: `git rebase upstream/main`

Modified to compile for Path with Intel compiler, MSVC 2022, and Whole Program Optimization.

Powershell:

`./scripts/prepare-machine.ps1`

Then:

`./scripts/build.ps1 -Config Release -Arch x64 -Static -Tls schannel -DisableLogs -DisableTools -DisablePerf -DisableTest -StaticCRT -PGO -Clean`

* Access .sln in build folder, change projects to use Intel compiler.
* Enable all optimizations, as well as Whole Program Optimization and Link Time Code Generation.
* Disable warnings as errors on all projects.
* Build within MSVC with Intel compiler.
