<!--- @file
  13.3 BoardInit

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

## 13.3 BoardInit

### 13.3.1 BoardInitSupportLib

```c
/** @file

Copyright (c) 2017, Intel Corporation. All rights reserved.<BR>
This program and the accompanying materials are licensed and made available under
the terms and conditions of the BSD License that accompanies this distribution.
The full text of the license may be found at
http://opensource.org/licenses/bsd-license.php.

THE PROGRAM IS DISTRIBUTED UNDER THE BSD LICENSE ON AN "AS IS" BASIS,
WITHOUT WARRANTIES OR REPRESENTATIONS OF ANY KIND, EITHER EXPRESS OR IMPLIED.

**/

#ifndef _BOARD_INIT_LIB_H_
#define _BOARD_INIT_LIB_H_

#include <PiPei.h>
#include <Uefi.h>

EFI_STATUS
EFIAPI
BoardDetect (
  VOID
  );

EFI_STATUS
EFIAPI
BoardDebugInit (
  VOID
  );

EFI_BOOT_MODE
EFIAPI
BoardBootModeDetect (
  VOID
  );

EFI_STATUS
EFIAPI
BoardInitBeforeMemoryInit (
  VOID
  );

EFI_STATUS
EFIAPI
BoardInitAfterMemoryInit (
  VOID
  );

EFI_STATUS
EFIAPI
BoardInitBeforeTempRamExit (
  VOID
  );

EFI_STATUS
EFIAPI
BoardInitAfterTempRamExit (
  VOID
  );

EFI_STATUS
EFIAPI
BoardInitBeforeSiliconInit (
  VOID
  );

EFI_STATUS
EFIAPI
BoardInitAfterSiliconInit (
  VOID
  );

EFI_STATUS
EFIAPI
BoardInitAfterPciEnumeration (
  VOID
  );

EFI_STATUS
EFIAPI
BoardInitReadyToBoot (
  VOID
  );

EFI_STATUS
EFIAPI
BoardInitEndOfFirmware (
  VOID
  );

#endif
```

### 13.3.2 MultiBoardInitSupportLib

```c
/** @file

Copyright (c) 2017, Intel Corporation. All rights reserved.<BR>
This program and the accompanying materials are licensed and made available under
the terms and conditions of the BSD License that accompanies this distribution.
The full text of the license may be found at
http://opensource.org/licenses/bsd-license.php.

THE PROGRAM IS DISTRIBUTED UNDER THE BSD LICENSE ON AN "AS IS" BASIS,
WITHOUT WARRANTIES OR REPRESENTATIONS OF ANY KIND, EITHER EXPRESS OR IMPLIED.

**/

#ifndef _MULTI_BOARD_INIT_SUPPORT_LIB_H_
#define _MULTI_BOARD_INIT_SUPPORT_LIB_H_

#include <Library/BoardInitLib.h>

typedef
EFI_STATUS
(EFIAPI *BOARD_DETECT) (
  VOID
  );

typedef
EFI_STATUS
(EFIAPI *BOARD_INIT) (
  VOID
  );

typedef
EFI_BOOT_MODE
(EFIAPI *BOARD_BOOT_MODE_DETECT) (
  VOID
  );

typedef struct {
  BOARD_DETECT  BoardDetect;
} BOARD_DETECT_FUNC;

typedef struct {
  BOARD_INIT              BoardDebugInit;
  BOARD_BOOT_MODE_DETECT  BoardBootModeDetect;
  BOARD_INIT              BoardInitBeforeMemoryInit;
  BOARD_INIT              BoardInitAfterMemoryInit;
  BOARD_INIT              BoardInitBeforeTempRamExit;
  BOARD_INIT              BoardInitAfterTempRamExit;
} BOARD_PRE_MEM_INIT_FUNC;

typedef struct {
  BOARD_INIT              BoardInitBeforeSiliconInit;
  BOARD_INIT              BoardInitAfterSiliconInit;
} BOARD_POST_MEM_INIT_FUNC;

typedef struct {
  BOARD_INIT              BoardInitAfterPciEnumeration;
  BOARD_INIT              BoardInitReadyToBoot;
  BOARD_INIT              BoardInitEndOfFirmware;
} BOARD_NOTIFICATION_INIT_FUNC;

EFI_STATUS
EFIAPI
RegisterBoardDetect (
  IN BOARD_DETECT_FUNC  *BoardDetect
  );

EFI_STATUS
EFIAPI
RegisterBoardPreMemoryInit (
  IN BOARD_PRE_MEM_INIT_FUNC  *BoardPreMemoryInit
  );

EFI_STATUS
EFIAPI
RegisterBoardPostMemoryInit (
  IN BOARD_POST_MEM_INIT_FUNC  *BoardPostMemoryInit
  );

EFI_STATUS
EFIAPI
RegisterBoardNotificationInit (
  IN BOARD_NOTIFICATION_INIT_FUNC  *BoardNotificationInit
  );

#endif
```
