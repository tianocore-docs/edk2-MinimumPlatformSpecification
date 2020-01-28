<!--- @file
  3 Stage I: Minimal Debug

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

## 3.1 Overview

The objective of Stage I is to provide a foundation for more complex
development in later stages. The board should implement a board-specific
minimal code path capable of firmware debug output. Basic debug capability
serves as a base for development activities in later stages. As Stage I is
inherently foundational to product execution it may include more content and
complexity than the functionality strictly required for debug output.

### 3.1.1 Major Execution Activities

* Establish temporary memory.
* Perform pre-memory board-specific initialization.
* Board detection
* GPIOs
* Serial Port initialization (Example: SIO, HSUART)

It is not necessary for the developer to fully configure GPIO at this time. The
only required board configuration is that necessary to reach system debug
activities.

### 3.1.2 Main Control Flow

Stage I is contained within SEC and PEI phases. Code must not be compressed and
content must be capable of being mapped to memory by hardware or other firmware.

The high level control flow is described in the diagram below.
![Stage 1 Main Control Flow](/media/3_stage_1_main_control_flow.png)
###### Figure 4 Stage I Main Control Flow

These activities do not map 1:1 to the required functions. Some of this flow is
already well defined by UEFI or EDK II specifications. The following details
are focused on the Platform, Silicon, and Board interactions, and minimal
requirements for structure, consistency, and portability.
