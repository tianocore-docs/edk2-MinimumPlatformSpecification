<!--- @file
  Appendix A.1 Firmware Volume Layout

  Copyright (c) 2019 - 2020, Intel Corporation. All rights reserved.<BR>

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

## A.1 Firmware Volume Layout

This is a logical firmware volume layout by stage.

| `Binary`   | `FV`                     | `Components`                                   | `Purpose`                                                                                                                                      |
| ---------- | ------------------------ | ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `Stage I`  | `FvPreMemory.fv`         | SecCore.efi                                    | <ul><li>Reset Vector</li><li>Passes PEI core the address of FvFspmM</li><li>Passes PEI core the debug configuration</li></ul>                  |
|            |                          | ReportFvPei.efi                                | <ul><li>Installs firmware volumes</li></ul>                                                                                                    |
|            |                          | SiliconPolicyPeiPreMemory.efi                  | <ul><li>Publishes silicon initialization configuration</li></ul>                                                                               |
|            |                          | PlatformInitPreMemory.efi                      | <ul><li>Performs pre memory initialization</li></ul>                                                                                           |
|            |                          | **FvSecurityPreMemory.fv**</br>_(child FV)_    |                                                                                                                                                |
|            |                          | &nbsp;&nbsp;&nbsp;&nbsp;Tcg2Pei.efi            | <ul><li>TPM2 initialization</li></ul>                                                                                                          |
|            |                          | &nbsp;&nbsp;&nbsp;&nbsp;Tcg2ConfigPei.efi      | <ul><li>TPM2 selection</li></ul>                                                                                                               |
|            |                          | &nbsp;&nbsp;&nbsp;&nbsp;Tcg2PlatformPei.efi    | <ul><li>TPM2 platform module</li></ul>                                                                                                         |
|            |                          | &nbsp;&nbsp;&nbsp;&nbsp;_Additional Components_| <ul><li>Additional pre-memory components required for Stage V boot</li></ul>                                                                   |
|            |                          | Additional Components                          | <ul><li>Additional pre-memory components required for Stage I boot</li></ul>                                                                   |
|            | `FvBspPreMemory.fv`      | **FvAdvancedPreMemory.fv**</br>_(child FV)_    |                                                                                                                                                |
|            |                          | &nbsp;&nbsp;&nbsp;&nbsp;_Additional Components_| <ul><li>Advanced feature pre-memory stacks</li></ul>                                                                                           |
|            |                          | Additional Components                          | <ul><li>Additional pre-memory board support components</li></ul>                                                                               |
|            | `FvFspT.fv`              | PlatformSec.efi                                | <ul><li>Initializes T-RAM silicon functionality</li><li>Tests T-RAM functionality</li></ul>                                                    |
|            |                          | Additional Components                          |                                                                                                                                                |
|            | `FvFspM.fv`              | PeiCore.efi                                    | <ul><li>PEI services and dispatcher</li></ul>                                                                                                  |
|            |                          | PcdPeim.efi                                    | <ul><li>PCD service</li></ul>                                                                                                                  |
|            |                          | FspPlatform.efi                                | <ul><li>Converts UPD to Policy PPI</li></ul>                                                                                                   |
|            |                          | **FvPreMemorySilicon.fv**</br>_(child FV)_     |                                                                                                                                                |
|            |                          | &nbsp;&nbsp;&nbsp;&nbsp;_Additional Components_| <ul><li>Pre-memory silicon initialization components</li></ul>                                                                                 |
|            |                          | ReportStatusCodeRouterPei.efi                  | <ul><li>Provide status code infrastructure</li></ul>                                                                                           |
|            |                          | StatusCodeHandlerPei.efi                       | <ul><li>Provide status code listeners</li></ul>                                                                                                |
|            |                          | Additional Components                          |                                                                                                                                                |
|            | `FvFspS.fv`              | **FvPostMemorySilicon.fv**</br>_(child FV)_    |                                                                                                                                                |
|            |                          | &nbsp;&nbsp;&nbsp;&nbsp;_Additional Components_| <ul><li>Post-memory silicon initialization components</li></ul>                                                                                |
|            |                          | Additional components                          |                                                                                                                                                |
| `Binary`   | `FV`                     | `Components`                                   | `Purpose`                                                                                                                                      |
| `Stage II` | `FvPostMemory.fv`        | ReadOnlyVariable.efi                           | <ul><li>Common core variable services</li></ul>                                                                                                |
|            |                          | SiliconPolicyPeiPostMemory.efi                 | <ul><li>Publishes silicon initialization configuration</li></ul>                                                                               |
|            |                          | PlatformInitPostMemory.efi                     | <ul><li>Performs post memory initialization</li></ul>                                                                                          |
|            |                          | DxeIpl.efi                                     | <ul><li>Load and invoke DXE</li></ul>                                                                                                          |
|            |                          | ResetSystemRuntimeDxe.efi                      | <ul><li>Provides reset service</li></ul>                                                                                                       |
|            |                          | PciHostBridge.efi                              | <ul><li>PCI host bridge driver</li></ul>                                                                                                       |
|            |                          | Additional Components                          | <ul><li>Additional post-memory components required for Stage II boot</li></ul>                                                                 |
|            | `FvBsp.fv`               | Additional Components                          | <ul><li>Post-memory board support components</li></ul>                                                                                         |
| `Binary`   | `FV`                     | `Components`                                   | `Purpose`                                                                                                                                      |
| `Stage III`| `FvUefiBoot.fv`          | DxeCore.efi                                    | <ul><li>DXE services and dispatcher</li></ul>                                                                                                  |
|            |                          | PcdDxe.efi                                     | <ul><li>Provides PCD services</li></ul>                                                                                                        |
|            |                          | ReportStatusCodeRouterDxe.efi                  | <ul><li>Provides status code infrastructure</li></ul>                                                                                          |
|            |                          | StatusCodeHandlerRuntimeDxe.efi                | <ul><li>Provides status code listeners</li></ul>                                                                                               |
|            |                          | BdsDxe.efi                                     | <ul><li>Provides Boot Device Selection phase</li></ul>                                                                                         |
|            |                          | CpuDxe.efi                                     | <ul><li>Provides processor services</li></ul>                                                                                                  |
|            |                          | Metronome.efi                                  | <ul><li>Provides metronome HW abstraction</li></ul>                                                                                            |
|            |                          | MonotonicCounterRuntimeDxe.efi                 | <ul><li>Provides monotonic counter service</li></ul>                                                                                           |
|            |                          | PcatRealTimeClockRuntimeDxe.efi                | <ul><li>Provides RTC abstraction</li></ul>                                                                                                     |
|            |                          | WatchdogTimer.efi                              | <ul><li>Provides watchdog timer service</li></ul>                                                                                              |
|            |                          | RuntimeDxe.efi                                 | <ul><li>Provides UEFI runtime service functionality</li></ul>                                                                                  |
|            |                          | Security.efi                                   | <ul><li>Provides security services to core</li></ul>                                                                                           |
|            |                          | HpetTimerDxe.efi                               | <ul><li>Provide timer service</li></ul>                                                                                                        |
|            |                          | EmuVariableRuntimeDxe.efi                      | <ul><li>Provides UEFI variable service</li></ul>                                                                                               |
|            |                          | CapsuleRuntimeDxe.efi                          | <ul><li>Provides capsule service</li></ul>                                                                                                     |
|            |                          | PciBusDxe.efi                                  | <ul><li>PCI bus driver</li></ul>                                                                                                               |
|            |                          | GraphicsOutputDxe.efi                          | <ul><li>Provides graphics support</li></ul>                                                                                                    |
|            |                          | TerminalDxe.efi                                | <ul><li>Provides terminal services</li></ul>                                                                                                   |
|            |                          | GraphicsConsoleDxe.efi                         | <ul><li>Provides graphics console</li></ul>                                                                                                    |
|            |                          | ConSplitterDxe.efi                             | <ul><li>Provides multi console support</li></ul>                                                                                               |
|            |                          | EnglishDxe.efi                                 | <ul><li>Provides Unicode collation services</li></ul>                                                                                          |
|            |                          | MemoryTest.efi                                 | <ul><li>Provide memory test</li></ul>                                                                                                          |
|            |                          | DevicePathDxe.efi                              | <ul><li>Provides device path services</li></ul>                                                                                                |
|            |                          | DiskIo.efi                                     | <ul><li>Provides disk IO services</li></ul>                                                                                                    |
|            |                          | Partition.efi                                  | <ul><li>Provides disk partition services</li></ul>                                                                                             |
|            |                          | Fat.efi                                        | <ul><li>Provides FAT filesystem services</li></ul>                                                                                             |
|            |                          | Additional Components                          | <ul><li>Additional post-memory components required for Stage III boot</li></ul>                                                                |
| `Binary`   | `FV`                     | `Components`                                   | `Purpose`                                                                                                                                      |
| `Stage IV` | `FvOsBoot.fv`            | **FvLateSilicon.fv**<br />_(child FV)_         |                                                                                                                                                |
|            |                          | &nbsp;&nbsp;&nbsp;&nbsp;_Additional Components_| <ul><li>Additional silicon initialization support that is performed late in the boot</li></ul>                                                 |
|            |                          | AcpiTable.efi                                  | <ul><li>Provides common ACPI services</li></ul>                                                                                                |
|            |                          | PlatformAcpi.efi                               | <ul><li>Provides MinPlatform ACPI content</li></ul>                                                                                            |
|            |                          | BoardAcpi.efi                                  | <ul><li>Provides board ACPI content</li></ul>                                                                                                  |
|            |                          | PiSmmIpl.efi                                   | <ul><li>SMM initial loader</li></ul>                                                                                                           |
|            |                          | PiSmmCore.efi                                  | <ul><li>SMM core services</li></ul>                                                                                                            |
|            |                          | ReportStatusCodeRouterSmm.efi                  | <ul><li>SMM status code infrastructure</li></ul>                                                                                               |
|            |                          | StatusCodeHandlerSmm.efi                       | <ul><li>SMM status code handlers</li></ul>                                                                                                     |
|            |                          | PiSmmCpu.efi                                   | <ul><li>SMM CPU services</li></ul>                                                                                                             |
|            |                          | CpuIo2Smm.efi                                  | <ul><li>SMM CPU IO services</li></ul>                                                                                                          |
|            |                          | FaultTolerantWriteSmm.efi                      | <ul><li>SMM fault tolerant write services</li></ul>                                                                                            |
|            |                          | SpiFvbServiceSmm.efi                           | <ul><li>SMM SPI FLASH services</li></ul>                                                                                                       |
|            |                          | Additional Components                          | <ul><li>Additional post-memory components required for Stage IV boot</li></ul>                                                                 |
| `Binary`   | `FV`                     | `Components`                                   | `Purpose`                                                                                                                                      |
| `Stage V`  | `FvSecurity.fv`          | Tcg2Dxe.efi                                    | <ul><li>TPM2 services</li></ul>                                                                                                                |
|            |                          | Tcg2ConfigDxe.efi                              | <ul><li>TPM2 configuration UI</li></ul>                                                                                                        |
|            |                          | Tcg2PlatformDxe.efi                            | <ul><li>TPM2 platform module</li></ul>                                                                                                         |
|            |                          | Tcg2Smm.efi                                    | <ul><li>TPM2 ACPI services</li></ul>                                                                                                           |
|            |                          | TcgMor.efi                                     | <ul><li>TCG Memory Override support</li></ul>                                                                                                  |
|            |                          | IntelVTdPmrPei.efi                             | <ul><li>IOMMU PEI services</li></ul>                                                                                                           |
|            |                          | IntelVTdDxe.efi                                | <ul><li>IOMMU DXE services</li></ul>                                                                                                           |
|            |                          | SecurityStubDxe.efi                            | <ul><li>Provide security architecture protocol.</li></ul>                                                                                      |
|            |                          | FaultTolerantWriteSmm.efi                      | <ul><li>Fault-tolerant services in SMM.</li></ul>                                                                                              |
|            |                          | VariableSmm.efi                                | <ul><li>Provide Variable service in SMM.</li></ul>                                                                                             |
|            |                          | VariableSmmRuntimeDxe.efi                      | <ul><li>Provide Variable service in UEFI.</li></ul>                                                                                            |
|            |                          | SecureBootConfigDxe.efi                        | <ul><li>SecureBoot configuration UI.</li></ul>                                                                                                 |
|            |                          | Additional Components                          | <ul><li>Additional post-memory components required for Stage V boot</li></ul>                                                                  |
| `Binary`   | `FV`                     | `Components`                                   | `Purpose`                                                                                                                                      |
| `Stage VI` | `FvAdvancedPreMemory.fv` | **FeatureStack1.fv** (child FV)                | <ul><li>Feature 1</li></ul>                                                                                                                    |
|            |                          | **FeatureStack2.fv** (child FV)                | <ul><li>Feature 2</li></ul>                                                                                                                    |
|            | `FvAdvanced.fv`          | **FeatureStack1.fv** (child FV)                | <ul><li>Feature 1</li></ul>                                                                                                                    |
|            |                          | **FeatureStack2.fv** (child FV)                | <ul><li>Feature 2</li></ul>                                                                                                                    |
|            |                          | **FeatureStack3.fv** (child FV)                | <ul><li>Feature 3</li></ul>                                                                                                                    |
|            |                          | Additional Feature Stacks                      | <ul><li>Features</li></ul>                                                                                                                     |

###### Table 71 Full Firmware Volume Layout
