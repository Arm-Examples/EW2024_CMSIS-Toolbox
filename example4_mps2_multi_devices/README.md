# CoreMark example for Cortex-M running on Arm MPS2/MPS2+ FPGA board
[![CMSIS Compliance](https://img.shields.io/github/actions/workflow/status/Arm-Examples/EW2024_CMSIS-Toolbox/verify-example4_mps2_multi_devices.yml?logo=arm&logoColor=0091bd&label=CMSIS%20Compliance)](https://www.keil.arm.com/cmsis)

## Descriptions

Execute CoreMark and use a peripheral timer / DWT Cycle Counter for timing measurement.

The printf is handled by CMSIS-Compiler, with uart_funcs.c provides the low level UART functions and interface to CMSIS-Compiler.

UART output

- For MPS2/MPS2+, the UART is configured as 38400bps, 8-bit, no parity.
- For MPS3, the UART is configured as 115200bps, 8-bit, no parity.

## Documentation related to the system

* [Application Note AN382 - ARM Cortex-M0 SMM on V2M-MPS2](https://developer.arm.com/documentation/dai0382/latest)
* [Application Note AN383 - ARM Cortex-M0+ SMM on V2M-MPS2](https://developer.arm.com/documentation/dai0383/latest)
* [Application Note AN385 - ARM Cortex-M3 SMM on V2M-MPS2](https://developer.arm.com/documentation/dai0385/latest)
* [Application Note AN386 - ARM Cortex-M4 SMM on V2M-MPS2](https://developer.arm.com/documentation/dai0386/latest/)
* [Application Note AN500 - ARM Cortex-M7 SMM on V2M-MPS2](https://developer.arm.com/documentation/dai0500/latest/)
* [Application Note AN505 - Cortex-M33 with IoT kit FPGA for MPS2+](https://developer.arm.com/documentation/dai0505/)
* [Application Note AN519 - Cortex-M23 with IoT kit FPGA for MPS2+](https://developer.arm.com/documentation/dai0519/)
* [Application Note AN552 - Arm Corstone SSE-300 with Cortex-M55 and Ethos-U55: Example Subsystem for MPS3 (Partial Reconfiguration Design)](https://developer.arm.com/documentation/dai0552/latest/)
* [Application Note AN555 - AN555 : Arm Corstone SSE-310 with Cortex-M85 and Ethos-U55](https://developer.arm.com/documentation/107642/B/?lang=en)
* [Arm MPS2 and MPS2+ FPGA Prototyping Boards Technical Reference Manual](https://developer.arm.com/documentation/100112/latest/)
* [MPS2+ FPGA Prototyping board](https://developer.arm.com/Tools%20and%20Software/MPS2%20Plus%20FPGA%20Prototyping%20Board)
* [Arm MPS3 FPGA Prototyping Board Technical Reference Manual](https://developer.arm.com/documentation/100765/latest/)
* [Arm MPS3 FPGA Prototyping board product page](https://developer.arm.com/Tools%20and%20Software/MPS3%20FPGA%20Prototyping%20Board)
* [Download FPGA images (Please see VEM31 for Cortex-M0/M0+/M3/M4/M7)](https://developer.arm.com/downloads/-/download-fpga-images)

## Steps to use this demo using command line interface

Before starting, edit coremark.csolution.yml to select toolchain (GCC/CLANG/AC6/IAR).

```
/* Step 1 : Update local copy of pack index */
cpackget update-index
```

Note: Not required for a new installation and usually this is not needed. But if the local CMSIS-Pack storage hasn't been used for a while, it worth running it to ensure the index is up-to-date.
```
/* Step 2: Generate the list of missing packs */
csolution list packs -s coremark.csolution.yml -m > required_packs.txt
```

```
/* Step 3: Install missing packs */
cpackget add -f required_packs.txt
```

```
/* Step 4: Generate build information */
csolution convert -s coremark.csolution.yml
```

```
/* Step 5: Compile project with cbuild */
cbuild coremark+<context_name>.cprj
```
Note: <context_name> can be MPS2_CM0 / MPS2_CM0plus /
 MPS2_CM3 / MPS2_CM4 / MPS2_CM4_FP / MPS2_CM7 /
 MPS2_CM7_SP / MPS2_CM7_DP / MPS2_CM23 / MPS2_CM33 /
 MPS2_CM33_FP / MPS3-Corstone-300 / MPS3-Corstone-310

Note: For IAR only - Instead of running step 4 and step 5, you can import csolution project in EWARM to compile the project.

## Disclaimers

- CoreMark is a benchmark from SPEC Embedded Group (formerly EEMBC) and is not a property of Arm.
- The compilation options for CoreMark and CoreMark-Pro used in these examples have not been tested for best performance.
