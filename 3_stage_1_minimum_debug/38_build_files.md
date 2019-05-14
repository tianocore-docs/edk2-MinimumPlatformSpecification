<!--- @file
  3.8 Build Files

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

## 3.8 Build Files

UEFI system firmware by nature is often constructed with a large number of
modules and components. EDK II modules are typically written to be generic and
reusable. As such, much of the build file content is the same for all
platforms. The platform architecture provides further structure and consistency
by defining dedicated build files that are exposed to all consumers of the
platform package. The modular separation of the build files is based on the
UEFI PI Architecture phases, the platform architecture stages, and optional
features. The board package is ultimately able to leverage as much of this
content as applicable for a given system. The build is coordinated by the board
package which should include standard build files from the minimum platform
package or other dependent packages such as a silicon package.

| `Name`                                                 | `Consumer` | `Standalone Buildable` | `FV Produced` | `Comments`                                                               |
| ------------------------------------------------------ | ---------- | ---------------------- | ------------- | ------------------------------------------------------------------------ |
| MinPlatformPkg<br />\Include\CoreCommonLib.dsc         | Board      | No                     | None          | Stage I-V common libraries                                               |
| MinPlatformPkg<br />\Include\CorePeiInclude.dsc        | Board      | No                     | None          | Combination of Stage I-V<br />that will be processed by compilation building  |
| MinPlatformPkg<br />\Include\CorePeiLib.dsc            | Board      | No                     | None          | Combination of Stage I-V<br />that will be processed by compilation building  |
| BoardPkg<br />\BoardName\BoardPkg.dsc                  | Build      | Yes                    | None          | Primary build file.                                                      |
| `Name`                                                 | `Consumer` | `Standalone Buildable` | `FV Produced` | `Comments`                                                               |
| MinPlatformPkg<br />\Include\CorePreMemoryInclude.fdf  | Board      | No                     | None          | Combination of Stage I-II<br />that will be processed by compilation building |
| BoardPkg<br />\BoardName\BoardPkg.fdf                  | Build      | Yes                    | Yes           | Combination of Stage I-V<br />that will be processed by compilation building  |

###### Table 13 Stage I Build Files
