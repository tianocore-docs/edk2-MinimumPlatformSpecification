<!--- @file
  Appendix B.2 Test Point Check Infrastructure

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

## B.2 Test Point Check Infrastructure

Today's platforms are tested against several test suites such as Chipsec,
Windows Hardware Security Test Infrastructure (HSTI), Windows Hardware Logo Kit
(HLK), Linux UEFI Validation (LUV), and others. However, platforms may have
platform-specific requirements not covered by test suites enforcing
specification or general hardware compliance. The Test Point Check
infrastructure is intended to test that actions such as MTRRs are configured
correctly, FV HOBs are reported properly, no 3rd party options ROMs are
executed before allowed, MemoryTypeInformation is reported correctly, and any
other custom logic that platform implementer considers appropriate based on the
platform requirements.

The Test Point infrastructure is supported by two primary libraries,
TestPointLib and TestPointCheckLib. TestPointLib reports test results via the
`ADAPTER_INFO_PLATFORM_TEST_POINT` structure defined below. The test result is
validated in the TestPointCheckLib.

```c
typedef struct {
  UINT32 Version;
  UINT32 Role;
  CHAR16 ImplementationID[256];
  UINT32 FeaturesSize;

  //UINT8 FeaturesImplemented[]; <- PCD set to define features
  //UINT8 FeaturesVerified[]; <- PCD read and set to determine features verified
  //CHAR16 ErrorString[];
} ADAPTER_INFO_PLATFORM_TEST_POINT;
```

![Test Point Check Infrastructure](/media/11_test_point_check_infrastructure.png)
###### Figure 11 Test Point Check Infrastructure
