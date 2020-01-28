<!--- @file
  7 Stage V: Security Enable

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

## 7.1 Overview

The objective of Stage V is to establish the basic system security foundation
for a production environment. Given the importance of security for all
connected systems, the platform architecture considers the following basic
security features as minimum requirements for any product and thus an important
part of the effort to produce a minimal platform. This stage is concerned with
enabling security technologies described in industry specifications.
Lower-level chipset-specific security technologies such as register locks may
exist and those should be enabled during standard silicon initialization flows
in earlier stages.

### 7.1.1 Major Execution Activities

| `Stage V Modules`                                                                    |
| ------------------------------------------------------------------------------------ |
| Full UEFI variable services support (i.e. non-volatile, volatile, and authenticated) |
| Authenticated boot (HW and UEFI)                                                     |
| TCG trusted boot (if TPM HW is present)                                              |
| DMA protection                                                                       |

### 7.1.2 Main Control Flow

Stage V introduces new modules and requirements to the boot incrementally over
Stage IV. The key requirement is to satisfy industry standard security
specifications applicable to the platform. The security technologies enabled in
this stage are not strictly bound to the definition in this specification and
may consist of a subset or superset of the content described in this section.
However, the only case in which a modern production system should not implement
a form of any of these technologies is if the necessary hardware is not
available. In all other cases, the system must at least implement a form of the
following:

* Hardware rooted authenticated boot that can establish a Static Root of Trust
  for Verification (S-RTV) and continue an authenticated chain of verification
  throughout the boot process.

* System measurement capability that allows the firmware to serve as a Static
  Root of Trust for Measurement (S-RTM).

* Protection from Direct Memory Access (DMA) attacks.

The TCG measured boot chain of trust is should be enabled in this stage. At
this point, Authenticated UEFI Variable support must be completely functional.
This is a basic requirement for secure authentication and management of the
UEFI Secure Boot keys.
