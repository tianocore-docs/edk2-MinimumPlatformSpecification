<!--- @file
  4.3 Modules

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

## 4.3 Modules

Only modules in the board package should be modified in the process of board
porting. The minimum platform package and other common package contents must
not be directly modified. The board package and silicon package modules may
have multiple instances to support different boards and different silicon.
These components are required. They enable orderly board porting and add the
support for extensibility in later stages. The libraries consumed are the
subset of libraries required by this specification. Some libraries are defined
in this specification, some are defined in EDK II documentation.

### 4.3.1 UEFI Components (DXE)

| `Item`                         | `Producing Package` | `Libraries Consumed`                              |
| ------------------------------ | ------------------- | ------------------------------------------------- |
| DxeIpl.efi                     | MdeModulePkg        |                                                   |
| SiliconPolicyPeiPostMemory.efi | MinPlatformPkg      | SiliconPolicyInitLib<br />SiliconPolicyUpdateLib  |
| PlatformInitPostMemory.efi     | MinPlatformPkg      | BoardInitLib<br />TestPointCheckLib               |
| ResetSystemRuntimeDxe.efi      | MdeModulePkg        | ResetSystemLib                                    |
| PciHostBridge.efi              | MdeModulePkg        | PciHostBridgeLib                                  |

###### Table 17 Stage II DXE UEFI Components

### 4.3.2 Platform Architecture Libraries (PEI)

| `Item`                  | `API Definition Package` | `Producing Package` | `Description`                                                                                   |
| ----------------------- | ------------------------ | ------------------- | ----------------------------------------------------------------------------------------------- |
| BoardInitLib            | MinPlatformPkg           | BoardPkg            | Board initialization library.                                                                   |
| SiliconPolicyInitLib    | IntelSiliconPkg          | SiliconPkg          | Provides default silicon configuration policy data.                                             |
| SiliconPolicyUpdat eLib | IntelSiliconPkg          | BoardPkg            | Provides board updates to silicon configuration policy data.                                    |
| TestPointCheckLib       | MinPlatformPkg           | MinPlatformPkg      | Test point check library. It is called by PlatformInit module to perform stage-specific checks. |
| TestPointLib            | MinPlatformPkg           | MinPlatformPkg      | Test point library. It provides helper functionality for TestPointCheck lib.                    |

###### Table 18 Stage II PEI Platform Architecture Libraries

### 4.3.3. Platform Architecture Libraries (DXE)

Stage II contains some DXE items needed to enable Stage III. No board porting
of these libraries is required. Board integrators should ensure that their
silicon package provides the necessary libraries. These libraries and the UEFI
Components (DXE) are functionally irrelevant to Stage II functionality.

| `Item`           | `API Definition Package` | `Producing Package` | `Description`                       |
| ---------------- | ------------------------ | ------------------- | ----------------------------------- |
| ResetSystemLib   | MdeModulePkg             | SiliconPkg          | For DXE reset architecture protocol |
| PciHostBridgeLib | MdeModulePkg             | SiliconPkg          | For DXE PCI host bridge driver      |

###### Table 19 Stage II DXE Platform Architecture Libraries
