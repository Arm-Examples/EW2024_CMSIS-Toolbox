# CMSIS-Toolbox Examples for Embedded World paper

This repository contains examples for Embedded World 2024 paper:
  [**Simplifying the integration of software components in modern microcontroller systems**](paper.md)

The examples can work with two FPGA platforms from Arm®:

- Arm MPS2/MPS2+ FPGA
- Arm MPS3 FPGA (With Cortex-M55 FPGA image AN552 and fewer number of examples)

## Setup / installation

This repository contains the following external submodules:

- SPEC®'s CoreMark (https://github.com/eembc/cormark)
  - License details for CoreMark is available in https://github.com/eembc/coremark/blob/main/LICENSE.md
  - For more information about CoreMark, please visit https://www.eembc.org/coremark/
- SPEC's CoreMark-Pro (https://github.com/eembc/cormark-pro)
  - License details for CoreMark-Pro is available in https://github.com/eembc/coremark-pro/blob/main/LICENSE.md
  - For more information about CoreMark-Pro, please visit https://www.eembc.org/coremark-pro/

These benchmarks are used as project examples to illustrate how csolution project format and CMSIS-Toolbox can be deployed.

To check out the repository:

```
> git clone https://github.com/Arm-Examples/EW2024_CMSIS-Toolbox
> cd EW2024_CMSIS-Toolbox
> git submodule update --init
```

To run the examples, you need to install:

