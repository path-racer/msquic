Fork of: https://github.com/microsoft/msquic

To merge with latest msquic, use: `git rebase upstream/main`

Modified to compile for Path with Intel compiler and MSVC 2022.

Powershell:

`./scripts/prepare-machine.ps1`

Then:

* Add `$Arguments += " -T ""Intel C++ Compiler 2024"""` to the `build.ps1` script before running to generate with the Intel compiler toolset.

`./scripts/build.ps1 -Config Release -Arch x64 -Static -Tls schannel -DisableLogs -DisableTools -DisablePerf -DisableTest -StaticCRT -PGO -Clean`

* Enter the `C:\Users\Chris\Desktop\msquic\src\bin` directory.
* Add `set(CMAKE_AR "C:/Program Files/LLVM/bin/llvm-ar.exe")` and `set(CMAKE_INTERPROCEDURAL_OPTIMIZATION TRUE)` to the very top of `CMakeLists.txt`.
* Access .sln in build folder.
* Set the optimizations to be the same as Path.
* Build `core`, `msquic_static`, and `platform` projects.
* Enter the `...\msquic\build\windows\x64_schannel\src\bin\` directory.
* Edit the `quicdeps.txt` files in the Release and Debug folders, which gives the `llvm-ar` commands:

`rcs "...\msquic\artifacts\bin\windows\x64_Release_schannel/msquic.lib" 
".../msquic/build/windows/x64_schannel/obj/Debug/msquic_static.lib" 
".../msquic/build/windows/x64_schannel/obj/Debug/core.lib" 
".../msquic/build/windows/x64_schannel/obj/Debug/platform.lib" 
"C:/Program Files (x86)/Windows Kits/10/Lib/10.0.22621.0/um/x64/wbemuuid.lib" 
"C:/Program Files (x86)/Windows Kits/10/Lib/10.0.22621.0/um/x64/winmm.lib" 
"C:/Program Files (x86)/Windows Kits/10/Lib/10.0.22621.0/um/x64/secur32.lib" 
"C:/Program Files (x86)/Windows Kits/10/Lib/10.0.22621.0/um/x64/onecore.lib"`

* The resulting `msquic.lib` file should be in the `msquic/artifacts/bin/windows` folder.
