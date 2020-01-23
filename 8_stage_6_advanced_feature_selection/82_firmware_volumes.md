<!--- @file
  8.2 Firmware Volumes

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

## 8.2 Firmware Volumes

Stage VI enables advanced features. There is a container FV for adding advanced
features:

| `Name`               | `Content`                                                                          | `Compressed` | `Parent FV` |
| -------------------- | ---------------------------------------------------------------------------------- | ------------ | ----------- |
| FvAdvancedPreMemory  | Advanced feature drivers that should be dispatched prior to memory initialization  | No           | None        |
| FvAdvanced           | Advanced feature drivers that should be dispatched after memory initialization     | Yes          | None        |

###### Table 67 Stage VI Firmware Volumes

Which yields this example extension of the flash map for MMIO storage (append to Stage I-Stage V map):

| `Binary` | `FV`                   | `Components`              | `Purpose`                               |
| -------- | ---------------------- | ------------------------- | --------------------------------------- |
| Stage VI | FvAdvancedPreMemory.fv | FeatureStack1.fv          | Feature 1                               |
|          |                        | Additional Feature Stacks | Additional pre-memory advanced features |
|          | FvAdvanced.fv          | FeatureStack1.fv          | Feature 1                               |
|          |                        | FeatureStack2.fv          | Feature 2                               |
|          |                        | FeatureStack3.fv          | Feature 3                               |
|          |                        | Additional Feature Stacks | Additional advanced features            |

The modules that constitute a particular feature are not required to be contained within a single firmware volume and
this might especially be the case in systems with limited flash storage capacity which could be impacted by firmware
volume alignment requirements.

###### Table 68 Stage VI FV and Component Layout

The PEI core will create a FV HOB for each child firmware volume such that each
DXE firmware volume is exposed to the DXE dispatcher.
