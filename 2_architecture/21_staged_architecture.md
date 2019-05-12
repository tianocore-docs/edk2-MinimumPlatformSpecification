<!--- @file
  2.1 Staged Architecture

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

## 2.1 Staged Architecture

The Minimum Platform Architecture defines a number of stages that are integral
to the design and implementation of conformant firmware solutions. Stages
define what code needs to be built, what functionality is required, what binary
components are required at the FV and UEFI PI Architecture executables level,
and what the system capabilities are available as a result of successfully
executing through a firmware stage.

| `Stage` | `Functional Objective`     | `Example Capabilities`                                                                                                                                                             |
| ------- | -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `I`     | Minimal Debug              | Serial Port, Port 80, External debuggers Optional: Software debugger                                                                                                               |
| `II`    | Memory Functional          | Basic hardware initialization including main memory                                                                                                                                |
| `III`   | Boot to UEFI Shell         | Generic DXE driver execution                                                                                                                                                       |
| `IV`    | Boot to OS                 | Boot a general purpose operating system with the minimally required feature set. Publish a minimal set of ACPI tables.                                                             |
| `V`     | Security Enabled           | UEFI Secure Boot, TCG trusted boot, DMA protection, etc.                                                                                                                           |
| `VI`    | Advanced Feature Selection | Firmware update, power management, networking support, manageability, testability, reliability, availability, serviceability, non-essential provisioning and resiliency mechanisms |
| `VII`   | Tuning                     | Size and performance optimizations                                                                                                                                                 |

###### Table 4 Architecture Stages

The stages correspond well to bootstrapping a system and to developing a
production-worthy solution. The stages are defined in order to detail the
minimum items required. It is expected that there will be more required and
more present than what is defined in this specification for an end product. The
stages capture what is minimally required to support the strategic objectives
of transparency and quality as well as the more tactical objectives of
structure, consistency, cohesion, coupling, and compatibility. Note that the
stages represent enabling steps, not necessarily the order of execution. For
example, ACPI initialization necessary in Stage IV may be performed before
Stage III would be considered complete. Further, the stages may not necessarily
be strictly additive once enabling is complete. For example, the UEFI shell may
not be required in the production firmware image based on product requirements,
but it must have been enabled and therefore capable of being loaded in the
final firmware if chosen by a firmware engineer supporting the firmware in the
final production image.
