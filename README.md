Fork of: https://github.com/microsoft/msquic

To merge with latest msquic, use: `git rebase upstream/main`

Modified to compile for Path with Intel compiler, MSVC 2022, and Whole Program Optimization.

Powershell:

`./scripts/prepare-machine.ps1`

Then:

`./scripts/build.ps1 -Config Release -Arch x64 -Static -Tls schannel -DisableLogs -DisableTools -DisablePerf -DisableTest -StaticCRT -PGO -Clean`

* Access .sln in build folder.
* You only need to build 'core' and 'platform' separately from the rest.
* Change to Intel compiler and disable warnings as errors.
* Enable same optimizations as Path has for Debug and Release modes (keep an eye on /Qipo, Whole Program Optimization, and Link Time Code Generation).
* Build projects 'core' and 'platform' within MSVC with Intel compiler.
* Find the two .lib files needed at: `msquic\build\windows\x64_schannel\obj\...`
* Link with `core.lib;platform.lib;wbemuuid.lib;winmm.lib;secur32.lib;onecore.lib;`
