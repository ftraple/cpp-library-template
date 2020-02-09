# Cpp Library Template

This a template to create a c++ library using [cmake](https://cmake.org/) and 
[Google Test Framework](https://github.com/google/googletest).

## How To Download

Clone the repository with git.
```bash
git clone --recursive git@github.com:ftraple/cpp-library-template.git
```
The **--recursive** option is to download the googletest repository dependency.

If you already downloaded the library and forgot to use the **--recursive** option, 
use the command below inside the project folder to download the submodules.

```bash
cd cpp-library-template
git submodule update --init --recursive
```

## How To Compile, Test and Install

The commands below will compile the library tests.

```bash
cd cpp-library-template
mkdir build
cd build
cmake ..
make
```
To run the tests use the command below inside the build folder.

```bash
make test
```

To install the library binaries use the command below inside the build folder.

```bash
sudo make install
```

## Guidelines

[Cpp Core Guidelines](https://github.com/isocpp/CppCoreGuidelines)
[Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html)
