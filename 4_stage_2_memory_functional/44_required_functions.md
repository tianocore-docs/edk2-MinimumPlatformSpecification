<!--- @file
  4.4 Required Functions

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

## 4.4 Required Functions

The following functions are required to exist and to execute in the listed
order. The component that provides the function is not specified because it is
not required by the architecture.

### 4.4.1 Required PEI functions

\* In the common EDK II open source code.

| `Name`                                                 | `Purpose`                                                                                        |
| ------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| BoardBootModeDetect                                    | Board hook for EFI_BOOT_MODE detection                                                           |
| BoardInitBeforeMemoryInit                              | Board specific initialization prior to permanent memory initialization (e.g. GPIO configuration) |
| SiliconPolicyInitPreMemory                             | Pre-memory silicon policy default initialization                                                 |
| SiliconPolicyUpdatePreMemory                           | Pre-memory silicon policy update logic                                                           |
| SiliconPolicyDonePreMemory                             | Opportunity to implement a board-specific indicator that silicon policy initialization is done   |
| MemoryInit                                             | Permanent memory initialization                                                                  |
| InstallEfiMemory                                       | Install permanent memory to core                                                                 |
| PeiCore (*)                                            | PEI entry point (post-memory entry)                                                              |
| SecTemporaryRamDone (*)                                | Optional API defined in the PI specification to disabled temporary RAM                           |
| ReportPostMemFv                                        | Firmware volume installation in post-memory                                                      |
| TestPointPostMemoryFvInfoFunctional                    | Test to verify correctness of the firmware volume map in post-memory                             |
| BoardInitAfterMemoryInit                               | Board initialization after memory is installed                                                   |
| SetCacheMtrr                                           | Configuration of MTRR settings for post-memory                                                   |
| TestPointPostMemoryMtrrAfterMemoryDiscoveredFunctional | Test to verify the correctness of the MTRR settings in post-memory                               |
| TestPointPostMemoryResourceFunctional                  | Test to verify correctness of permanent memory                                                   |

###### Table 20 Stage II PEI Functions

### 4.4.2 Interfaces

\* In the common EDK II open source code.

| `Component`             | `Name`                       | `Consumer` | `Purpose`                                                        |
| ----------------------- | ---------------------------- | ---------- | ---------------------------------------------------------------- |
| BoardInitLib            | BoardBootModeDetect          | Platform   | Board-specific boot mode detection                               |
|                         | BoardInitAfterMemoryInit     | Platform   | Board specific initialization after memory initialization        |
|                         | BoardInitBeforeTempRamExit   | Platform   | Board specific hook before temporary RAM exit                    |
|                         | BoardInitAfterTempRamExit    | Platform   | Board specific hook after temporary RAM exit                     |
| SiliconPolicyInitLib    | SiliconPolicyInitPreMemory   | Platform   | Initialize silicon policy default values                         |
|                         | SiliconPolicyDonePreMemory   | Platform   | Platform-specific behavior to indicate the policy update is done |
| SiliconPolicyUpdateLib  | SiliconPolicyUpdatePreMemory | Platform   | Board updates default policy                                     |

###### Table 21 Stage II Interfaces
