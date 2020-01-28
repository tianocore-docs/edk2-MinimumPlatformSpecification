<!--- @file
  3.2 Firmware Volumes

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

## 3.2 Firmware Volumes

The Stage I functionality is contained in these Firmware Volumes with these
attributes.

| `Name`              | `Content`                          | `Compressed` | `Parent FV` |
| ------------------- | ---------------------------------- | ------------ | ----------- |
| FvPreMemory         | SEC + StatusCode                   | No           | None        |
| FvBspPreMemory      | Pre-memory board initialization    | No           | None        |
| FvFspT              | SEC silicon initialization         | No           | None        |
| FvFspM              | Memory initialization              | No           | None        |
| FvPreMemorySilicon  | Pre-memory silicon initialization  | No           | FvFspM      |
| FvFspS              | Silicon initialization             | No           | None        |
| FvPostMemorySilicon | Post-memory silicon initialization | Yes          | FvFspS      |

###### Table 5 Stage I Firmware Volumes

As the foundational stage for further functionality, Stage I may include
additional content beyond what is strictly required to meet the stage
objective. Typically this will include silicon initialization code that may be
packaged in a variety of mechanisms including varying size binary blobs. In the
layout shown in Table 5, the Intel&reg; FSP solution is shown as an example. In
this case, the FSP binary can be rebased and integrated in one step rather than
distributing the work for the FSP-M and FSP-S rebase unnecessarily across later
stages. Note that a child FV is a FV embedded within the parent FV. The child
FV is identified by a file type of EFI_FV_FILETYPE_FIRMWARE_VOLUME_IMAGE.

Combining the FVs with full set of silicon binary components yields this
example flash map for MMIO storage:

| `Binary` | `FV`              | `Components`                  | `Purpose`                                                                                                                      |
| -------- | ----------------- | ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Stage I  | FvPreMemory.fv    | SecCore.efi                   | <ul><li>Reset Vector</li><li>Passes PEI core the address of FvFspM</li><li>Passes PEI core the debug configuration</li></ul>   |
|          |                   | ReportFvPei.efi               | <ul><li>Installs firmware volumes</li></ul>                                                                                    |
|          |                   | SiliconPolicyPeiPreMemory.efi | <ul><li>Publishes silicon initialization configuration</li></ul>                                                               |
|          |                   | PlatformInitPreMemory.efi     | <ul><li>Performs pre memory initialization   </li></ul>                                                                        |
|          |                   | Additional Components         | <ul><li>Additional pre-memory components required for Stage I boot</li></ul>                                                   |
|          | FvBspPreMemory.fv | Additional Components         | <ul><li>Advanced pre-memory board support components</li></ul>                                                                 |
|          | FvFspT.fv         | PlatformSec.efi               | <ul><li>Initializes T-RAM silicon functionality</li></ul>                                                                      |
|          |                   |                               | <ul><li>Tests T-RAM functionality</li></ul>                                                                                    |
|          |                   | Additional Components         |                                                                                                                                |
|          | FvFspM.fv         | PeiCore.efi                   | <ul><li>PEI services and dispatcher</li></ul>                                                                                  |
|          |                   | PcdPeim.efi                   | <ul><li>PCD service</li></ul>                                                                                                  |
|          |                   | FspPlatform.efi               | <ul><li>Converts UPD to Policy PPI</li></ul>                                                                                   |
|          |                   | FvPreMemorySilicon.fv         |                                                                                                                                |
|          |                   | (child FV)                    |                                                                                                                                |
|          |                   | Additional Components         | <ul><li>Pre-memory silicon initialization components</li></ul>                                                                 |
|          |                   | ReportStatusCodeRouterPei.efi | <ul><li>Provide status code infrastructure</li></ul>                                                                           |
|          |                   | StatusCodeHandlerPei.efi      | <ul><li>Provide status code listeners</li></ul>                                                                                |
|          |                   | Additional Components         |                                                                                                                                |
|          | FvFspS.fv         | FvPostMemorySilicon.fv        |                                                                                                                                |
|          |                   | (child FV)                    |                                                                                                                                |
|          |                   | Additional Components         | <ul><li>Post-memory silicon initialization components</li></ul>                                                                |
|          |                   | Additional components         |                                                                                                                                |

###### Table 6 Stage I FV and Component Layout

Note that many of the components included above do not actually participate in
producing Stage I functionality, and will not be executed when the boot stage
target is set to Stage I. For systems that use non-volatile storage technology
that does not provide memory map capabilities, this layout may be modified
where necessary. However, the firmware execution path must remain scoped to
only perform actions required to achieve the boot stage objective.

See [Appendix: Full FV Map](10_full_maps/101_firmware_volume_layout.md "Full FV Map") for a more complete example Firmware Volume layout.
