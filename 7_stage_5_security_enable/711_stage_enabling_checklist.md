<!--- @file
  7.11 Stage Enabling Checklist

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

## 7.11 Stage Enabling Checklist

The following steps should be followed to enable a platform for Stage V.

1. Update *Board*Pkg/*Board*.

    1. Deploy the UEFI secure boot variables (PK/KEK/db/dbx)

    2. Configure `PcdTpmInstanceGuid` to select TPM hardware. Default of
       `gEfiTpmDeviceInstanceTpm20DtpmGuid`value is usually correct.

2. UEFI secure boot

    1. Update `PlatformSecureLib`:`UserPhysicalPresent ()`, to check if a
       user is physically present to authorize change of authenticated variables

3. For TCG trusted boot

    1. May select TPM2 instance `PcdTpmInstanceGuid`.

    2. May set `PcdFirmwareDebuggerInitialized` based on whether or not a
       Firmware Debugger is attached to the platform

4. For DMA Protection

    1. May include IOMMU driver to do DMA protection, if the silicon supports
       IOMMU.
5. Ensure all PCDs in the configuration section (DSC files) are correct for your board.

    1. Set `gMinPlatformPkgTokenSpaceGuid.PcdBootStage` = 5

6. Ensure all required binaries in the flash file (FDF files) are correct for your board.

7. Boot, collect log, verify test point results defined in section 7.9 Test Point Results are correct

