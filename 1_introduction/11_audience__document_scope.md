<!--- @file
  1.1 Audience / Document scope

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

## 1.1 Audience / Document scope

The audience for this document includes UEFI firmware architecture,
development, validation, and enabling engineers.

The UEFI Forum and the TianoCore.org EDK II specifications provide tremendous
flexibility and extensibility. The Minimum Platform Architecture is intended to
introduce interfaces and structure so that platforms are consistent and thus
approachable by engineers from across the ecosystem. The minimal platform
specifically refers to a platform layer within a multi-layer solution; its
scope and therefore this specification defines this layer and its dependencies.
The minimal platform is a single code package used as-is from open source
similar to MDE Module package usage. By using this platform as a base, the
fundamental boot flow is consistent, well-documented, and visible across the
UEFI community.

This approach does not rule out innovation and customization. The platform
calls two primary sets of external APIs throughout the boot, for board and
chipset initialization. These APIs are considered dependencies, and therefore
are defined in this specification. The implementation of these APIs is expected
to vary based on unique board and chipset requirements. Furthermore, the
minimal platform can be arbitrarily extended through a simple and modular
advanced feature design.

The Minimum Platform Architecture enables scalability from pre-silicon
validation activities, to final product shipment, to derivative product use.
The Minimum Platform Architecture should enable engineering activities from all
segments: from high-touch Intel supported OEMs to individual makers with
previous UEFI experience but no direct support from Intel.
