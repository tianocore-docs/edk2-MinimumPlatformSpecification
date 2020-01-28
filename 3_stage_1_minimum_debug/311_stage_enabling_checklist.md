<!--- @file
  3.11 Stage Enabling Checklist

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

## 3.11 Stage Enabling Checklist

The following steps should be followed to enable a board for Stage I.

1. Copy the EDK II packages locally to the workspace.

2. Select an appropriate silicon initialization solution such as Intel&reg; FSP.

3. Review the requirements for the silicon initialization solution.

4. Gather the silicon initialization requirements for the given board.

5. Customize the silicon initialization solution to configure the system to the
   board-specific requirements.

    1. For Intel&reg; FSP, this includes setting minimal policy configuration.

    2. For other silicon solutions, similar parameter customization may be
       needed if the silicon solution is not written for a particular system
       design.

6. Determine other firmware and software components required for the system to
   function properly.

    1. For an Intel platform, this may include firmware images such as the
       appropriate microcode patch, EC firmware image, power management
       controller firmware, and others.

    2. Additional third-party add-in components such as specific UEFI drivers
       may also be required.

7. Determine board-specific information required to fetch code and show debug
   output.

    1. This includes details such as the NVRAM layout and strap information.

8. Copy a reference *Generation*OpenBoardPkg/*BoardXXX* and update the
   board interfaces in Required Functions.

    1. Add serial port initialization code in `PlatformHookSerialPortInitialize ()` at *Board*Pkg/Library/BasePlatformHookLib.

        1. This is SIO related code.

    2. Add Board detection code in `BoardDetect ()`,

*Board*Pkg/BoardInitLib/PeiBoardXXXInitPreMemoryLib.c`

9. If the project only supports one board, this function can return directly.

1. Add Board pre-memory debug initialization code in `BoardDebugInit ()`,
   *Board*Pkg/BoardInitLib/PeiBoardXXXInitPreMemoryLib.c.

    1. This is for debug channel related initialization.

1. Audit *Board*Pkg/Stage1.dsc, ensure all PCDs in the Configuration section
   are correct for your board.

    1. Set `gMinPlatformPkgTokenSpaceGuid.PcdBootStage` = 1

    2. Follow "Debug Lib Selection" to enable serial debug capability.

2. Audit all other PCD settings in the board DSC file to verify the values are
   correct for your board.

3. Verify the flash layout is compliant with this specification.

4. Verify the required binaries will be included in the image produced in the
   build.

5. Verify the code execution path for Stage I will only perform the actions
   required to achieve debug output.

6. Boot the system, collect the debug log, and verify the test point results
   defined in the Test Point section are correct.
