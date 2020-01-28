<!--- @file
  Appendix C.2 ACPI Table Contents

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

## C.2 ACPI Table Contents

There are three types of tables supported. _Standard Static Tables,_
_Differentiated System Description Table (DSDT), Secondary System Description
Table (SSDT)._ The standard static tables have a defined structure in the ACPI
specification. The contents of the DSDT and SSDT are described in this
specification.

### C.2.1 DSDT Contents

DSDT is a mandatory fixed table that is pointed to by the FADT (Fixed ACPI
Description Table).

#### C.2.1.1 Stage IV Build

Stage IV is intended to have the minimum configuration to boot a platform with
basic features and minimal set of devices enabled. Similarly ACPI
implementation should have a minimal framework implemented for ACPI compliant
OS.

The DSDT in this case should have a root and system bus defined. In addition to
that, the DSDT will have device scopes for all the devices present in the
minimum platform required packages (Section 8.1.1).

#### C.2.1.2 Stage VI Build

In this case, DSDT will include the following Device scopes and objects:

1. Device scopes for all PCI devices that need an ACPI component
2. Global NVS area region defined
3. Interrupt routing (_PRT method)
