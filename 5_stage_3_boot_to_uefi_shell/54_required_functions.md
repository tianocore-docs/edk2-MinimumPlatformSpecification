<!--- @file
  5.4 Required Functions

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

## 5.4 Required Functions

The following functions are required to exist and to execute in the listed
order. The component that provides the function is not specified because it is
not required by the architecture.

### 5.4.1 Required PEI functions

| `Name`                                    | `Purpose`                                                  |
| ----------------------------------------- | ---------------------------------------------------------- |
| BoardInitBeforeSiliconInit                | Board initialization hook                                  |
| SiliconPolicyInitPostMemory               | Silicon post memory policy initialization                  |
| SiliconPolicyUpdatePostMemory             | Board updates silicon policies                             |
| SiliconPolicyDonePostMemory               | Complete post memory silicon policy data collection        |
| BoardInitAfterSiliconInit                 | Board specific initialization after silicon is initialized |
| DxeLoadCore (*)                           | DXE IPL locate and call DXE Core                           |
| SetCacheMtrrAfterEndOfPei                 | Sets cache map in preparation for DXE                      |
| TestPointEndOfPei                         | Verify expected state as we exit PEI phase                 |
| TestPointPostMemoryMtrrEndOfPeiFunctional | Basic test for cache configuration before entering DXE     |

###### Table 31 Stage III Required PEI Functions

\* In the common EDK II open source code.

### 5.4.2 PEI Interfaces

| `Component`            | `Name`                        | `Consumer` | `Purpose`                                                   |
| ---------------------- | ----------------------------- | ---------- | ----------------------------------------------------------- |
| BoardInitLib           | BoardInitBeforeSiliconInit    | Platform   | Board specific initialization before silicon initialization |
|                        | BoardInitAfterSiliconInit     | Platform   | Board specific initialization after silicon initialization  |
| SiliconPolicyInitLib   | SiliconPolicyInitPostMemory   | Platform   | Silicon provides default policy                             |
|                        | SiliconPolicyDonePostMemory   | Platform   | Platform to indicate the policy update is done              |
|                        | SiliconGetPolicySubData       | Board      | Return policy data for update.                              |
| SiliconPolicyUpdateLib | SiliconPolicyUpdatePostMemory | Platform   | Board updates default policy                                |

###### Table 32 Stage III PEI Functions

### 5.4.3 Required DXE functions

| `Name`                                   | `Purpose`                                                          |
| ---------------------------------------- | ------------------------------------------------------------------ |
| DxeMain (*)                              | DXE entry point                                                    |
| CoreStartImage (*)                       | DXE driver entry point                                             |
| SiliconPolicyInitLate                    | Silicon policy late (DXE) initialization                           |
| SiliconPolicyUpdateLate                  | Silicon policy late (DXE) update from the board package            |
| SiliconPolicyDoneLate                    | Silicon policy late (DXE) indication policy initialization is done |
| CoreAllEfiServicesAvailable (*)          | Verify all architectural protocols are installed                   |
| BdsEntry (*)                             | BDS entry point                                                    |
| PlatformBootManagerBeforeConsole (*)     | Platform-specific BDS functionality before console                 |
| BoardInitAfterPciEnumeration             | Board-specific hook after PCI enumeration completion               |
| TestPointPciEnumerationDone              | Test to verify PCI enumeration assignment                          |
| ExitPmAuth                               | Signal key security events EndOfDxe and SmmReadyToLock             |
| TestPointEndOfDxe                        | Test to verify expected state after EndOfDxe                       |
| TestPointDxeSmmReadyToLock               | Test to verify expected state after SmmReadyToLock                 |
| EfiBootManagerDispatchDeferredImages (*) | Dispatch deferred third party UEFI driver OPROMs                   |
| PlatformBootManagerAfterConsole (*)      | Platform specific BDS functionality after console                  |
| BootBootOptions (*)                      | Attempt each boot option                                           |
| EfiSignalEventReadyToBoot (*)            | Signals the ReadyToBoot event group                                |
| BoardInitReadyToBoot                     | Board hook on ReadyToBoot event                                    |
| TestPointReadyToBoot                     | Test to verify expected state after ReadyToBoot event signal       |
| UefiMain (*)                             | UEFI Shell entry point                                             |

###### Table 33 Stage III DXE Functions

### 5.4.4 DXE Interfaces

| `Component`  | `Name`                | `Consumer` | `Purpose`                                       |
| ------------ | --------------------- | ---------- | ----------------------------------------------- |
| BoardInitLib | BoardNotificationInit | Platform   | Board specific initialization hook at DXE phase |

###### Table 34 Stage III DXE Interfaces
