<!--- @file
  2.5 Platform and Board Layer

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

## 2.5 Platform and Board Layer

The Minimum Platform Architecture is designed to provide consistency across
boot flows with the control flows defined in this specification. These control
flows are common to all platforms. Therefore, a single implementation is
intended to serve all platforms. This implementation is maintained in the
MinPlatformPkg on TianoCore.org. Throughout the standardized boot flow,
implementation-specific details are required including board resource
information for devices, buses, GPIO settings, etc. In addition, logic is
necessary to integrate the silicon solution. For Intel&reg; FSP, this involves
invoking the appropriate FSP API with the proper parameters at the proper time
in the boot flow. Such details are implemented in the board package behind the
board API defined in this specification. This results in flexibility at the
board layer for a custom software design that allows substitution of details
like silicon initialization flow while maintaining a common control flow with
other platforms. The board package is also typically responsible for other
implementation-specific integration such as providing a custom build
environment that prepares a firmware image processed by the tools required to
produce an image compatible for a given board.
