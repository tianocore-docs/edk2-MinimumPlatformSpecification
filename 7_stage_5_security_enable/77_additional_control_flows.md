<!--- @file
  7.7 Additional Control Flows

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

## 7.7 Additional Control Flows

This section describes how the security features are embedded in the control
flows. PSCS/ChipSec required features should be enabled in this stage in addition
to other general security flow. This section will also elaborate on each security
feature and the platform code implementation required to enable the feature.

***
**Note:** Some of these features can be treated as an advanced feature and can
be turned on or off based on system-specific usage. However, this section
serves as a guideline to develop platform code for security features.
***

### 7.7.1 UEFI Secure Boot

Refer to the UEFI specification and the whitepaper
[A Tour Beyond BIOS - Implementing UEFI Authenticated Variables in SMM with EDK II](https://github.com/tianocore-docs/Docs/raw/master/White_Papers/A_Tour_Beyond_BIOS_Implementing_UEFI_Authenticated_Variables_in_SMM_with_EDKII_V2.pdf)

### 7.7.2 Hardware Authenticated Boot

UEFI Secure boot provides verification of 3rd party drivers, such as the OS
loader or PCI option ROMs.

A platform may provide additional authentication for firmware volume.

For example: Intel Boot Guard, or PI signed FV.

* Intel&reg; Boot Guard provides a hardware way to verify the initial boot block 
  (IBB) code. After power on, the CPU Microcode finds a Boot Guard ACM and 
  executes the Boot Guard ACM, which is signed by Intel. Then the Boot Guard 
  ACM takes the Boot Guard manifest and verifies the IBB code.

* The PI specification also provides the verification for the system firmware
  code on the board. Refer to PI specification, EFI Signed Firmware Volumes and
  EFI Signed Sections.

The whole hardware based secure boot flow on an Intel Boot Guard platform is:

1. Startup ACM or some equivalent module verifies the initial boot block of the 
system firmware.
    * Intel&reg; Boot Guard Technology is one possible implementation
2. The initial boot block verifies the rest of the system firmware.
    * PI signed FV is one possible implementation. An implementation may choose 
      PKCS7 or RSA2048_SHA256 based signing verification.
    * The other option is just to use the HASH for the rest of the system 
      firmware. In PEI phase, the code who installs the addition FV for the post 
      memory phase need verify the HASH of the system firmware.
3. The system firmware verifies 3rd party code.
    * UEFI secure boot is the implementation.

### 7.7.3 TCG Trusted Boot and Memory Overwrite Request (MOR)

Refer to TCG platform specification and the white paper
[A Tour Beyond BIOS - Implementing TPM Support in EDK II](https://firmware.intel.com/sites/default/files/resources/A_Tour_Beyond_BIOS_Implementing_TPM2_Support_in_EDKII.pdf)

### 7.7.4 DMA (VT-d) Protection

Refer to Intel&reg; VT-d specification and the white paper
[Using IOMMU for DMA Protection in UEFI](https://firmware.intel.com/sites/default/files/Intel_WhitePaper_Using_IOMMU_for_DMA_Protection_in_UEFI.pdf
)
