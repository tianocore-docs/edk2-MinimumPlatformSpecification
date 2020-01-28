<!--- @file
  2 Architecture

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

# 2 Architecture

The Minimum Platform Architecture is structured around required functionality
over time. As such, the key elements of architecture and design
(flows, interfaces, etc) are organized into a staged architecture, where each
stage will have requirements and functionality that lead to specific uses.
Stages build upon prior stages with extensibility to meet silicon, platform,
or board requirements.

Early in a development cycle, engineering is focused on creating the platform
and acquiring basic functionality. This can be pursued within simulation and
emulation environments, or on real hardware. This often includes creating a
new set of silicon and platform source code that handles the basic differences
between the new target and prior solutions. Often this entails reuse of the
prior generation silicon support and existing feature sets.

Later development engineering effort is focused on enabling the full range
of functionality, supporting all deltas in the new platform - typically in
the form of reference designs and lead products. Next, platform development
is focused on scaling.  This involves customer enabling and aligning products
for time-to-market and silicon roadmaps. Finally, there is sustaining,
maintenance, and derivatives activity. These are characterized by smaller
changes to existing production-worthy solutions, repurposing them
opportunistically.

![Minimum Platform Architecture Overview](/media/1_architecture_minimum_platform_architecture_overview.png "Minimum Platform Architecture Overview")
###### Figure 1 Minimum Platform Architecture Overview

Figure 1 shows the basic Minimum Platform Architecture. The enabling steps
for a Minimum Platform solution should occur in the following order to add
complexity over time, and only where it is necessary. This progression from
minimum required to more full-featured permeates the design of the boot flow,
modules implemented, and collection of components into firmware volumes.

1. **Develop a board solution around the minimum platform.** This involves
  implementing the essential board information and initialization defined in
  the Minimum Platform board API.
2. **Add silicon initialization support.** For many silicon vendors this
   will be accomplished through the use of binary blobs with well-defined
   interfaces. In any case, the silicon initialization invocation is performed
   from the board code.
3. **Add advanced features,** which are typically implemented in the form of
   source code designed to be generically plugged into a large number of diverse
   system types.
4. **Add product-specific features** that are required for product initialization.
   This support is not part of essential board organization or maintained as a
   generic advanced feature. It is enabled in the advanced feature stage.

![Figure 2 Minimum Platform Architecture High Level Sequence](/media/1_architecture_minimum_platform_architecture_high_level_sequence.png)
###### Figure 2 Minimum Platform Architecture High Level Sequence

Figure 2 shows the same basic idea can be represented as a Venn diagram with
three fundamental steps.

This architecture is reflected in these areas:
* Source code in modules, packages, and resulting binary components
* Execution in control, data, error, and debug flows
* Functionality as solutions evolve from initial to complete
* Scaling from silicon development to products
