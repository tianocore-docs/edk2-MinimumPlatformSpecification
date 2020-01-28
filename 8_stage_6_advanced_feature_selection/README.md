<!--- @file
  8 Stage VI: Advanced Feature Selection

  Copyright (c) 2019 - 2020, Intel Corporation. All rights reserved.<BR>

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

## 8.1 Overview

Advanced features are non-essential features. Essential features are defined as
being support required to meet earlier stage boot objectives. An advanced
feature must be implemented as highly cohesive and stand-alone software to only
support a specific feature. Modularizing such features, reducing dependencies
on other advanced features, and eliminating dependencies on specific
implementations of other advanced features is critical and results in a variety
of benefits:

* The minimum platform serves as a basic enabling vehicle ready to support
  various roles for a given hardware platform. This yields a minimum platform
  solution that is open to extension but closed for modification.

* System power-on is simplified because unnecessary code paths and silicon
  paths can be avoided or deferred.

* Platforms can be composed in a more modular and portable manner allowing
  generic advanced features to be readily shared among participants.

* Feature adoption benefits from modular design that is simple to maintain.

Organizing advanced features in the platform architecture enables better
realization of the benefits in UEFI specification compliant firmware with
highly cohesive and lowly coupled component interactions.

This chapter provides guidance on how to design and integrate advanced features.
The source code layout and other maintenance details are outside the scope of this
specification.

The core advanced feature requirements that must be met:
* _Cohesive_, the feature should not contain any functionality unrelated to the feature.
* _Complete_, the feature must have a complete design that minimizes dependencies. A feature package cannot directly
  depend on another feature package.
* _Easy to Integrate_, the feature should expose well-defined software interfaces to use and configure the feature.
  * It should also present a set of simple and well-documented standard EDK II configuration options such as PCDs to
  configure the feature.
  * In general, features should be self-contained and started by the dispatcher. The board firmware should
    be required to perform as few steps as possible to enable the feature.
  * All features are required to have a feature enable PCD (`PcdFeatureEnable`). Any effort to enable the feature
    besides this PCD should be carefully considered. Default configuration values should apply to the common case.
* _Portable_, the feature is not allowed to depend on other advanced feature or board source code packages. For example,
  if Feature A depends on output Feature B, a board integration module should use a generic interface in Feature A
  to get the output and pass it to a generic interface in Feature B. Structures should not be shared between feature
  packages. Most structures should be defined in a common package such as MdePkg if the structure is industry standard,
  IntelSiliconPkg if the structure is specific to Intel silicon initialization, etc. Feature-specific structures are
  of course allowed to be defined within a feature package and used by libraries and modules in that package.
* _Self Documenting_, the feature should follow software best practices to allow others to debug the code and
  contribute changes. In addition to source code, advanced features must have a Readme.md with sufficient
  information for a newcomer to understand the feature.
* _Single Instance_, the feature should not have more than one instance of a source solution. If an existing feature
  package does not solve a specific instance of a problem for the feature, the feature package should be re-worked
  to consider new requirements instead of duplicating feature code.

### 8.1.1 Major Execution Activities

| `Stage VI Modules`                    |
| ------------------------------------- |
| Execute the Enabled Advanced Features |

The number of embedded features must be minimized in order to support the
broadest compatibility of the minimal platform. Features should be designed to
define an API that can be used to integrate the feature into generic platform
configurations. The feature source code should never be modified to absorb
details of a specific platform or board.
