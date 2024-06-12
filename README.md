Fork of: https://github.com/microsoft/msquic

To merge with latest msquic, use: `git rebase upstream/main`

Modified to compile for Path with Intel compiler and MSVC 2022.

Powershell:

`./scripts/prepare-machine.ps1`

Then:

* Add `$Arguments += " -T ""Intel C++ Compiler 2024"""` to the `build.ps1` script before running it, to generate with the Intel compiler toolset.

`./scripts/build.ps1 -Config Release -Arch x64 -Static -Tls schannel -DisableLogs -DisableTools -DisablePerf -DisableTest -StaticCRT -PGO -Clean`

* Access .sln in build folder.
* Set the optimizations to be the same as Path. Be sure in Debug to disable /Qipo, /LTCG, Whole Program Optimization, etc.
* Build `core` and `platform` projects.
* Copy over the `core.lib` and `platform.lib` files from `...\msquic\build\windows\x64_schannel\obj`
* Include libs in project settings: `core.lib;platform.lib;wbemuuid.lib;winmm.lib;secur32.lib;onecore.lib;`
