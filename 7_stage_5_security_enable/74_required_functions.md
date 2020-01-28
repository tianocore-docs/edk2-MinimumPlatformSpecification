<!--- @file
  7.4 Required Functions

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

## 7.4 Required Functions

The following functions are required to exist and to execute in the given
order. The component that provides the function is not specified because it is
not required by the architecture.

\* In the common EDK II open source code.

The required functions for Stage IV are presented organized by phase and
subsystem (e.g. ACPI, SMM, etc). See Appendix: Full Functions Map for a
complete ordering for all stages.

### 7.4.1 Required PEI functions

| Name                      | Purpose                       |
| ------------------------- | ----------------------------- |
| PeimEntryMA (*)           | Entry point for the TPM2 PEIM |
| IntelVTdPmrInitialize (*) | Entry point for the VT-d PEIM |

###### Table 59 Stage V PEI Functions

\* In the common EDK II open source code.

### 7.4.2 Required DXE functions

| Name                    | Purpose                                                           |
| ----------------------- | ----------------------------------------------------------------- |
| DriverEntry (*)         | Entry point for the TPM2 DXE module                               |
| IntelVTdInitialize(*)   | Entry point for the VT-d DXE module                               |
| UserPhysicalPresent (*) | Indicates whether a physical user is present for UEFI secure boot |
| ProcessTcgPp            | Process the TPM physical presence (PP) request                    |
| ProcessTcgMor           | Process the TPM memory overwrite request (MOR)                    |

###### Table 60 Stage V DXE Functions

\* In the common EDK II open source code.

### 7.4.3 Required SMM functions

| Name                    | Purpose                                        |
| ----------------------- | ---------------------------------------------- |
| InitializeTcgSmm (*)    | Entry point for the TPM2 SMM module            |
| MemoryClearCallback (*) | Callback function for setting the MOR variable |

###### Table 61 Stage V SMM Functions

\* In the common EDK II open source code.

