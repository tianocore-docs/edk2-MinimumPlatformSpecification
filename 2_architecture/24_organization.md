<!--- @file
  2.4 Organization

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

## 2.4 Organization

The architecture makes use of four primary classifications of code that are
generally instantiated in different EDK II packages.

* **Common** (EDK II) is code that does not have any direct HW requirements other
  than the basics required to execute machine code on the processor (stack,
  memory, IA registers, etc).
    * **Producer(s): TianoCore.org**


* **Silicon**, also often called hardware code, has some tie to a specific class
  of physical hardware. Sometimes governed by industry standards, sometimes
  proprietary. Silicon or hardware code is usually not intended to have
  multiple implementations for the same hardware.
    * **Producer(s): Silicon vendor**


* **Platform** defines the actions needed to enable a specific platform's
  capabilities. In this architecture, capabilities are divided into mandatory
  and advanced features. Mandatory features are enabled in stages prior to
  Stage VI. Advanced features are enabled in Stage VI and later.
    * **Minimum Platform Producer(s): TianoCore.org**
    * **Advance Feature Producer(s): TianoCore.org, OEM, BIOS vendor**


* **Board** packages contains board specific code for one or more motherboards.
    * **Producer(s):** Device manufacturer, BIOS vendor, Board user


The architecture is designed to support a maintainer ownership model. For
example, board developers should not directly modify (fork) the platform,
silicon, or common code. More details on conventional usage of the package
classifications can be found in supplemental literature from UEFI Forum,
TianoCore.org, and others.

For the purposes of this document, the board package is considered an
integration point of the firmware image in addition to providing board-specific
functionality. The silicon package provides supported silicon initialization
support for one or more silicon products. The minimum platform package
represents common elements of this architecture that may depend upon board and
silicon interfaces. In order to meet the security objectives of this
specification, the minimum platform package must not depend upon deprecated EDK
II packages. Other packages composed within the firmware solution described in
this specification should consist of widely known elements of the EDKII
ecosystem from TianoCore.org.

An example of a firmware stack compliant with this specification for three
classes of computer systems is shown in the below figure.

![Figure 3 Example of a Minimal Platform Firmware Stack](/media/2_architecture_example_of_a_minimal_platform_firmware_stack.png)
###### Figure 3 Example of a Minimal Platform Firmware Stack
