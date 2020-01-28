<!--- @file
  Appendix A.3 BDS Hook Points

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

## A.3 BDS Hook Points

**BDS Hook Point Summary**

Four new event signal groups are defined that will be signaled at the point
shown in Table 16 Event groups as described in the UEFI specification are
collections of events identified by a shared EFI_GUID that when one member
event group is signaled, all other event groups are signed and their individual
notification actions are taken. These event groups should be used in
combination with the pre-existing notification mechanisms: signal of
gEfiEndOfDxeEventGroupGuid and installation of the
gEfiPciEnumerationCompleteProtocolGuid or gEfiDxeSmmReadyToLockProtocolGuid.
Preference should always be given to the notification points defined outside
this specification to make code dependent upon the notification as portable as
possible.

**PlatformBootManagerBeforeConsole ()**
[1] *Event: PCI enumeration complete - Install gEfiPciEnumerationCompleteProtocolGuid*
    * Minimum Platform action(s) performed:
        * Trusted consoles added

[2] *Event: SignalBeforeConsoleAfterTrustedConsole*
    * Minimum Platform action(s) performed:
        * Enumerate USB keyboard
        * Connect controller for trusted graphics console
        * Register default boot option (UEFI shell)
        * Register static hot keys (F2/F7)
        * Process TCG Physical Presence
        * Process TCG MOR
        * Perform memory test

[3] *Event: SignalBeforeConsoleBeforeEndOfDxe*
    * Minimum Platform action(s) performed:
        * None

[4] *Event: End of DXE - Signal gEfiEndOfDxeEventGroupGuid*
    * Minimum Platform action(s) performed:
        * None

[5] *Event: SmmReadyToLock: Signal gEfiDxeSmmReadyToLockProtocolGuid*
    * Minimum Platform action(s) performed:
        * Dispatch deferred 3rd party images (e.g. UEFI OPROMs)

**PlatformBootManagerAfterConsole ()**
[1] Invoke ConnectSequence ()

[2] *Event: Signal AfterConsoleReadyBeforeBootOption*
    * Minimum Platform action(s) performed:
        * Print hot key message to output console ("Press F7 for BootMenu!")
        * Refresh all boot options
        * Sort load option variables

![Full BDS Hook Point Map](/media/10_bds_hook_point_summary.png)
###### Figure 10 Full BDS Hook Point Map
