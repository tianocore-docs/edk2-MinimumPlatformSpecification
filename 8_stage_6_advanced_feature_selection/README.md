<!--- @file
  8 Stage VI: Advanced Feature Selection

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

This chapter provides guidance and some brief informative examples on how to
define and integrate advanced features. These example are not implied as a
mandatory requirement and only serve for information purposes. Advanced
features are not required to be implemented with any particular design allowing
flexibility for various organizations and projects to develop advanced features
that meet their overall firmware design objectives. Furthermore, the source
code layout and other maintenance details are outside the scope of this
specification.

The core advanced feature requirements that must be met:
* Advanced features must be a complete feature.
    * Fractions of functionality such as libraries that plug into a module defined in another package are not features.
* Advanced features may only depend on packages in edk2.
    * DEC files outside edk2 shall not be referenced in an advanced feature.
* Advanced features shall be organized in cohesive packages related to the feature domain.
    * *Informative examples: DebugFeaturePkg, IoFeaturePkg, PowerManagementFeaturePkg*
    * New feature packages must be proposed as an RFC to the community mailing list.
    The proposal shall include the package name, purpose, maintainers and reviewers, 
    and identify any pre-existing packages that will be moved to the feature. The 
    maintainers of any packages affected by the proposal must be included in the RFC 
    notification list. If the feature proposal is well received, it must be ratified 
    in the TianoCore Design Meeting. If approved, the RFC author should follow through 
    to implement the change.
* Advanced features must be mutually independent.
* Advanced features must support being enabled on an individual basis when Stage VI is enabled.
* Advanced features must be distributed in a binary independent manner such that the feature 
  can be added and removed at the binary level (recommendation is with a single FeaturePcd).
* Advanced features must be self-documenting. Each feature must include a ReadMe.md in the
  root directory that describes the feature using the template described in this section.
* Advanced features must fail in a graceful and developer friendly manner. 

For all advanced features, complete and maintain a human readable copy of the 
Advanced Feature Template provided in this chapter.

### 8.1.1 Major Execution Activities

| `Stage VI Modules`                    |
| ------------------------------------- |
| Execute the Enabled Advanced Features |

### 8.1.2 Examples

Provided below are high-level examples of advanced features. The number of
"advanced features" in a platform should be limited to what is required and
reasonable to reduce the required level of design and validation complexity.

* Core Features
    * Signed Capsule update
    * Signed Recovery
    * Source Debug Enable
    * NVMe (secondary storage)
    * eMMC (secondary storage)
    * S3 resume
    * Network

* Platform Features
    * SMBIOS
    * Intel&reg; Active Management Technology (AMT)

* Board Features
    * SMBIOS
    * EC
    * Setup (policy)

In this chapter, two advanced features are described in detail and each of them
represents a typical type of advanced feature, fully modular and embedded.
***
**Note:** The network stack and signed capsule update examples are incomplete and
no longer accurately represent the latest vision for advanced features. These sections
will be updated to provide more accurate examples in the future.
***
#### 8.1.2.1 Network stack - Fully Modular Feature

For this type of feature, all the necessary code can be included in the
platform build by defining the necessary sources the .dsc/.fdf. The feature
enabling is modular enough to support binary enabling as there are no strong
board dependencies.

In this Network stack case, the necessary changes are:

* Include EDK II core network related modules in .dsc/.fdf
* Include Option Rom for the network device (e.g. Intel&reg; NIC) in the flash
  image

#### 8.1.2.2 Signed Capsule update - Embedded Feature

For this type of feature, in addition to the necessary code/module inclusion,
existing code that supports this feature should be embedded in the minimum
platform code.

In the signed capsule update case, the necessary changes are:

* Include necessary modules in .dsc/.fdf
* Define the necessary library class implementation in .dsc
* Use PCD or other configuration method to enable the feature in the existing
  code

The number of embedded features must be minimized in order to support the
broadest compatibility of the minimal platform. Features should be designed to
define an API that can be used to integrate the feature into generic platform
configurations. The feature source code should never be modified to absorb
details of a specific platform or board.
