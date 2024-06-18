# CoreMark-Pro example for Cortex-M running on Arm MPS2/MPS2+ FPGA board
[![CMSIS Compliance](https://img.shields.io/github/actions/workflow/status/Arm-Examples/EW2024_CMSIS-Toolbox/verify-example5_multi_projects.yml?logo=arm&logoColor=0091bd&label=CMSIS%20Compliance)](https://www.keil.arm.com/cmsis)

## Descriptions

Execute CoreMark-Pro and use a SysTick timer to generate timer tick interrupts for timing measurement.

The printf is handled by CMSIS-Compiler, with uart_funcs.c provides the low level UART functions and interface to CMSIS-Compiler.

The UART is configured as 38400bps, 8-bit, no parity.

## Documentation related to the system

* [Application Note AN500 - ARM Cortex-M7 SMM on V2M-MPS2](https://developer.arm.com/documentation/dai0500/latest/)
* [Arm MPS2 and MPS2+ FPGA Prototyping Boards Technical Reference Manual](https://developer.arm.com/documentation/100112/latest/)
* [MPS2+ FPGA Prototyping board](https://developer.arm.com/Tools%20and%20Software/MPS2%20Plus%20FPGA%20Prototyping%20Board)
* [Download FPGA images (Please see VEM31)](https://developer.arm.com/downloads/-/download-fpga-images)

## Steps to use this demo using command line interface

Before starting, edit coremark-pro.csolution.yml to select toolchain (GCC/CLANG/AC6/IAR).

```
/* Step 1 : Update local copy of pack index */
cpackget update-index
```

Note: Not required for a new installation and usually this is not needed. But if the local CMSIS-Pack storage hasn't been used for a while, it worth running it to ensure the index is up-to-date.

```
/* Step 2: Generate the list of missing packs */
csolution list packs -s coremark-pro.csolution.yml -m > required_packs.txt
```

```
/* Step 3: Install missing packs */
cpackget add -f required_packs.txt
```

```
/* Step 4: Generate build information */
csolution convert -s coremark-pro.csolution.yml
```

```
/* Step 5: Compile project with cbuild */
cbuild proj_{project_name}/{project_name}+MPS2_CM7_DP.cprj
```

Note: For IAR only - Instead of running step 4 and step 5, you can import csolution project in EWARM to compile the project.

## Disclaimers

* CoreMark-Pro is a benchmark from SPEC Embedded Group (formerly EEMBC) and is not property of Arm.
* The compilation options for CoreMark and CoreMark-Pro used in these examples have not been tested for best performance.
