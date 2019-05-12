<!--- @file
  8.7 Signed Capsule Update Enabling Example

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

## 8.7 Signed Capsule Update Enabling Example
***
**Note:** The signed capsule update example is presently incomplete and
no longer accurately represents the latest vision for advanced features. 
This section will be updated to provide more accurate examples in the future.
***

### 8.7.1 Overview

The Signed Capsule Update stack supports capsule update functionality. Refer
to the UEFI specification for related interfaces. More details on UEFI Signed
Capsule Update can be found online such as the following resource
[A Tour Beyond BIOS - Capsule Update and Recovery in EDK II](https://github.com/tianocoredocs/Docs/raw/master/White_Papers/A_Tour_Beyond_BIOS_Capsule_Update_and_Recovery_in_EDK_II.pdf)

### 8.7.2 Firmware Volumes

TBD

### 8.7.3 Modules

The signed capsule update stack is a relatively simple feature stack. The
majority of the modules are board and silicon independent so minimal
porting is required.

#### 8.7.3.1 UEFI Components (DXE)

The libraries consumed are the subset of libraries required by this
specification. Some libraries are defined in this specification, some are
defined in EDK II documentation.

| `Item`                   | `Producing Package` | `Libraries Consumed`   |
| ------------------------ | ------------------- | ---------------------- |
| CapsuleRuntime.inf       | MdeModulePkg        |                        |
| SystemFirmwareUpdate.inf | SignedCapsulePkg    | PlatformFlashAccessLib |

#### 8.7.3.2 Platform Architecture Libraries

Board porting will require creation of libraries identified as produced by the
BoardPkg. Depending on the board, there may be existing libraries that are
sufficient for a board, so it is important to assess the utility of existing
library instances when developing board support.

| `Item`                    | `API Definition Package` | `Producing Package` | `Description`                 |
| ------------------------- | ------------------------ | ------------------- | ----------------------------- |
| `PlatformFlashAccessLib`  | SignedCapsule Pkg        | BoardPkg            | Signed Capsule Update details |

### 8.7.4 Required Functions

None

### 8.7.5 Configuration

| `PCD`                                                        | `Purpose`                                                                                           |
| ------------------------------------------------------------ | --------------------------------------------------------------------------------------------------- |
| gEfiMdeModulePkgTokenSpaceGuid. PcdSupportUpdateCapsuleReset | Indicates if the platform can support update capsule across a system reset.                         |
| gEfiMdeModulePkgTokenSpaceGuid. PcdMaxSizeNonPopulateCapsule | Indicates the maximum size of the capsule image without a reset flag that the platform can support. |
| gEfiMdeModulePkgTokenSpaceGuid. PcdMaxSizePopulateCapsule    | Indicates the maximum size of the capsule image with a reset flag that the platform can support.    |

### 8.7.6 Data Flows

None

### 8.7.7 Control Flows

None

### 8.7.8 Build Files

These are the advanced feature module build files (i.e. INF files) included in
a board to build and include the FvSignedCapsuleUpdate.fv in the FvAdvanced
firmware volume.

### 8.7.9 Test Point Results

There are currently no test points defined for the signed capsule update stack.

### 8.7.10 Functional Exit Criteria

TBD

### 8.7.11 Feature Enabling Checklist

The following steps should be followed to enable a platform for enabling the
Signed Capsule Update feature stack:

1. Create a BoardCapsuleLib library class instance

2. Include BoardCapsuleLib

3. Include SecureCapsuleUpdate.dsc

4. Include SecureCapsuleUpdate.fdf

5. Add FvSecureCapsuleUpdate.fv

6. Set Set `gMinPlatformPkgTokenSpaceGuid.PcdBootStage` = 6

7. Verify if reset is required or optional

8. Verify PCD default sizes cover required firmware image sizes

9. Verify functionality as per whitepaper referenced in Overview

### 8.7.12 Common Optimizations

None
