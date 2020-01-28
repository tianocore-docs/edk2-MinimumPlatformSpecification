<!--- @file
  3.4 Required Functions

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

## 3.4 Required Functions

The following functions are required to exist and to execute in the listed
order. The component that provides the function is not specified because it is
not required by the architecture.

\* In the common EDK II open source code.

### 3.4.1 Required SEC functions

| `Name`                      | `Purpose`                                    |
| --------------------------- | -------------------------------------------- |
| ResetHandler (*)            | The reset vector invoked by silicon          |
| TempRamInit                 | Silicon initializes temporary memory         |
| TestPointTempMemoryFunction | Test temporary memory functionality          |
| SecStartup (*)              | First C code execution, constructs PEI input |
| TestPointEndOfSec           | Verify state before switching to PEI         |

###### Table 9 Stage I SEC Functions

### 3.4.2 Required PEI functions

| `Name`                           | `Purpose`                                                |
| -------------------------------- | -------------------------------------------------------- |
| PeiCore (*)                      | PEI entry point                                          |
| PeiDispatcher (*)                | Calls the entry points of PEIM                           |
| ReportPreMemFv                   | Installs firmware volumes required in pre-memory         |
| BoardDetect                      | Board detection of the motherboard type                  |
| BoardDebugInit                   | Board specific initialization for debug device           |
| PlatformHookSerialPortInitialize | Board serial port initialization. Called from SEC or PEI |
| TestPointDebugInitDone           | Verify debug functionality                               |

###### Table 10 Stage I PEI Functions
