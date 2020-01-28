<!--- @file
  1.3 Terminology

  Copyright (c) 2019, Intel Corporation. All rights reserved.<BR>

  Redistribution and use in source (original document form) and 'compiled'
  forms (converted to PDF, epub, HTML and other formats) with or without
  modification, are permitted provided that the following conditions are met:

  1) Redistributions of source code (original document form) must retain the
     above copyright notice, this list of conditions and the following
     disclaimer as the first lines of this file unmodified.

  2) Redistributions in compiled form (transformed to other DTDs, converted to
     PDF, epub, HTML and other formats) must reproduce the above copyright
     notice, this list of conditions and the following disclaimer in the
     documentation and/or other materials provided with the distribution.

  THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR
  IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
  MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO
  EVENT SHALL TIANOCORE PROJECT  BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
  PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
  OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
  WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
  OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF
  ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

-->

## 1.3 Terminology

| `Term`           | `Definition`                                                                                                                                                                                        |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ACM              | Authenticated Code Module                                                                                                                                                                           |
| ACPI             | Advanced Configuration and Power Interface                                                                                                                                                          |
| BCT              | Intel Binary Configuration Tool                                                                                                                                                                     |
| BFV              | Boot Firmware Volume                                                                                                                                                                                |
| BoardPkg         | The EDK II package a developer creates to port the Minimum Platform for their motherboard or family of motherboards                                                                                 |
| BSF              | Boot Setting File                                                                                                                                                                                   |
| CAR              | Cache-As-RAM                                                                                                                                                                                        |
| Component        | An executable binary. Typically UEFI defined, e.g. PEIM, DXE driver, SMM driver, or UEFI application. Also used to refer to other system binaries. Not appropriate for statically linked libraries. |
| DXE              | Driver execution environment. Role is to load drivers for system devices. Finds and executes boot code. After OS loads, it handles OS to UEFI calls.                                                |
| DSDT             | Differentiated System Description Table                                                                                                                                                             |
| EC               | Embedded Controller                                                                                                                                                                                 |
| EDK              | EFI Development Kit                                                                                                                                                                                 |
| FACS             | Firmware ACPI Control Structure                                                                                                                                                                     |
| FADT             | Firmware ACPI Description Table                                                                                                                                                                     |
| FFS              | EFI Firmware File System Specification                                                                                                                                                              |
| FRU              | Field Replaceable Unit, the minimal silicon that can be added or removed from a system, e.g.                                                                                                        |
|                  | an SoC, a MCP, a standalone processor or PCH.                                                                                                                                                       |
| FSP              | Intel&reg; Firmware Support Package                                                                                                                                                                   |
| Full Platform    | A platform implementation that includes the minimal features, as well as some number of advanced features. (Stage I-VII). Note: most advanced features may not be described in this document.       |
| FV               | Firmware Volume, a UEFI Forum defined firmware storage container                                                                                                                                    |
| GPIO             | General Purpose Input/Output                                                                                                                                                                        |
| GUID             | Globally Unique Identifier(s)                                                                                                                                                                       |
| HOB              | Hand Off Blocks(s)                                                                                                                                                                                  |
| Hybrid EDKII     | Any Module that contains both EDKII compliant wrapper code, and non EDK payloads (e.g., CSM-bin or FSP-bin)                                                                                         |
| IBB              | Initial Boot Block                                                                                                                                                                                  |
| IFWI             | Integrated Firmware Image, includes things like UEFI firmware, microcode, microcontroller and firmware, configuration data.                                                                         |
| `Term`           | `Definition`                                                                                                                                                                                        |
| IPL              | Initial Program Load                                                                                                                                                                                |
| MASM             | Microsoft Macro Assembler                                                                                                                                                                           |
| Minimum Platform | A platform implementation that only includes the minimal features. (Stage I-VII)                                                                                                                    |
| MinPlatformPkg   | The EDK II package that contains common elements of the platform architecture.                                                                                                                      |
| Module           | Typically any EDK II independently buildable item, includes static libraries and executables.                                                                                                       |
| MOR              | Memory Overwrite Request. See Trusted Computing Group documentation.                                                                                                                                |
| MTRR             | Memory Type Range Register                                                                                                                                                                          |
| NASM             | Netwide Assembler                                                                                                                                                                                   |
| Native EDKII     | All modules build with only EDKII compliant source code, and no non-EDK payloads (e.g., CSM-bin, LegacyOpRom, or FSP-bin)                                                                           |
| NVRAM            | Non-Volatile Random Access Memory                                                                                                                                                                   |
| OBB              | OEM Boot Block                                                                                                                                                                                      |
| OPROM            | Option ROM                                                                                                                                                                                          |
| PCD              | Platform Configuration Database                                                                                                                                                                     |
| PEI              | Pre EFI Initialization. Role is to initialize memory, and also initialize enough of the system to run DXE.                                                                                          |
| PEIM             | Pre-EFI Initialization Module                                                                                                                                                                       |
| PI               | Platform Initialization                                                                                                                                                                             |
| PPI              | PEIM-to-PEIM Interface                                                                                                                                                                              |
| RSDP             | Root System Description Pointer                                                                                                                                                                     |
| RSDT             | Root System Description Table                                                                                                                                                                       |
| SEC              | Security phase. Role is to initialize the system far enough to find, validate, install and run PEI.                                                                                                 |
| SiliconPkg       | The EDK II Package that contains silicon support for a system.                                                                                                                                      |
| SIO              | Super I/O is a type of I/O controller IP. Typical functionality provided are one or more serial port UARTs, keyboard controller, and many others.                                                   |
| SMBIOS           | System Management BIOS                                                                                                                                                                              |
| SMM              | System Management Mode                                                                                                                                                                              |
| SSDT             | Secondary System Description Table                                                                                                                                                                  |
| T-RAM            | Temporary RAM (memory used before permanent memory is initialized such as CAR)                                                                                                                      |
| TPM              | Trusted Platform Module                                                                                                                                                                             |
| UEFI             | Unified Extensible Firmware Interface                                                                                                                                                               |
| UPD              | Updatable Product Data                                                                                                                                                                              |
| XSDT             | Extended System Description Table                                                                                                                                                                   |

###### Table 2 Terminology
