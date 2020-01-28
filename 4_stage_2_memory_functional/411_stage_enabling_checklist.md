<!--- @file
  4.11 Stage Enabling Checklist

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

## 4.11 Stage Enabling Checklist

The following steps should be followed to enable a platform for Stage II.

1. Update *GenerationOpenBoardPkg*/*BoardXXX*

    1. Add Board boot mode detection code in `BoardBootModeDetect ()`,
       *Board*XXX/BoardInitLib/Pei*BoardXXX*InitPreMemoryLib.c.

        1. The boot mode can be hardcoded. It should reflect actual 
           functionality based upon the feature, such as S3 (silicon register), 
           Capsule (variable), Recovery (GPIO).

    2. Add Board pre-memory initialization code in `BoardInitBeforeMemoryInit ()` and `BoardInitAfterMemoryInit ()`, *BoardXXX*/BoardInitLib/Pei*BoardXXX*InitPreMemLib.c.

        1. It initializes board specific hardware devices, such as GPIO.

        2. It also updates pre-memory policy configuration by using PCD

    3. Add Board policy update code in `SiliconPolicyUpdatePreMemory ()`,
       *BoardXXX*/PeiSiliconPolicyUpdateLib/Pei*BoardXXX*InitPreMemoryLib.c.

        1. The PCD updated in `BoardInitBeforeMemoryInit ()` might be used here.

2. Ensure all PCDs in the configuration section (DSC files) are correct for your board.

    1. Set `gMinPlatformPkgTokenSpaceGuid.PcdBootStage` = 2

3. Ensure all required binaries in the flash file (FDF files) are correct for your board.

4. Boot, collect log, verify test point results defined in section 4.9 are correct.
