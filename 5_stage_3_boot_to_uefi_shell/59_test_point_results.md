<!--- @file
  5.9 Test Point Results

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

## 5.9 Test Point Results

| `Test Point`                                               | `Test Subject`                    | `Test Overview`                                                                                                                               | `Reporting Mechanism`                                                                                              |
| ---------------------------------------------------------- | --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| TestPointEndOfPeiMtrrFunctional ()                         | MTRR after EndOfPei               | Confirm MTRR settings.<br /><br />Example:<ul><li>No overlap</li><li>DXE memory is WB</li><li>MMIO is UC</li><li>Flash region is UC</li></ul> | Dump result to serial log.<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT                                  |
| TestPointEndOfPeiSystemResourceFunctional ()               | Resource HOB<br /><br />SMRAM HOB | SMRAM<br /><br />No system resource overlap                                                                                                   | Dump result to serial log.<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT                                  |
| TestPointEndOfPeiPciBusMasterDisabled ()                   | PCI device<br /><br />BME         | Check if BME is cleared                                                                                                                       | Dump result to serial log.<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT                                  |
| TestPointPciEnumerationDonePciResourceAllocated ()         | PCI device resource               | Check if all PCI devices have been assigned proper resources.                                                                                 | Dump PCI resource assignment.<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT                               |
| TestPointPciEnumerationDonePciBusMasterDisabled ()         | PCI device<br /><br />BME         | Check if BME is cleared                                                                                                                       | Dump result to serial log.<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT                                  |
| TestPointEndOfDxeNoThirdPartyPciOptionRom ()               | 3rd party PCI option ROMs         | Check if any 3rd party PCI option ROMs have been dispatched before EndOfDxe.                                                                  | Dump LoadedImage.<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT                                           |
| TestPointReadyToBootUefiMemoryAttributeTableFunctional ()  | UEFI memory attribute table       | Table is reported.<br /><br />Image code and data is consistent with the table.                                                               | Dump UEFI Table and UEFI Image Info.<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT                        |
| TestPointReadyToBootMemoryTypeInformationFunctional ()     | Memory type information           | Inspect and verify memory type information is correct.<br /><br />Confirm no fragmentation exists in the ACPI/Reserved/Runtime memory regions.| Dump the memory type information settings to the debug log.<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT |
| TestPointReadyToBootUefiConsoleVariableFunctional ()       | Console                           | Inspect and verify console variable information is correct.                                                                                   | Dump the variable information to the serial log<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT             |
| TestPointReadyToBootUefiBootVariableFunctional ()          | Boot Option                       | Inspect and verify boot option information is correct.                                                                                        | Dump the variable information to the serial log<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT             |

###### Table 38 Stage III Test Point Results
