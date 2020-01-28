<!--- @file
  6.2 Firmware Volumes

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

## 6.2 Firmware Volumes

Stage IV finalizes silicon initialization, adds basic operating system required
interfaces, and supports minimally featured operating system boot. The new
components are support in a dedicated firmware volume.

| `Name`        | `Content`                    | `Compressed` | `Parent FV` |
| ------------- | ---------------------------- | ------------ | ----------- |
| FvOsBoot      | DXE/BDS Services             | Yes          | None        |
| FvLateSilicon | ACPI and SMM silicon support | No           | FvOsBoot    |

###### Table 39 Stage IV Firmware Volumes

Which yields this example extension of the flash map for MMIO storage (add to
Stage I + II + III map):

| `Binary` | `FV`        | `Components`                  | `Purpose`                                                                    |
| -------- | ----------- | ----------------------------- | ---------------------------------------------------------------------------- |
| Stage IV | FvOsBoot.fv | FvLateSilicon.fv (child FV)   |                                                                              |
|          |             | Additional Components         | Additional silicon initialization support that is performed late in the boot |
|          |             | AcpiTable.efi                 | Provides common ACPI services                                                |
|          |             | PlatformAcpi.efi              | Provides MinPlatform ACPI content                                            |
|          |             | BoardAcpi.efi                 | Provides board ACPI content                                                  |
|          |             | PiSmmIpl.efi                  | SMM initial loader                                                           |
|          |             | PiSmmCore.efi                 | SMM core services                                                            |
|          |             | ReportStatusCodeRouterSmm.efi | SMM status code infrastructure                                               |
|          |             | StatusCodeHandlerSmm.efi      | SMM status code handlers                                                     |
|          |             | PiSmmCpu.efi                  | SMM CPU services                                                             |
|          |             | CpuIo2Smm.efi                 | SMM CPU IO services                                                          |
|          |             | FaultTolerantWriteSmm.efi     | SMM fault tolerant write services                                            |
|          |             | SpiFvbServiceSmm.efi          | SMM SPI FLASH services                                                       |
|          |             | Additional Components         | Additional post-memory components required for Stage IV boot                 |

###### Table 40 Stage IV FV and Component Layout

See [Appendix: Full FV Map](10_full_maps/101_firmware_volume_layout.md "Full FV Map") for a more complete example Firmware Volume layout.
