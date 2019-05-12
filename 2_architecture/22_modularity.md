<!--- @file
  2.2 Modularity

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

## 2.2 Modularity

Throughout the architecture you will find a mix of static and dynamic
modularity. Static libraries are used to make the platform and board code
simpler and more approachable. Dynamic linking in the form of UEFI PI
Architecture components (PEIM and drivers) as well as large grain Firmware
Volume containers are also used extensively in order to increase leverage,
scalability, and large grain FV container updates.

An important concept is that the minimum platform is defined with a mix of
solutions for modularity, but that said modularity will be flexible. It is
intended that products will be able to scale from fully statically-linked
embedded solutions to fully dynamically-linked leveraged validation solutions
as they reach the end of Stage VII optimization activities. These advanced
solutions can be considered derivatives of the platform architecture and should
not undermine the strategic objectives of transparency and quality, nor the
more tactical objectives of structure, consistency, cohesion, coupling, and
compatibility.
