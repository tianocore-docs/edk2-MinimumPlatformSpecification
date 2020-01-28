<!--- @file
  4.9 Test Point Results

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

## 4.9 Test Point Results

| `Test Point`                                                           | `Test Subject`                 | `Test Overview`                                                                             | `Reporting Mechanism`                                                                              |
| ---------------------------------------------------------------------- | ------------------------------ | ------------------------------------------------------------------------------------------  | -------------------------------------------------------------------------------------------------- |
| TestPointMemory<br />DiscoveredMtrr<br />Functional ()                 | MTRR after memory discovered   | Verifies MTRR settings.<br /><br />(No overlap, PEI memory WB, Flash region is WP, MMIO UC) | Dump result to serial log.<br /><br />Set ADAPTER\_INFO\_<br />PLATFORM\_TEST\_<br />POINT\_STRUCT |
| TestPointMemory<br />DiscoveredMemory<br />Resource<br />Functional () | Resource description HOB       | No memory resource overlap.                                                                 | Dump result to serial log.<br /><br />Set ADAPTER\_INFO\_<br />PLATFORM\_TEST\_<br />POINT\_STRUCT |
| TestPointMemory<br />DiscoveredFvInfo<br />Functional ()               | FV HOB and FV info PPI         | FV HOB and FV info PPI.                                                                     | Dump result to serial log.<br /><br />Set ADAPTER\_INFO\_<br />PLATFORM\_TEST\_<br />POINT\_STRUCT |

###### Table 26 Test Point Results

***
**NOTE:** _ADAPTER_INFO_PLATFORM_TEST_POINT_STRUCT can be updated by
TestPointCheckLib. The format is similar to the HSTI. See Appendix - Interface
TestPoint._
***
