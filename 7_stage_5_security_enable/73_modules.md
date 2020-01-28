<!--- @file
  7.3 Modules

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

## 7.3 Modules

Only modules in the board package should be modified in the process of board
porting. The minimum platform package and other common package contents must
not be directly modified. The board package and silicon package modules may
have multiple instances to support different boards and different silicon.
These components are required. They enable orderly board porting and add the
support for extensibility in later stages. The libraries consumed are the
subset of libraries required by this specification. Some libraries are defined
in this specification, some are defined in EDK II documentation.

### 7.3.1 UEFI Components (PEI)

These components are required. They enable orderly board porting and orderly
extensibility to add functionality over time.

The libraries consumed are the subset of libraries required by this
specification. Some libraries are defined in this specification, some are
defined in EDK II documentation.

| `Item`              | `Producing Package` | `Libraries Consumed` |
| ------------------- | ------------------- | -------------------- |
| Tcg2Pei.efi         | SecurityPkg         |                      |
| Tcg2ConfigPei.efi   | SecurityPkg         |                      |
| Tcg2PlatformPei.efi | MinPlatformPkg      |                      |
| IntelVTdPmrPei.efi  | IntelSiliconPkg     |                      |

###### Table 55 Stage V PEI UEFI Components

### 7.3.2 UEFI Components (DXE)

These components are required. They enable orderly board porting and orderly
extensibility to add functionality over time.

The libraries consumed are the subset of libraries required by this
specification. Some libraries are defined in this specification, some are
defined in EDK II documentation.

| `Item`                    | `Producing Package` | `Libraries Consumed` |
| ------------------------- | ------------------- | -------------------- |
| TcgMor.efi                | SecurityPkg         |                      |
| Tcg2Dxe.efi               | SecurityPkg         |                      |
| Tcg2ConfigDxe.efi         | SecurityPkg         |                      |
| Tcg2PlatformDxe.efi       | MinPlatformPkg      |                      |
| VariableSmmRuntimeDxe.efi | MdeModulePkg        |                      |
| SecureBootConfigDxe.efi   | SecurityPkg         |                      |
| SecurityStubDxe.efi       | MdeModulePkg        |                      |
| IntelVTdDxe.efi           |                     |                      |

###### Table 56 Stage V DXE UEFI Components

### 7.3.3 UEFI Components (SMM)

These components are required. They enable orderly board porting and orderly
extensibility to add functionality over time.

The libraries consumed are the subset of libraries required by this
specification. Some libraries are defined in this specification, some are
defined in EDK II documentation.

| `Item`                    | `Producing Package` | `Libraries Consumed` |
| ------------------------- | ------------------- | -------------------- |
| Tcg2Smm.efi               | SecurityPkg         |                      |
| FaultTolerantWriteSmm.efi | MdeModulePkg        |                      |
| VariableSmm.efi           | MdeModulePkg        |                      |

###### Table 57 Stage V SMM UEFI Components

### 7.3.4 Platform Architecture Libraries

Board porting will require creation of libraries identified as produced by the
BoardPkg. Depending on the board, there may be existing libraries that are
sufficient for a board, so it is important to assess the utility of existing
library instances when developing board support.

| `Item` | `API Definition Package` | `Producing Package` | `Description` |
| ------ | ------------------------ | ------------------- | ------------- |
|        |                          |                     |               |

###### Table 58 Stage V Platform Architecture Libraries
