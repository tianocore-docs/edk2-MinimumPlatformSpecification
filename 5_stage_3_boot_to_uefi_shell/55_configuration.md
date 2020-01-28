<!--- @file
  5.5 Configuration

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

## 5.5 Configuration

This section defines the configurable items that must be available to achieve
Stage III functionality.

These definitions may be both source and binary in nature.

### 5.5.1 FV Related Configuration

| `PCD`                                                | `Purpose`                 |
| ---------------------------------------------------- | ------------------------- |
| gMinPlatformPkgTokenSpaceGuid.PcdFlashFvUefiBootBase | UefiBoot FV base address. |
| gMinPlatformPkgTokenSpaceGuid.PcdFlashFvUefiBootSize | UefiBoot FV size.         |

###### Table 35 Stage III Flash Map Configuration PCDs

### 5.5.2 Driver Related Configuration

| `PCD`                                                      | `Purpose`                             |
| ---------------------------------------------------------- | ------------------------------------- |
| gEfiMdeModulePkgTokenSpaceGuid.PcdEmuVariableNvModeEnable  | Enables UEFI variable emulation mode. |

###### Table 36 Stage III Driver Configuration
