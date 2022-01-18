# Building WAVM from source

To build WAVM, you'll need CMake and the latest LLVM [LLVM 13.0+](https://releases.llvm.org/).
If CMake can't find your LLVM directory, you can manually give it the location in the LLVM_DIR CMake
configuration variable. Note that on Windows, you must compile LLVM from source, and manually point
the LLVM_DIR configuration variable at `<LLVM build directory>\lib\cmake\llvm`.

### Prerequisites

* **CMake 3.8 or higher** - On Linux, it is probably available via your
package manager. For example, you can install it on Ubuntu with `sudo apt install cmake`.
Otherwise, you can download it from the [CMake website](https://cmake.org/download/).

#### Windows

You can use Visual Studio 2019+ to compile WAVM. If you don't have Visual Studio, you can use the
freely available Visual Studio C++ Build Tools for Visual Studio or Visual Studio Community, both
available from the Visual Studio [download page](https://visualstudio.microsoft.com/downloads/).

#### Linux

You'll need a C/C++ compiler. `gcc` and `clang` are known to compile WAVM correctly.

#### MacOS

You'll need to install Xcode from the App Store.

### Configure a WAVM build

1) Create a new directory: `<build_dir>`

2) In a shell, navigate to that directory, and run:
    ```
    cmake <path to WAVM source> -G <generator> -DLLVM_DIR=<path to LLVM build>/lib/cmake/llvm
    ```
   
   What you pass as `<generator>` depends on your platform:
   * For Windows, you'll use either `"Visual Studio 16 2019"` (aka Visual Studio 2019) OR  `"Visual Studio 17 2022"` (aka Visual Studio 2022)
   * For Linux and MacOS, you'll use `"Unix Makefiles"`.
   
   If `cmake` executes successfully, it will create either a Visual Studio solution file or
   makefiles in `<build_dir>`, depending on the generator used.

### Building WAVM

3) On MacOS and Linux, in the `<build_dir>` that you configured in the previous step, simply run
   the `make` command.

   On Windows, open `<build_dir>/WAVM.sln` in Visual Studio and build the solution.

4) If the build completed successfully, the WAVM executable will now be in `<build_dir>/bin`.

## Continue to: [Exploring the WAVM source](CodeOrganization.md)
