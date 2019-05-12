<!--- @file
  6.9 Test Point Results

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

## 6.9 Test Point Results

| `Test Point`                                               | `Test Subject`                    | `Test Overview`                                                                                                                                | `Reporting Mechanism`                                                                                              |
| ---------------------------------------------------------- | --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| TestPointReadyToBootAcpiTableFunctional ()                 | ACPI table(s)                     | <ul><li>Table is reported.</li><li>MADT is consistent with MP services.</li></ul>                                                              | Dump ACPI tables.<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT.                                          |
| TestPointSmmReadyToLockSecureSmmCommunicationBuffer ()     | SMM communication buffer          | Only CommBuffer(s) and MMIO are mapped in the page table.                                                                                      | Dump memory map and GCD map at SmmReadyToLock and check at SmmReadyToBoot.                                         |
| TestPointSmmReadyToLockSmmMemoryAttributeTableFunctional ()| SMM memory page attribute table   | Table is reported. Image code/data mapping is accurate.<ul><li>GDT, IDT, and page table are RO</li><li>Data is NX</li><li>Code is RO</li></ul> | Dump SMM table and SMM Image Info.<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT.                         |
| TestPointSmmEndOfDxeSmrrFunctional ()                      | SMRR                              | <ul><li>SMRR is aligned.</li><li>SMRR matches SMRAM_INFO</li></ul>                                                                             | Dump SMRR and SMRAM_INFO.<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT.                                  |
| TestPointSmmReadyToBootSmmPageProtection ()                | SMM page table                    | SMM page table matches SmmMemoryAttribute table.                                                                                               | Report error based upon check.<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT.                             |
| TestPointDxeSmmReadyToLockSmramAligned ()                  | SMRAM info                        | SMRAM is aligned.                                                                                                                              | Dump SMRAM region table.<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT.                                   |
| TestPointDxeSmmReadyToLockWsmtTableFunctional ()           | WSMT table                        | WSMT is reported.                                                                                                                              | Dump WSMT table.<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT.                                           |
| TestPointDxeSmmReadyToBootSmiHandlerInstrument ()          | SmiHandler profile                | SmiHandler profile.                                                                                                                            | Dump SMI Handler profile.<br /><br />Set ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT.                                  |

###### Table 52 Stage IV Test Point Results
