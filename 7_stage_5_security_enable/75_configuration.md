<!--- @file
  7.5 Configuration

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

## 7.5 Configuration

This section defines the configurable items that must be available to achieve
Stage IV functionality.

These definitions may be both source and binary in nature.
### 7.5.1 Security Related Configuration

| `Component`                            | `Name`          | `Producer` | `Consumer` | `Purpose`                                                                           | `Porting Category`                       |
| -------------------------------------- | --------------- | ---------- | ---------- | ----------------------------------------------------------------------------------- | ---------------------------------------- |
| Post Build                             | PK              | Board      | Core       | PK variable                                                                         | Platform Policy: UEFI Secure Boot        |
|                                        | KEK             | Board      | Core       | KEK variable                                                                        | Platform Policy: UEFI Secure Boot        |
|                                        | db              | Board      | Core       | db variable                                                                         | Platform Policy: UEFI Secure Boot        |
|                                        | dbx             | Board      | Core       | dbx variable                                                                        | Platform Policy: UEFI Secure Boot        |
| PcdTpmInstance<br />Guid               | GUID            | Board      | Core       | Select TPM instance                                                                 | Platform Policy: TCG trusted boot        |
| PcdTpm2<br />InitializationPolicy      | UINT8           | Board      | Core       | Choose if TPM driver need send Tpm2Init.                                            | Platform Policy: TCG trusted boot        |
| PcdTpm2Self<br />TestPolicy            | UINT8           | Board      | Core       | Choose if TPM driver need send Tpm2SelfTest                                         | Platform Policy: TCG trusted boot        |
| PRE_MEM_SILICON_POLICY                 | MOR data        | Board      | Silicon    | The board code consumes the MOR variable and pass it to MemoryInit module as policy | Platform Policy: TCG MOR                 |
| L"MemoryOverwrite<br />RequestControl" | MOR Variable    | OS         | Board      | OS indicates to UEFI FW the MOR request.                                            | Platform Policy: TCG MOR                 |
| PcdVTdPolicy<br />PropertyMask         | VTd policy mask | Platform   | Core       | VTd policy                                                                          | Platform Policy: DMA                     |

###### Table 62 Stage V Security Configuration

### 7.5.2 FV Related Configuration

| `PCD`                                                           | `Purpose`                                                                                                                        |
| --------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| gEfiMdeModulePkgTokenSpaceGuid. PcdFlashNvStorageVariableBase   | Base address of the NV variable range in flash device.                                                                           |
| gEfiMdeModulePkgTokenSpaceGuid. PcdFlashNvStorageVariableSize   | Size of the non-volatile variable range. Note that this value should less than or equal to PcdFlashNvStorageFtwSpareSize.        |
| gEfiMdeModulePkgTokenSpaceGuid. PcdFlashNvStorageFtwWorkingBase | Base address of the FTW working block range in flash device.                                                                     |
| gEfiMdeModulePkgTokenSpaceGuid. PcdFlashNvStorageFtwWorkingSize | Size of the FTW working block range.                                                                                             |
| gEfiMdeModulePkgTokenSpaceGuid. PcdFlashNvStorageFtwSpareBase   | Base address of the FTW spare block range in flash device. Note that this value should be block size aligned.                    |
| gEfiMdeModulePkgTokenSpaceGuid. PcdFlashNvStorageFtwSpareSize   | Size of the FTW spare block range. Note that this value should larger than PcdFlashNvStorageVariableSize and block size aligned. |
| gMinPlatformPkgTokenSpaceGuid. PcdFlashFvSecurityBase           | Security FV base address.                                                                                                        |
| gMinPlatformPkgTokenSpaceGuid. PcdFlashFvSecuritySize           | Security FV size.                                                                                                                |

###### Table 63 Stage V Flash Map Configuration PCDs

## 7.5.3 Feature Related Configuration

| `PCD`                                                       | `Purpose`                   |
| ----------------------------------------------------------- | --------------------------- |
| gMinPlatformModuleTokenSpaceGuid.PcdSmiHandlerProfileEnable | Enable SMI handler profile. |
| gMinPlatformModuleTokenSpaceGuid.PcdTpm2Enable              | Enable TPM2.                |
| gMinPlatformModuleTokenSpaceGuid.PcdUefiSecureBootEnable    | Enable UEFI Secure Boot.    |

###### Table 64 Stage V Feature Configuration
