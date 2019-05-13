<!--- @file
  13.4 SiliconPolicyInit

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

## 13.4 SiliconPolicyInit

### 13.4.1 SiliconPolicyInitLib

The SiliconPolicyInitLib provides functions that silicon code initializes the default policy.

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

#ifndef _SILICON_POLICY_INIT_LIB_H_
#define _SILICON_POLICY_INIT_LIB_H_

/**
  Performs silicon pre-memory policy initialization.

  The meaning of Policy is defined by silicon code.
  It could be the raw data, a handle, a PPI, etc.

  The returned data must be used as input data for SiliconPolicyDonePreMemory(),
  and SiliconPolicyUpdateLib.SiliconPolicyUpdatePreMemory().

  1) In FSP path, the input Policy should be FspmUpd.
  Value of FspmUpd has been initialized by FSP binary default value.
  Only a subset of FspmUpd needs to be updated for different silicon sku.
  The return data is same FspmUpd.

  2) In non-FSP path, the input policy could be NULL.
  The return data is the initialized policy.

  @param[in, out] Policy       Pointer to policy.

  @return the initialized policy.
**/
VOID *
EFIAPI
SiliconPolicyInitPreMemory (
  IN OUT VOID *Policy OPTIONAL
  );

/*
  The silicon pre-mem policy is finalized.
  Silicon code can do initialization based upon the policy data.

  The input Policy must be returned by SiliconPolicyInitPreMemory().

  @param[in] Policy       Pointer to policy.

  @retval RETURN_SUCCESS The policy is handled consumed by silicon code.
*/
RETURN_STATUS
EFIAPI
SiliconPolicyDonePreMemory (
  IN VOID *Policy
  );

/**
  Performs silicon post-memory policy initialization.

  The meaning of Policy is defined by silicon code.
  It could be the raw data, a handle, a PPI, etc.

  The returned data must be used as input data for SiliconPolicyDonePostMemory(),
  and SiliconPolicyUpdateLib.SiliconPolicyUpdatePostMemory().

  1) In FSP path, the input Policy should be FspsUpd.
  Value of FspsUpd has been initialized by FSP binary default value.
  Only a subset of FspsUpd needs to be updated for different silicon sku.
  The return data is same FspsUpd.

  2) In non-FSP path, the input policy could be NULL.
  The return data is the initialized policy.

  @param[in, out] Policy       Pointer to policy.

  @return the initialized policy.
**/
VOID *
EFIAPI
SiliconPolicyInitPostMemory (
  IN OUT VOID *Policy OPTIONAL
  );

/*
  The silicon post-memory policy is finalized.
  Silicon code can do initialization based upon the policy data.

  The input Policy must be returned by SiliconPolicyInitPostMemory().

  @param[in] Policy       Pointer to policy.

  @retval RETURN_SUCCESS The policy is handled consumed by silicon code.
*/
RETURN_STATUS
EFIAPI
SiliconPolicyDonePostMemory (
  IN VOID *Policy
  );

/**
  Performs silicon late policy initialization.

  The meaning of Policy is defined by silicon code.
  It could be the raw data, a handle, a protocol, etc.

  The returned data must be used as input data for SiliconPolicyDoneLate(),
  and SiliconPolicyUpdateLib.SiliconPolicyUpdateLate().

  In FSP or non-FSP path, the input policy could be NULL.
  The return data is the initialized policy.

  @param[in, out] Policy       Pointer to policy.

  @return the initialized policy.
**/
VOID *
EFIAPI
SiliconPolicyInitLate (
  IN OUT VOID *Policy OPTIONAL
  );

/*
  The silicon late policy is finalized.
  Silicon code can do initialization based upon the policy data.

  The input Policy must be returned by SiliconPolicyInitLate().

  @param[in] Policy       Pointer to policy.

  @retval RETURN_SUCCESS The policy is handled consumed by silicon code.
*/
RETURN_STATUS
EFIAPI
SiliconPolicyDoneLate (
  IN VOID *Policy
  );

#endif
```

### 13.4.2 SiliconPolicyUpdateLib

The SiliconPolicyUpdateLib provides functions that board code overrides the default policy.

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

#ifndef _SILICON_POLICY_UPDATE_LIB_H_
#define _SILICON_POLICY_UPDATE_LIB_H_

/**
  Performs silicon pre-memory policy update.

  The meaning of Policy is defined by silicon code.
  It could be the raw data, a handle, a PPI, etc.

  The input Policy must be returned by SiliconPolicyDonePreMemory().

  1) In FSP path, the input Policy should be FspmUpd.
  A platform may use this API to update the FSPM UPD policy initialized
  by the silicon module or the default UPD data.
  The output of FSPM UPD data from this API is the final UPD data.

  2) In non-FSP path, the board may use additional way to get
  the silicon policy data field based upon the input Policy.

  @param[in, out] Policy       Pointer to policy.

  @return the updated policy.
**/
VOID *
EFIAPI
SiliconPolicyUpdatePreMemory (
  IN OUT VOID *Policy
  );

/**
  Performs silicon post-memory policy update.

  The meaning of Policy is defined by silicon code.
  It could be the raw data, a handle, a PPI, etc.

  The input Policy must be returned by SiliconPolicyDonePostMemory().

  1) In FSP path, the input Policy should be FspsUpd.
  A platform may use this API to update the FSPS UPD policy initialized
  by the silicon module or the default UPD data.
  The output of FSPS UPD data from this API is the final UPD data.

  2) In non-FSP path, the board may use additional way to get
  the silicon policy data field based upon the input Policy.

  @param[in, out] Policy       Pointer to policy.

  @return the updated policy.
**/
VOID *
EFIAPI
SiliconPolicyUpdatePostMemory (
  IN OUT VOID *Policy
  );

/**
  Performs silicon late policy update.

  The meaning of Policy is defined by silicon code.
  It could be the raw data, a handle, a Protocol, etc.

  The input Policy must be returned by SiliconPolicyDoneLate().

  In FSP or non-FSP path, the board may use additional way to get
  the silicon policy data field based upon the input Policy.

  @param[in, out] Policy       Pointer to policy.

  @return the updated policy.
**/
VOID *
EFIAPI
SiliconPolicyUpdateLate (
  IN OUT VOID *Policy
  );

#endif
```
