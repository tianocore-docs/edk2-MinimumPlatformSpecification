<!--- @file
  5 Stage III: Boot to UEFI Shell

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

## 5.1 Overview

The primary objective of Stage III is to enable a minimal boot path that
successfully loads the UEFI Shell. A secondary objective for Stage III is to be
silicon and board agnostic. All silicon and board specific details should be
leveraged from Stages I and II. Demonstrating the capability to load the UEFI
shell does not imply that the UEFI shell is a required component in the end
product firmware. It does ensure that the platforms with a terminal boot stage
target greater than Stage II can load the UEFI shell so the system can be
analyzed and configured in the UEFI boot services environment with well-defined
behavior in a consistent manner with other Minimum Platform
specification-compliant systems.

The minimal UI capability that is required is serial console. UEFI variables
must be supported with at least emulated variable behavior. UEFI variable
storage to a non-volatile media such as SPI NOR flash is acceptable if the
platform requirements mandate such support. Additional capabilities are
optional and must not be assumed. These include USB input devices, graphics
devices, and other storage devices.

### 5.1.1 Major Execution Activities

* DXE Initial Program Load (IPL)

* DXE Core initialization and dispatcher execution

* Initialize the generic infrastructure required for the DXE environment o
  Installation of DXE architectural protocols o Initialization of
  architecturally required hardware such as timers

* Post-memory silicon policy initialization

* Serial console input and output capabilities

| `Stage III Functionality`                                                        |
| -------------------------------------------------------------------------------- |
| Universally usable infrastructure: DXE Core, Minimal BDS, console infrastructure |
| Silicon agnostic architectural protocol producing hardware modules               |
| UEFI Variable support (emulation allowed)                                        |
| UEFI Shell                                                                       |
| Tests for Memory Map, Cache Map, architectural hardware                          |

### 5.1.2 Main Control Flow

Stage III extends Stage II control flow by executing Driver Execution
Environment (DXE), executing Boot Device Selection (BDS) and invoking the UEFI
Shell.

![Stage III Main Control Flow](/media/5_stage_3_main_control_flow.png)
###### Figure 8 Stage III Main Control Flow

After memory is installed during Stage II, the remaining silicon and platform
initialization must take place in the PEI phase only. All silicon
initialization tasks should have been completed in Stage II, and there should
be no silicon-specific initialization required in the DXE phase. The default
console information should be transferred via a HOB and initialized and used in
Stage III.
