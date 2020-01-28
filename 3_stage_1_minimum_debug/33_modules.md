<!--- @file
  3.3 Modules

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

## 3.3 Modules

The architecture requires the following modules. Only modules found in the
BoardPkg should be modified for board porting. MinPlatformPkg and other common
package contents must not be directly modified. BoardPkg and SiliconPkg modules
will have multiple instances to support different boards and different silicon.

### 3.3.1 UEFI Components

These components are required. They enable orderly board porting and add the
support for extensibility in later stages. The libraries consumed are the
subset of libraries required by this specification. Some libraries are defined
in this specification, and some are defined in EDK II documentation.

| `Item`                        | `Producing Package` | `Libraries Consumed`            |
| ----------------------------- | ------------------- | ------------------------------- |
| SecCore.efi                   | UefiCpuPkg          | PlatformSecLib, SerialPortLib   |
| PeiCore.efi                   | MdeModulePkg        |                                 |
| PcdPeim.efi                   | MdeModulePkg        |                                 |
| ReportStatusCodeRouterPei.efi | MdeModulePkg        |                                 |
| StatusCodeHandlerPei.efi      | MdeModulePkg        | SerialPortLib                   |
| ReportFvPei.efi               | MinPlatformPkg      | ReportFvLib, TestPointCheckLib  |
| SiliconPolicyPeiPreMemory.efi | MinPlatformPkg      | SiliconPolicyInitLib,           |
|                               |                     | SiliconPolicyUpdateLib          |
| PlatformInitPreMemory.efi     | MinPlatformPkg      | BoardInitLib, TestPointCheckLib |

###### Table 7 Stage I UEFI Components Platform Architecture Libraries

### 3.3.2 Platform Architecture Libraries

Board porting will require creation of libraries identified as produced by the
BoardPkg. Depending on the board, there may be existing libraries that are
sufficient for a board, so it is important to assess the utility of existing
library instances when developing board support.

| `Item`                 | `API Definition Package` | `Producing Package` | `Description`                                                                                   |
| ---------------------- | ------------------------ | ------------------- | ----------------------------------------------------------------------------------------------- |
| BoardInitLib           | MinPlatformPkg           | BoardPkg            | Board initialization library.                                                                   |
| ReportFvLib            | MinPlatformPkg           | MinPlatformPkg      | Installs platform firmware volumes.                                                             |
| SerialPortLib          | MdeModulePkg             | BoardPkg            | SIO vendor specific initialization to enable serial port.                                       |
| SiliconPolicyInitLib   | IntelSiliconPkg          | SiliconPkg          | Provides default silicon configuration policy data.                                             |
| SiliconPolicyUpdateLib | IntelSiliconPkg          | BoardPkg            | Provides board updates to silicon configuration policy data.                                    |
| PlatformSecLib         | UefiCpuPkg               | MinPlatformPkg      | Reset vector and SEC initialization code.                                                       |
| TestPointCheckLib      | MinPlatformPkg           | MinPlatformPkg      | Test point check library. It is called by PlatformInit module to perform stage-specific checks. |
| TestPointLib           | MinPlatformPkg           | MinPlatformPkg      | Test point library. It provides helper functionality for TestPointCheck lib.                    |

###### Table 8 Stage I Libraries
