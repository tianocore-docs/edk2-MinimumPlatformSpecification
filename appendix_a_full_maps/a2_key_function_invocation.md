<!--- @file
  Appendix A.2 Key Function Invocation

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

## A.2 Key Function Invocation

| Name                                                   | Purpose                                                    |
| ------------------------------------------------------ | ---------------------------------------------------------- |
| ResetHandler (*)                                       | The reset vector invoked by silicon                        |
| TempRamInit                                            | Silicon initializes temporary memory                       |
| TestPointTempMemoryFunction                            | Test temporary memory functionality                        |
| SecStartup (*)                                         | First C code execution, constructs PEI input               |
| TestPointEndOfSec                                      | Verify state before switching to PEI                       |
| PeiCore (*)                                            | PEI entry point                                            |
| PeiDispatcher (*)                                      | Calls the entry points of PEIM                             |
| ReportPreMemFv                                         | Installs firmware volumes required in pre-memory           |
| BoardDetect                                            | Board detection of the motherboard type                    |
| BoardDebugInit                                         | Board specific initialization for debug device             |
| PlatformHookSerialPortInitialize                       | Board serial port initialization. Called from SEC or PEI   |
| TestPointDebugInitDone                                 | Verify debug functionality                                 |
| BoardBootModeDetect                                    | Board hook for EFI_BOOT_MODE detection                     |
| BoardInitBeforeMemoryInit                              | Board specific initialization, e.g. GPIO                   |
| SiliconPolicyInitPreMemory                             | Silicon pre memory policy initialization                   |
| SiliconPolicyUpdatePreMemory                           | Board updates silicon policies                             |
| SiliconPolicyDonePreMemory                             | Complete pre memory silicon policy data collection         |
| MemoryInit                                             | Silicon initializes permanent memory                       |
| InstallEfiMemory                                       | Install permantent memory to core                          |
| PeiCore (*)                                            | PEI entry point (post memory entry)                        |
| SecTemporaryRamDone (*)                                | Call SEC to tear down temporary memory                     |
| ReportPostMemFv                                        | Installs firmware volumes required in post-memory          |
| TestPointPostMemoryFvInfoFunctional                    | Test for Firmware Volume map                               |
| BoardInitAfterMemoryInit                               | Board initialization after memory is installed             |
| SetCacheMtrr                                           | Configure cache map for permanent memory                   |
| TestPointPostMemoryMtrrAfterMemoryDiscoveredFunctional | Test post-memory cache map                                 |
| TestPointPostMemoryResourceFunctional                  | Test resources                                             |
| TestPointPostMemoryFvInfoFunctional                    | Test for Firmware Volume map                               |
| BoardInitBeforeSiliconInit                             | Board initialization hook                                  |
| SiliconPolicyInitPostMemory                            | Silicon post memory policy initialization                  |
| SiliconPolicyUpdatePostMemory                          | Board updates silicon policies                             |
| SiliconPolicyDonePostMemory                            | Complete post memory silicon policy data collection        |
| BoardInitAfterSiliconInit                              | Board specific initialization after silicon is initialized |
| DxeLoadCore (*)                                        | DXE IPL locate and call DXE Core                           |
| SetCacheMtrrAfterEndOfPei                              | Sets cache map in preparation for DXE                      |
| TestPointEndOfPei                                      | Verify expected state as we exit PEI phase                 |
| TestPointPostMemoryMtrrEndOfPeiFunctional              | Basic test for cache configuration before entering DXE     |
| PeimEntryMA (*)                                        | Entrypoint for TPM2 PEIM                                   |
| IntelVTdPmrInitialize (*)                              | Entrypoint for VT-d PEIM                                   |
| DxeMain (*)                                            | DXE entry point                                            |
| CoreStartImage (*)                                     | Calls the entry points of DXE drivers                      |
| SiliconPolicyInitLate                                  | Silicon late policy initialization                         |
| SiliconPolicyUpdateLate                                | Board updates silicon policies                             |
| SiliconPolicyDoneLate                                  | Complete late silicon policy data collection               |
| CoreAllEfiServicesAvailable (*)                        | Check if required architectural protocols are installed    |
| SmmIplEntry (*)                                        | SMM IPL                                                    |
| SmmMain (*)                                            | SMM Core entrypoint                                        |
| PiCpuSmmEntry (*)                                      | SMM CPU driver                                             |
| SmmRelocateBases (*)                                   | Relocation                                                 |
| _SmiEntryPoint (*)                                     | SMI entry point                                            |
| SmmEntryPoint (*)                                      | Dispatch SMI handlers                                      |
| PchSmmCoreDispatcher                                   | Dispatch PCH child SMI handlers                            |
| InitializeTcgSmm (*)                                   | Entrypoint for TPM2 SMM                                    |
| MemoryClearCallback (*)                                | Callback function for MOR setting                          |
| PlatformCreateAcpiTable                                | Create the minimum set of platform specific tables         |
| PlatformUpdateAcpiTable                                | Update platform specific data in ACPI tables - FADT.       |
| PlatformInstallAcpiTable                               | Install platform specific ACPI tables                      |
| DriverEntry (*)                                        | Entrypoint for TPM2 DXE                                    |
| IntelVTdInitialize(*)                                  | Entrypoint for VT-d DXE                                    |
| UserPhysicalPresent (*)                                | Return if physical user is present for UEFI secure boot    |
| ProcessTcgPp                                           | Process TPM PP request                                     |
| ProcessTcgMor                                          | Process TPM MOR request                                    |
| BdsEntry (*)                                           | BDS entry point                                            |
| PlatformBootManagerBeforeConsole (*)                   | Platform specific BDS functionality before console         |
| BoardInitAfterPciEnumeration                           | Board-specific hook on PCI enumeration completion          |
| TestPointPciEnumerationDone                            | Verify PCI                                                 |
| ExitPmAuth                                             | Signal key security events EndOfDxe and SmmReadyToLock     |
| TestPointEndOfDxe                                      | Verify expected state after EndOfDxe                       |
| TestPointDxeSmmReadyToLock                             | Verify expected state after SmmReadyToLock                 |
| TestPointSmmEndOfDxe                                   | Verify state after SmmEndOfDxe                             |
| TestPointSmmEndOfDxe                                   | Verify state after SmmEndOfDxe                             |
| TestPointSmmReadyToLock                                | Verify state after SmmReadyToLock                          |
| EfiBootManagerDispatchDeferredImages (*)               | Dispatch deferred third party UEFI driver OPROMs           |
| PlatformBootManagerAfterConsole (*)                    | Platform specific BDS functionality after console          |
| BootBootOptions (*)                                    | Attempt each boot option                                   |
| EfiSignalEventReadyToBoot (*)                          | Signals the ReadyToBoot event group                        |
| BoardInitReadyToBoot                                   | Board hook on ReadyToBoot event                            |
| TestPointReadyToBoot                                   | Verify state after ReadyToBoot event signal                |
| UefiMain (*)                                           | UEFI Shell entry point                                     |
| CoreExitBootServices (*)                               | Dismantles UEFI boot services and enters runtime           |
| BoardInitEndOfFirmware                                 | Board hook for ExitBootServices event                      |
| TestPointExitBootServices                              | Verify state after ExitBootServices has been called        |
| RuntimeDriverSetVirtualAddressMap (*)                  | Set virtual address mode                                   |
| PlatformEnableAcpiCallback                             | Switch the system to ACPI mode                             |
| BoardEnableAcpiCallback                                | Board hook for ACPI mode switch                            |

###### Table 72 Key Function Invocation

\* In the common EDK II open source code.
