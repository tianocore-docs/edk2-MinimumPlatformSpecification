<!--- @file
  5.3 Modules

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

## 5.3 Modules

Only modules in the board package should be modified in the process of board
porting. The minimum platform package and other common package contents must
not be directly modified. The board package and silicon package modules may
have multiple instances to support different boards and different silicon.
These components are required. They enable orderly board porting and add the
support for extensibility in later stages. The libraries consumed are the
subset of libraries required by this specification. Some libraries are defined
in this specification, some are defined in EDK II documentation.

### 5.3.1 UEFI Components (DXE)

| `Item`                          | `Producing Package` | `Libraries Consumed`   | `Comments`            |
| ------------------------------- | ------------------- | ---------------------- | --------------------- |
| DxeCore.efi                     | MdeModulePkg        |                        |                       |
| PcdDxe.efi                      | MdeModulePkg        |                        |                       |
| BdsDxe.efi                      | MdeModulePkg        | PlatformBootManagerLib |                       |
| CpuDxe.efi                      | UefiCpuPkg          |                        | Architecture Protocol |
| Metronome.efi                   | MdeModulePkg        |                        | Architecture Protocol |
| MonotonicCounterRuntimeDxe.efi  | MdeModulePkg        |                        | Architecture Protocol |
| PcatRealTimeClockRuntimeDxe.efi | PcAtChipsetPkg      |                        | Architecture Protocol |
| WatchdogTimer.efi               | MdeModulePkg        |                        | Architecture Protocol |
| RuntimeDxe.efi                  | MdeModulePkg        |                        | Architecture Protocol |
| SecurityStubDxe.efi             | SecurityPkg         |                        | Architecture Protocol |
| HpetTimerDxe.efi (*)            | PcAtChipsetPkg      |                        | Architecture Protocol |
| VariableRuntimeDxe.efi /        | MdeModulePkg        |                        | Architecture Protocol |
| VariableSmmRuntimeDxe.efi       |                     |                        |                       |
| CapsuleRuntimeDxe.efi           | MdeModulePkg        |                        | Architecture Protocol |
| PciBusDxe.efi                   | MdeModulePkg        |                        | PCI                   |
| TerminalDxe.efi                 | MdeModulePkg        |                        | Terminal              |
| ConSplitterDxe.efi              | MdeModulePkg        |                        | Console               |
| EnglishDxe.efi                  | MdeModulePkg        |                        | Localization          |
| DevicePathDxe.efi               | MdeModulePkg        |                        | Other                 |
| `Optional drivers`              |                     |                        |                       |
| GraphicsOutputDxe.efi           | MdeModulePkg        |                        | Graphics              |
| GraphicsConsoleDxe.efi          | MdeModulePkg        |                        | Console               |
| MemoryTest.efi                  | MdeModulePkg        |                        | Other                 |
| ReportStatusCodeRouterDxe.efi   | MdeModulePkg        |                        | Status code           |
| StatusCodeHandlerRuntimeDxe.efi | MdeModulePkg        | SerialPortLib          | Status code           |

###### Table 29 Stage III DXE UEFI Components

\* An alternative timer module may be used to produce an instance of gEfiTimerArchProtocolGuid.

### 5.3.2 Platform Architecture Libraries

No board porting of these libraries is required.

| `Item`                  | `API Definition Package` | `Producing Package` | `Description`                                      |
| ----------------------- | ------------------------ | ------------------- | -------------------------------------------------- |
| SerialPortLib           | MdeModulePkg             | MinPlatformPkg      | Serial port leveraging PEI and HOB initialization. |
| PlatformBoot ManagerLib | MdeModulePkg             | MinPlatformPkg      | Basic platform boot manager port.                  |

###### Table 30 Stage III Platform Architecture Libraries
