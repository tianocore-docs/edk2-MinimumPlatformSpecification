<!--- @file
  7.9 Test Point Results

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

## 7.9 Test Point Results

| `Test Point`                                                      | `Test Subject`        | `Test Overview`                                                        | `Reporting Mechanism`                                                                                       |
| ----------------------------------------------------------------- | --------------------- | ---------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| TestPoint<br />EndOfDxe<br />DmarTable<br />Funtional ()          | DMAR table            | DMAR table is reported.                                                | Dump DMAR table.<br /><br />Set ADAPTER\_INFO\_<br />PLATFORM\_TEST\_<br />POINT\_STRUCT                    |
| TestPoint<br />ReadyToBoot<br />AcpiTable<br />Functional ()      | ACPI table            | ACPI tables are valid.                                                 | Dump installed ACPI tables.<br /><br />Set ADAPTER\_INFO\_<br />PLATFORM\_TEST\_<br />POINT\_STRUCT         |
| TestPoint<br />ReadyToBoot<br />GcdResource<br />Functional ()    | GCD resource          | Memory resources are described consistently in ACPI tables and GDT.    | Dump installed ACPI tables and GDT.<br /><br />Set ADAPTER\_INFO\_<br />PLATFORM\_TEST\_<br />POINT\_STRUCT |
| TestPoint<br />ReadyToBoot<br />HstiTable<br />Functional ()      | HSTI table            | HSTI table is reported.                                                | Dump HSTI table.<br /><br />Set ADAPTER\_INFO\_<br />PLATFORM\_TEST\_<br />POINT\_STRUCT                    |
| TestPoint<br />ReadyToBoot<br />EsrtTable<br />Functional ()      | ESRT table            | ESRT table is reported.                                                | Dump ESRT table.<br /><br />Set ADAPTER\_INFO\_<br />PLATFORM\_TEST\_<br />POINT\_STRUCT                    |
| TestPoint<br />ReadyToBoot<br />PiSignedFvBoot<br />Enabled ()    | PI signed FV boot     | Verify PI signed FV boot is enabled.                                   | Set ADAPTER\_INFO\_<br />PLATFORM\_TEST\_<br />POINT\_STRUCT                                                |
| TestPoint<br />ReadyToBoot<br />UefiSecureBoot<br />Enabled ()    | UEFI Secure Boot      | SecureBoot variable is set.                                            | Dump the SecureBoot variable.<br /><br />Set ADAPTER\_INFO\_<br />PLATFORM\_TEST\_<br />POINT\_STRUCT       |
| TestPoint<br />ReadyToBoot<br />TcgTrustedBoot<br />Enabled ()    | TCG trusted boot      | TCG protocol is installed.                                             | Dump TCG protocol capability.<br /><br />Set ADAPTER\_INFO\_<br />PLATFORM\_TEST\_<br />POINT\_STRUCT       |
| TestPoint<br />ReadyToBoot<br />TcgMor<br />Enabled ()            | TCG MOR               | MOR variable is set.                                                   | Dump the MOR UEFI variable.<br /><br />Set ADAPTER\_INFO\_<br />PLATFORM\_TEST\_<br />POINT\_STRUCT         |
| TestPoint<br />DiscoveredDma<br />Protection<br />Enabled ()      | DMA protection        | DMA protection in PEI.                                                 | Dump DMA ACPI table.<br /><br />Set ADAPTER\_INFO\_<br />PLATFORM\_TEST\_<br />POINT\_STRUCT                |
| TestPoint<br />EndOfDxe<br />DmaAcpiTable<br />Functional ()      | DMA protection        | DMA ACPI table is reported.                                            | Dump DMA ACPI table.<br /><br />Set ADAPTER\_INFO\_<br />PLATFORM\_TEST\_<br />POINT\_STRUCT                |
| TestPoint<br />EndOfDxe<br />DmaProtection<br />Enabled()         | DMA protection        | DMA protection in DXE.                                                 | Dump DMA ACPI table.<br /><br />Set ADAPTER\_INFO\_<br />PLATFORM\_TEST\_<br />POINT\_STRUCT                |

###### Table 66 Stage V Test Point Results
