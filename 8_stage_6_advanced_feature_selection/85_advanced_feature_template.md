<!--- @file
  8.5 Advanced Feature Template

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

## 8.5 Advanced Feature Template

Define an advanced feature using the following template. The template is
roughly equivalent to preceding stage description sections within this
document, with the addition of common optimization opportunities. This
template should be included in feature review and placed in the feature
root directory as README.md.

| `Overview`                     | `An overview of the feature`                                                                                                                                     |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Firmware Volumes**           | The binary containers needed for the feature.                                                                                                                    |
| **Modules**                    | The EDK II component binaries and static libraries required.                                                                                                     |
| **Required Functions**         | Functions that are useful for understanding, porting, or debugging the feature and how these key functions are integrated into the Stage I-V required functions. |
| **Configuration**              | The configurable parameters for a given feature.                                                                                                                 |
| **Data Flows**                 | The architecturally defined data structures and flows for a given feature.                                                                                       |
| **Control Flows**              | Key control flows for the feature.                                                                                                                               |
| **Build Files**                | The DSC/FDF for integrating the feature.                                                                                                                         |
| **Test Point Results**         | The test that can verify porting is complete for the feature.                                                                                                    |
| **Functional Exit Criteria**   | The testable functionality for the feature.                                                                                                                      |
| **Feature Enabling Checklist** | The required activities to achieve desired functionality for the feature.                                                                                        |
| **Common Optimizations**       | Common size or performance tuning options for this feature.                                                                                                      |

###### Table 70 Advanced Feature Template
