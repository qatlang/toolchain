This repository provides SDK of different operating systems, so as to enable cross-compilation

**I do not expect you to blindly trust these files. In the case of cross-compilation, the `qat` compiler just expects these files to be present in the installation directory. You can use your own versions of the files if you can obtain them. Just follow the default directory structure expected by the compiler**

### Windows

Windows specific files include the MSVC libraries and Windows SDK files. The MSVC libraries are obtained from the following path:

```
C:/Program Files/Microsoft Visual Studio/2022/Community/VC/Tools/MSVC/14.32.31326/lib
```

Inside the `lib` folder, there are folders for different architectures supported by Windows, namely, `x64`, `x86`, `arm64`, `arm`, `onecore/x64`, `onecore/x86`.

The Windows OS SDKs are also included. These are specific to major releases of the Windows OS. For the SDK, the only relevant directories are the ones containing the UCRT and UM libraries. For example, if you have the SDK for Windows 11 installed, the path could be,

```
C:/Program Files (x86)/Windows Kits/10/Lib/10.0.19041.0/
```

> Remember than on Windows, _file names are case insensitive_, but **on other platforms, that is not the case**. So in a cross-compilation setup, make sure that the case is preserved, as the compiler will use the default case for names.

In the `toolchain` folder inside the qat installation directory, the directory structure for Windows would be:

- windows
  - MSVC
    - (MSVC Major Version)
      - lib
        - x64
        - x86
        - arm64
        - arm
        - onecore
          - x64
          - x86
  - SDK
    - (OS Version)
      - Lib
        - (SDK Version)
          - ucrt
            - x64
            - x86
            - arm64
            - arm
          - um
            - x64
            - x86
            - arm64
            - arm

In the above directory structure,

- `MSVC Major Version` is always a number. Even though there is a complete version of MSVC in the path from where the files are obtained, this value expects only the major version like 14, 11 ...

- `OS Version` have the following possible values: `10`, `8.1`, `7.1`

- `SDK Version` have many possible values, but usually resemble the format `10.0.19041.0`

