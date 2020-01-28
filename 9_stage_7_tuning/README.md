<!--- @file
  9 Stage VII: Tuning

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

## 9.1 Overview
***
**Note:** This is a proposed stage in the architecture and this section is
reserved for future completion and definition of the stage. Any implementation 
may ignore this stage until this section is completed and this notice is 
removed.

It is anticipated that  future versions of this architecture specification 
will provide details for embedded performance tuning, common component
tuning, and more invasive customization. The objective for this section is to
provide a spectrum of options that keep as many board designs as consistent as
possible. Some potential topics follow, but should not be reviewed at this
***

In Stage VII, the fully featured is tuned for production.

First, it can be worthwhile to look at the embedded features and performance
oriented options that have been designed into the core or minimum platform. For
example, if you do not support network boot, the PciBus driver provides a PCD
to disable dispatching the network option ROM. By default, network option ROM
dispatch is enabled. This is a known tunable setting.

Second, it can be worthwhile to strip unused components from the defined FV.
For simplicity and consistency of progressing through Stage VI, it is better to
use the provided code consistent with the architecture. Once a stable and fully
functional system is completed, it is intended that platform architecture
compatible systems can still remove unneeded components in order to finely tune
the product. The core provides a tool named FMMT that can be used to process
the build output and remove unnecessary components. Alternatively, a board can
copy and modify the provided Build DSC and FDF files in the MinPlatformPkg and
SiliconPkg. The former increases build time. The latter increases integration
effort for new core, MinPlatformPkg, and SiliconPkg releases.

Third, it is often necessary to enable and use tools to perform detailed
analysis of performance and size to identify hotspots that need to be improved.
