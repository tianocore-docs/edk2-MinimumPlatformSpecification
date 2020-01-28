<!--- @file
  4.2 Firmware Volumes

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

## 4.2 Firmware Volumes

Stage II leverages most of the Stage I content. Additional firmware volumes
include:

| `Name`       | `Content`                 | `Compressed` | `Parent FV` |
| ------------ | ------------------------- | ------------ | ----------- |
| FvPostMemory | Post-memory modules       | Yes          | None        |
| FvBsp.fv     | Post-memory board support | Yes          | None        |

###### Table 15 Stage II Firmware Volumes

Which yields this example extension of the flash map for MMIO storage (append
to Stage I map):

| `Binary` | `FV`            | `Components`                   | `Purpose`                                                    |
| -------- | --------------- | ------------------------------ | ------------------------------------------------------------ |
| Stage II | FvPostMemory.fv | ReadOnlyVariable.efi           | Common core variable services                                |
|          |                 | SiliconPolicyPeiPostMemory.efi | Publishes silicon initialization configuration               |
|          |                 | PlatformInitPostMemory.efi     | Performs post memory initialization                          |
|          |                 | DxeIpl.efi                     | Load and invoke DXE                                          |
|          |                 | ResetSystemRuntimeDxe.efi      | Provides reset service                                       |
|          |                 | PciHostBridge.efi              | PCI host bridge driver                                       |
|          |                 | Additional Components          | Additional post-memory components required for Stage II boot |
|          | FvBsp.fv        | Additional Components          | Post-memory board support components                         |

###### Table 16 Stage II FV and Component Layout

See [Appendix: Full FV Map](10_full_maps/101_firmware_volume_layout.md "Full FV Map") for a more complete example Firmware Volume layout.
