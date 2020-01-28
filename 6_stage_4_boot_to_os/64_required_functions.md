<!--- @file
  6.4 Required Functions

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

## 6.4 Required Functions

The following functions are required to exist and to execute in the given
order. The component that provides the function is not specified because it is
not required by the architecture.

The required functions for Stage IV are organized by phase and subsystem (e.g.
ACPI, SMM, etc). See Appendix: Full Functions Map for a complete ordering for
all stages.

### 6.4.1 Required DXE Functions

| `Name`                                | `Purpose`                                                    |
| ------------------------------------- | ------------------------------------------------------------ |
| PlatformCreateAcpiTable               | Create the minimum set of platform-specific ACPI tables      |
| PlatformUpdateAcpiTable               | Update data in platform-specific in ACPI tables              |
| PlatformInstallAcpiTable              | Install platform-specific ACPI tables                        |
| CoreExitBootServices (*)              | Dismantles UEFI boot services and enter UEFI run time        |
| BoardInitEndOfFirmware                | Board hook for the ExitBootServices event                    |
| TestPointExitBootServices             | Test to verify state after ExitBootServices has been invoked |
| RuntimeDriverSetVirtualAddressMap (*) | Sets virtual address mode                                    |

###### Table 45 Stage IV DXE Functions

\* In the common EDK II open source code.

### 6.4.2 DXE Interfaces

| `Component`  | `Name`                | `Consumer` | `Purpose`                                       |
| ------------ | --------------------- | ---------- | ----------------------------------------------- |
| BoardInitLib | BoardNotificationInit | Platform   | Board specific initialization hook at DXE phase |

###### Table 46 Stage IV DXE Interfaces

### 6.4.3 Required SMM Functions

| `Name`                     | `Purpose`                         |
| -------------------------- | --------------------------------- |
| SmmIplEntry (*)            | SMM IPL                           |
| SmmMain (*)                | SMM Core entry point              |
| PiCpuSmmEntry (*)          | SMM CPU driver                    |
| SmmRelocateBases (*)       | Relocation                        |
| _SmiEntryPoint (*)         | SMI entry point                   |
| SmmEntryPoint (*)          | Dispatch SMI handlers             |
| PchSmmCoreDispatcher       | Dispatch PCH child SMI handlers   |
| TestPointSmmEndOfDxe       | Verify state after SmmEndOfDxe    |
| TestPointSmmEndOfDxe       | Verify state after SmmEndOfDxe    |
| TestPointSmmReadyToLock    | Verify state after SmmReadyToLock |
| PlatformEnableAcpiCallback | Switch the system to ACPI mode    |
| BoardEnableAcpiCallback    | Board hook for ACPI mode switch   |

###### Table 47 Stage IV SMM Functions

\* In the common EDK II open source code.

### 6.4.4 SMM Interfaces

| `Component`  | `Name`                    | `Consumer` | `Purpose`                               |
| ------------ | ------------------------- | ---------- | --------------------------------------- |
| BoardAcpiLib | BoardEnableEcAcpiMode ()  | Platform   | Board specific ENABLE_ACPI_MODE action  |
|              | BoardDisableEcAcpiMode () | Platform   | Board specific DISABLE_ACPI_MODE action |

###### Table 48 Stage IV SMM Interfaces
