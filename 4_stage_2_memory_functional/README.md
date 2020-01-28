<!--- @file
  4 Stage II: Memory Functional

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

## 4.1 Overview

The objective of Stage II is to enable a minimal boot path memory
initialization code execution that successfully installs permanent memory.

### 4.1.1 Major Execution Activities

* Complete execution of the memory initialization module.
* Discover, train and install permanent memory.
* Migrate the temporary memory/stack to permanent memory.
* Migrate any code modules from temporary RAM to permanent memory.
* Perform cache configuration for a post-memory environment.
* Execute memory installed notification actions.

| `Stage II Functionality`                    |
| --------------------------------------------|
| Non-volatile storage read-only access       |
| Pre-memory silicon policy initialization    |
| Basic services like cache and CPU IO        |
| Initialization of decompression capability  |
| Memory initialization and basic memory test |

### 4.1.2 Main Control Flow

Stage II extends the Stage I control flow by executing the platform and silicon
initialization required for memory initialization. The stage is completed when
permanent memory is installed. Since execution prior to memory initialization
typically occurs in a resource-constrained environment, the code in this stage
is not compressed. To simplify silicon enabling which may be opaque to the
board engineer in the form of a binary blob, Stage II enabling does not
strictly constrain the extent of silicon initialization. In particular, it is
recommended to perform standard security lock functionality such as register
locks, privilege level changes, and other actions that are in the system
requirements to reduce conditional logic and therefore potential for error in
enabling those settings. This only pertains to security settings within the
chipset. This does not include larger industry standard security features such
as UEFI Secure Boot and TCG measured boot. Those features are enabled in Stage
V Security Enable.

![Stage II Main Control Flow](/media/4_stage_2_main_control_flow.png)
###### Figure 5 Stage II Main Control Flow

