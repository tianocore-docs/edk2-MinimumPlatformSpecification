<!--- @file
  7.2 Firmware Volumes

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

## 7.2 Firmware Volumes

Stage V supports key security features. Additional FV are:

| `Name`     | `Content`                | `Compressed` | `Parent FV` |
| ---------- | ------------------------ | ------------ | ----------- |
| FvSecurity | Security related modules | No           | None        |
| NvStorage  | Real NV storage on flash | No           | None        |

###### Table 53 Stage V Firmware Volumes

Which yields this example extension of the flash map for MMIO storage (add to Stage I - IV map):

| `Binary` | `FV`          | `Components`              | `Purpose`                                                   |
| -------- | ------------- | ------------------------- | ----------------------------------------------------------- |
| Stage V  | FvSecurity.fv | Tcg2Dxe.efi               | TPM2 services                                               |
|          |               | Tcg2ConfigDxe.efi         | TPM2 configuration UI.                                      |
|          |               | Tcg2PlatformDxe.efi       | TPM2 platform module.                                       |
|          |               | Tcg2Smm.efi               | TPM2 ACPI services.                                         |
|          |               | TcgMor.efi                | TCG Memory Override support                                 |
|          |               | IntelVTdPmrPei.efi        | IOMMU PEI services.                                         |
|          |               | IntelVTdDxe.efi           | IOMMU DXE services.                                         |
|          |               | SecurityStubDxe.efi       | Provide security architecture protocol.                     |
|          |               | FaultTolerantWriteSmm.efi | Fault-tolerant services in SMM.                             |
|          |               | VariableSmm.efi           | Provide Variable service in SMM.                            |
|          |               | VariableSmmRuntimeDxe.efi | Provide Variable service in UEFI.                           |
|          |               | SecureBootConfigDxe.efi   | SecureBoot configuration UI.                                |
|          |               | Additional Components     | Additional post-memory components required for Stage V boot |

###### Table 54 Stage V FV and Components Layout

See [Appendix: Full FV Map](10_full_maps/101_firmware_volume_layout.md "Full FV Map") for a more complete example Firmware Volume layout.
