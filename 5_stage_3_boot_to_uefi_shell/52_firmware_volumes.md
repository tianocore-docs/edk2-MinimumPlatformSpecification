<!--- @file
  5.2 Firmware Volumes

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

## 5.2 Firmware Volumes

Stage III finalizes silicon and prepares DXE/BDS services. Additional firmware
volumes include:

| `Name`     | `Content`               | `Compressed` | `Parent FV` |
| ---------- | ----------------------- | ------------ | ----------- |
| FvUefiBoot | Common DXE/BDS Services | Yes          | None        |

###### Table 27 Stage III Firmware Volumes

Which yields this example extension of the flash map for MMIO storage (add to Stage I + II map):

| `Binary`  | `FV`          | `Components`                    | `Purpose`                                                     |
| --------- | ------------- | ------------------------------- | ------------------------------------------------------------- |
| Stage III | FvUefiBoot.fv | DxeCore.efi                     | DXE services and dispatcher                                   |
|           |               | PcdDxe.efi                      | Provides PCD services                                         |
|           |               | ReportStatusCodeRouterDxe.efi   | Provides status code infrastructure                           |
|           |               | StatusCodeHandlerRuntimeDxe.efi | Provides status code listeners                                |
|           |               | BdsDxe.efi                      | Provides Boot Device Selection phase                          |
|           |               | CpuDxe.efi                      | Provides processor services                                   |
|           |               | Metronome.efi                   | Provides metronome HW abstraction                             |
|           |               | MonotonicCounterRuntimeDxe.efi  | Provides monotonic counter service                            |
|           |               | PcatRealTimeClockRuntimeDxe.efi | Provides RTC abstraction                                      |
|           |               | WatchdogTimer.efi               | Provides watchdog timer service                               |
|           |               | RuntimeDxe.efi                  | Provides UEFI runtime service functionality                   |
|           |               | HpetTimerDxe.efi                | Provide timer service                                         |
|           |               | EmuVariableRuntimeDxe.efi       | Provides UEFI variable service                                |
|           |               | CapsuleRuntimeDxe.efi           | Provides capsule service                                      |
|           |               | PciBusDxe.efi                   | PCI bus driver                                                |
|           |               | GraphicsOutputDxe.efi           | Provides graphics support                                     |
|           |               | TerminalDxe.efi                 | Provides terminal services                                    |
|           |               | GraphicsConsoleDxe.efi          | Provides graphics console                                     |
|           |               | ConSplitterDxe.efi              | Provides multi console support                                |
|           |               | EnglishDxe.efi                  | Provides Unicode collation services                           |
|           |               | GenericMemoryTestDxe.efi        | Provide memory test                                           |
|           |               | DevicePathDxe.efi               | Provides device path services                                 |
|           |               | DiskIo.efi                      | Provides disk IO services                                     |
|           |               | Partition.efi                   | Provides disk partition services                              |
|           |               | Fat.efi                         | Provides FAT filesystem services                              |
|           |               | Additional Components           | Additional post-memory components required for Stage III boot |

###### Table 28 Stage III FV and Component Layout

See [Appendix: Full FV Map](10_full_maps/101_firmware_volume_layout.md "Full FV Map") for a more complete example Firmware Volume layout.