- CMSIS-Toolbox (See releases in https://github.com/Open-CMSIS-Pack/cmsis-toolbox/releases)
  - Minimum version is 2.0.0
- CMAKE
  - If using Linux, you can install CMAKE using "sudo apt install cmake".
  - Alternatively you can find installers from https://cmake.org/download
- Ninja-build
  - If using Linux, you can install Ninja-build using "sudo apt install ninja-build"
  - Alternatively you can find installers from https://ninja-build.org
- One of the compilation toolchains
  - Arm Compiler 6 (https://developer.arm.com/Tools%20and%20Software/Arm%20Compiler%20for%20Embedded)
  - LLVM Embedded Toolchain for Arm (https://github.com/ARM-software/LLVM-embedded-toolchain-for-Arm)
    - Minimum version 17.0.1
  - GCC (https://developer.arm.com/Tools%20and%20Software/GNU%20Toolchain)
    - Minimum version 10.3.1
  - IAR Compiler
    - If using Embedded Workbench for ARM (EWARM), minimum version is 9.50.
    - If using IAR build tools for Arm (BXARM), most recent versions should be suitable.

After installing the tools, you need to setup a local CMSIS-PACK storage location and environment variables for the CMSIS-Toolbox to work. Please see the details from CMSIS-Toolbox documentation: https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/installation.md

## Examples in this repository

This repository contains the following examples:

- Example 1: A minimal blinky project
  - example1_cm4_mps2_an386  : For MPS2/MPS2+ with Cortex-M4 FPGA image (AN386) [![CMSIS Compliance](https://img.shields.io/github/actions/workflow/status/Arm-Examples/EW2024_CMSIS-Toolbox/verify-example1_cm4_mps2_an386.yml?logo=arm&logoColor=0091bd&label=CMSIS%20Compliance)](https://www.keil.arm.com/cmsis)
  - example1_cm55_mps3_an552 : For MPS3 with Cortex-M55 FPGA image (AN552) [![CMSIS Compliance](https://img.shields.io/github/actions/workflow/status/Arm-Examples/EW2024_CMSIS-Toolbox/verify-example1_cm55_mps3_an552.yml?logo=arm&logoColor=0091bd&label=CMSIS%20Compliance)](https://www.keil.arm.com/cmsis)
- Example 2: Hello world based on CMSIS-Compiler, with printf message(s) output via a UART interface.
  - example2_cm4_mps2_an386  : For MPS2/MPS2+ with Cortex-M4 FPGA image (AN386) [![CMSIS Compliance](https://img.shields.io/github/actions/workflow/status/Arm-Examples/EW2024_CMSIS-Toolbox/verify-example2_cm4_mps2_an386.yml?logo=arm&logoColor=0091bd&label=CMSIS%20Compliance)](https://www.keil.arm.com/cmsis)
  - example2_cm55_mps3_an552 : For MPS3 with Cortex-M55 FPGA image (AN552) [![CMSIS Compliance](https://img.shields.io/github/actions/workflow/status/Arm-Examples/EW2024_CMSIS-Toolbox/verify-example2_cm55_mps3_an552.yml?logo=arm&logoColor=0091bd&label=CMSIS%20Compliance)](https://www.keil.arm.com/cmsis)
- Example 3: Compilation of the SPEC's CoreMark benchmark to demonstrate compiler options and linker script setup.
  - example3_cm4_mps2_an386  : For MPS2/MPS2+ with Cortex-M4 FPGA image (AN386) [![CMSIS Compliance](https://img.shields.io/github/actions/workflow/status/Arm-Examples/EW2024_CMSIS-Toolbox/verify-example3_cm4_mps2_an386.yml?logo=arm&logoColor=0091bd&label=CMSIS%20Compliance)](https://www.keil.arm.com/cmsis)
- Example 4: A modified version of the example 3 to support multiple types of FPGA images.
  - example4_mps2_multi_devices : For MPS2/MPS2+ and MPS3 FPGA images including: [![CMSIS Compliance](https://img.shields.io/github/actions/workflow/status/Arm-Examples/EW2024_CMSIS-Toolbox/verify-example4_mps2_multi_devices.yml?logo=arm&logoColor=0091bd&label=CMSIS%20Compliance)](https://www.keil.arm.com/cmsis)
    - AN382: [MPS2/MPS2+] Cortex-M0 with CMSDK (Cortex-M System Design Kit)
    - AN383: [MPS2/MPS2+] Cortex-M0+ with CMSDK (Cortex-M System Design Kit)
    - AN385: [MPS2/MPS2+] Cortex-M3 with CMSDK (Cortex-M System Design Kit)
    - AN386: [MPS2/MPS2+] Cortex-M4 with CMSDK (Cortex-M System Design Kit)
    - AN500: [MPS2+] Cortex-M7 with CMSDK (Cortex-M System Design Kit)
    - AN505: [MPS2+] Cortex-M33 with IoTKit
    - AN519: [MPS2+] Cortex-M23 with IoTKit
    - AN552: [MPS3] Cortex-M55 with Corstone-300
    - AN555: [MPS3] Cortex-M85 with Corstone-310
- Example 5: Compilation of the SPEC's CoreMark-Pro benchmark to demonstrate multiple projects in a CMSIS solution, as well as using clayer.
  - example5_multi_projects  : For MPS2/MPS2+ with Cortex-M7 FPGA image (AN500) [![CMSIS Compliance](https://img.shields.io/github/actions/workflow/status/Arm-Examples/EW2024_CMSIS-Toolbox/verify-example5_multi_projects.yml?logo=arm&logoColor=0091bd&label=CMSIS%20Compliance)](https://www.keil.arm.com/cmsis)

In each of the example directories, there is a makefile and a batch file to help you to go through different steps.

- Before using the makefile, you can edit the file to update the TOOLCHAIN setting based on your preference. Alternatively you can override the TOOLCHAIN setting when involving make in the command line.
- Before using the batch file, please edit the TOOLCHAIN setting based on your preference.

The file [vcpkg-configuration.json](./vcpkg-configuration.json) is for Arm Keil Studio Pack to download toolchains.
More information about Arm Keil Studio Pack can be found [here](https://marketplace.visualstudio.com/items?itemName=Arm.keil-studio-pack).

Arm Tools available in vcpkg can be found [here](https://www.keil.arm.com/artifacts/).

## Limitations

Please note that the examples currently have the following limitations:

- When using the makefiles the first time to download CMSIS-PACK, the tool might report an error after downloading the pack and stop. This is because some of the packs are not aware of CMSIS-CORE in the CMSIS version 6. However, the projects are compatible with CMSIS 6 and you can ignore the error(s) and just rerun the make to compile the projects. 
- One of the tests in CoreMark-Pro (Zip-test) in Example 5 contains C source file that is not compatible to modern C standard and therefore cannot be compiled with IAR toolchain. As a result this test is disabled.
- When using IAR EWARM debugger with Cortex-M55/Cortex-M85 FPGA, please select JTAG debug protocol and the connection speed need to be set to 24MHz or lower.
- The makefiles have not been tested with IAR Build Tools for Arm. However, the projects have been tested with IAR EWARM toolchain.

## Disclaimers

- CoreMark and CoreMark-Pro are benchmarks from SPEC® Embedded Group (formerly EEMBC®) and are not properties of Arm.
- The compilation options for CoreMark and CoreMark-Pro used in these examples have not been tested for best performance.
