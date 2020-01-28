<!--- @file
  Appendix C.3 ACPI Device Categorization

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

## C.3 ACPI Device Categorization

ACPI device description tables such as DSDT and SSDT are comprised of device
scopes and methods that define the capabilities and resources of an ACPI
device. For scalability purposes, the ACPI devices are categorized in a manner
that they can be easily plugged in and out of UEFI FW.

### C.3.1 Silicon Specific Devices

These devices are silicon specific and are assumed to not change with different
SKUs and stepping of the silicon. These devices will become part of DSDT as it
is a mandatory table containing the fixed devices for the systems.

The number of silicon devices present in the DSDT will be decided by the scope
of minimum and full build.

### C.3.2 SKU Specific Devices

These devices are SKU specific and are assumed to change based on various SKUs.
They are considered to be dynamic as they can be enabled/disabled/modified
based on setup knobs or softstraps etc.

Because of their dynamic nature, these devices are added in the Platform SSDT.
Every SKU will have a unique Platform SSDT installed. It will only contain
devices present on that platform.

### C.3.3 Board Specific Devices

These devices are board specific and are assumed to change based on the various
board SKUs. These devices will also become part of SSDTs. These devices can
have an SSDT of their own or get added to the platform SSDT depending on their
availability on multiple SKUs. A fairly common board device will be added to
the platform SSDT and the other devices can have a SSDT of their own.

### C.3.4 Feature Specific Devices/Methods

These devices or methods are optional as they are exposed to handle certain
advanced features. They will be added to DSDT or SSDT depending on the device
they are being added for. For example a special DSM (device specific method) is
to be added for an Audio codec, then it will fall under the Platform/Board SSDT.
