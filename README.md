# learning-histogram
C++ etude for Boost Histogram


## Build

On Windows with powershell:

|Name|                    Version|                 
|----|                    -------|                 
cmake|                   3.25.2                                 
mingw-winlibs-llvm-ucrt| 12.2.0-16.0.0-10.0.0-r5 
ninja|                   1.11.1                  


```powershell
$ cmake -S . -B build/ -G Ninja
$ cmake --build .\build\
$ .\build\apps\cli.exe -l -1 -r 1 -m 0,0,0,0.5,-0.25,3,-20
```
