# Android

## Install dependencies

* libogg: [Download](https://xiph.org/downloads/), unzip it in `dependencies/android/libogg`, then navigate to `libogg/include/ogg` and run: `git restore config_types.h`.

* libtheora: [Download](https://github.com/xiph/theora/releases/tag/v1.1.0) and unzip it in `dependencies/android/libtheora`.

## Set up symlinks

* Ensure the symbolic links in `[root]/android/app/jni` are correct:
  * `Game` -> root of the **Sonic-Mania-Decompilation** repo (or any other game that you may be compiling)
  * Extra symbolic links can be added for things like mods, **as mods do not use the local files for logic.** Just ensure that there are `CMakeLists.txt` files at the root of them. **If you want to know how to do it, [go here](https://github.com/MegAmi24/Mania-Decomp-Mods/blob/main/BUILDING.md)**
  
    To add symbolic links, do the following:
      * Windows: `mklink /d "[name-of-symlink]" "[path]"`
      * Linux: `ln -s "[path]" "[name-of-symlink]"`
      * MacOS: `ln -s "[path]" "[name-of-symlink]"` **(Basically the same as the Linux command)**
* Open `[root]/android/` in Android Studio, install the NDK and everything else that it asks for, and build.

**GL shaders are not required,
## Common build issues (Windows)
### `make: *** INTERNAL: readdir: No such file or directory`
Delete `android/app/build` and try again. This occurs when the path is short enough to build, but too long for a rebuild. 
### `make: Interrupt/exception caught (code = 0xc0000005)`
Your paths are too long. Try renaming the symbolic links to something shorter, or make a symbolic link to RSDKv5 closer to the root of the drive and open the project through there (e.x. C:/RSDKv5/android). *I haven't had either issue since I did this.*
