<!--- @file
  6.5 Configuration

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

## 6.5 Configuration

This section defines the configurable items that must be available to achieve
Stage IV functionality.

These definitions may be both source and binary in nature.

### 6.5.1 Memory Type Information Related Configuration

| `PCD`                                                          | `Purpose`                                        |
| -------------------------------------------------------------- | ------------------------------------------------ |
| gMinPlatformPkgTokenSpaceGuid.                                 | Memory size reserved for ACPI reclaim memory     |
| PcdPlatformEfiAcpiReclaimMemorySize                            |                                                  |
| gMinPlatformPkgTokenSpaceGuid. PcdPlatformEfiAcpiNvsMemorySize | Memory size reserved for ACPI NVS memory         |
| gMinPlatformPkgTokenSpaceGuid.                                 | Memory size reserved for EFI reserved memory     |
| PcdPlatformEfiReservedMemorySize                               |                                                  |
| gMinPlatformPkgTokenSpaceGuid. PcdPlatformEfiRtDataMemorySize  | Memory size reserved for EFI runtime data memory |
| gMinPlatformPkgTokenSpaceGuid. PcdPlatformEfiRtCodeMemorySize  | Memory size reserved for EFI runtime code memory |

###### Table 49 Memory Type Information Configuration

### 6.5.2 FV Related Configuration

| `PCD`                                                | `Purpose`              |
| ---------------------------------------------------- | ---------------------- |
| `gMinPlatformPkgTokenSpaceGuid.PcdFlashFvOsBootBase` | OsBoot FV base address |
| `gMinPlatformPkgTokenSpaceGuid.PcdFlashFvOsBootSize` | OsBoot FV size         |

###### Table 50 Flash Map Configuration PCDs
