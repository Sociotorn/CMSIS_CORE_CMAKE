# CMSIS Version 5 Core CMake
This fork of CMSIS_5 adds CMake support to Core(M). This allows for the easy integration of these libraries into a microcontroller
project. All other components except Driver(which can be used for reference) have been removed as they are unused. Support for Core(A) is currently not implemented.

[![Version](https://img.shields.io/github/v/release/arm-software/CMSIS_5)](https://github.com/ARM-software/CMSIS_5/releases/latest) [![License](https://img.shields.io/github/license/arm-software/CMSIS_5)](https://arm-software.github.io/CMSIS_5/General/html/LICENSE.txt)

The branch *master* of this GitHub repository contains ![Version](https://img.shields.io/github/v/release/arm-software/CMSIS_5?display_name=release&label=%20&sort=semver).
The [documentation](http://arm-software.github.io/CMSIS_5/General/html/index.html) is available under http://arm-software.github.io/CMSIS_5/General/html/index.html


**Note:** The branch *develop* of this GitHub repository reflects our current state of development and is constantly updated. It gives our users and partners contiguous access to the CMSIS development. It allows you to review the work and provide feedback or create pull requests for contributions.

A [pre-built documentation](https://arm-software.github.io/CMSIS_5/develop/General/html/index.html) is updated from time to time, but may be also generated using the instructions under [Generate CMSIS Pack for Release](https://github.com/ARM-software/CMSIS_5#generate-cmsis-pack-for-release).

## Overview of CMSIS Components

The following is an list of all CMSIS components that are available.

| CMSIS-... | Target Processors   | Description  |
|:----------|:--------------------|:-------------|
|[Core(M)](http://arm-software.github.io/CMSIS_5/Core/html/index.html)  | All Cortex-M, SecurCore | Standardized API for the Cortex-M processor core and peripherals. Includes intrinsic functions for Cortex-M4/M7/M33/M35P SIMD instructions.|
|[Core(A)](http://arm-software.github.io/CMSIS_5/Core_A/html/index.html)| Cortex-A5/A7/A9 | API and basic run-time system for the Cortex-A5/A7/A9 processor core and peripherals.|
|[Driver](http://arm-software.github.io/CMSIS_5/Driver/html/index.html) | All Cortex-M, SecurCore | Generic peripheral driver interfaces for middleware. Connects microcontroller peripherals with middleware that implements for example communication stacks, file systems, or graphic user interfaces.|

**Note:** CMSIS-DSP moved off into its [own repository](https://github.com/ARM-software/CMSIS-DSP), see below.

## Other related GitHub repositories

| Repository                  | Description                                               |
|:--------------------------- |:--------------------------------------------------------- |
| [cmsis-pack-eclipse](https://github.com/ARM-software/cmsis-pack-eclipse)    |  CMSIS-Pack Management for Eclipse reference implementation Pack support  |
| [CMSIS-FreeRTOS](https://github.com/arm-software/CMSIS-FreeRTOS)            | CMSIS-RTOS adoption of FreeRTOS                                                      |
| [CMSIS-Driver](https://github.com/arm-software/CMSIS-Driver)                | Generic MCU driver implementations and templates for Ethernet MAC/PHY and Flash.  |
| [CMSIS-Driver_Validation](https://github.com/ARM-software/CMSIS-Driver_Validation) | CMSIS-Driver Validation can be used to verify CMSIS-Driver in a user system |
| [CMSIS-DSP](https://github.com/ARM-software/CMSIS-DSP)                      | DSP library collection with hundreds of functions for various data types: fixed-point (fractional q7, q15, q31) and single precision floating-point (32-bit). Implementations optimized for the SIMD instruction set are available for Armv7E-M and later devices. |
| [CMSIS-Zone](https://github.com/ARM-software/CMSIS-Zone)                    | CMSIS-Zone Utility along with example projects and FreeMarker templates         |
| [NXP_LPC](https://github.com/ARM-software/NXP_LPC)                          | CMSIS Driver Implementations for the NXP LPC Microcontroller Series       |
| [mdk-packs](https://github.com/mdk-packs)                                   | IoT cloud connectors as trail implementations for MDK (help us to make it generic)|
| [trustedfirmware.org](https://www.trustedfirmware.org/)                     | Arm Trusted Firmware provides a reference implementation of secure world software for Armv8-A and Armv8-M.|


## Directory Structure

| Directory            | Content                                                   |
|:-------------------- |:--------------------------------------------------------- |
| CMSIS/Core           | CMSIS-Core(M) related files (for release)                 |
| CMSIS/Core_A         | CMSIS-Core(A) related files (for release)                 |
| CMSIS/CoreValidation | Validation for Core(M) and Core(A) (NOT part of release)  |
| CMSIS/Driver         | CMSIS-Driver API headers and template files               |

## Generate CMSIS Pack for Release

This GitHub development repository lacks pre-built libraries of various software components (RTOS, RTOS2).
In order to generate a full pack one needs to have the build environment available to build these libraries.
This causes some sort of inconvenience. Hence the pre-built libraries may be moved out into separate pack(s)
in the future.

To build a complete CMSIS pack for installation the following additional tools are required:
 - **doxygen.exe**    Version: 1.8.6 (Documentation Generator)
 - **mscgen.exe**     Version: 0.20  (Message Sequence Chart Converter)
 - **7z.exe (7-Zip)** Version: 16.02 (File Archiver)

Using these tools, you can generate on a Windows PC:
 - **CMSIS Documentation** using the batch file **gen_doc.sh** (located in ./CMSIS/Doxygen).
 - **CMSIS Software Pack** using the batch file **gen_pack.sh** (located in ./CMSIS/Utilities).
   The bash script does not generate the documentation. The pre-built libraries for RTX4 and RTX5
   are not included within this repository.

The file ./CMSIS/DoxyGen/How2Doc.txt describes the rules for creating API documentation.

## License

Arm CMSIS is licensed under Apache 2.0.

## Contributions and Pull Requests

Contributions are accepted under Apache 2.0. Only submit contributions where you have authored all of the code.

