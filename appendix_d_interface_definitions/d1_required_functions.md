<!--- @file
  Appendix D.1 Required Functions

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

## D.1 Required Functions

### D.1.1 BoardPorting.SEC

#### D.1.1.1 ResetHandler (*)
```
; For IA32, the reset vector must be at 0xFFFFFFF0, i.e., 4G-16 byte
; Execution starts here upon power-on/platform-reset.
;
ResetHandler:
    nop
    nop
ApStartup:
    ;
    ; Jmp Rel16 instruction
    ; Use machine code directly in case of the assembler optimization
    ; SEC entry point relative address will be fixed up by some build tool.
    ;
    ; Typically, SEC entry point is the function _ModuleEntryPoint() defined in
    ; SecEntry.asm
    ;
    DB      0e9h
    DW      -3
```

### D.1.2 BoardPorting.PEI

#### D.1.2.1 ReportPreMemFv

```c
VOID
ReportPreMemFv (
  VOID
  );
```

#### D.1.2.2 BoardDetect

```c
EFI_STATUS
EFIAPI
BoardDetect (
  VOID
  );
```

#### D.1.2.3 BoardDebugInit

```c
EFI_STATUS
EFIAPI
BoardDebugInit (
  VOID
  );
```

#### D.1.2.4 PlatformHookSerialPortInitialize

```c
/**
  Performs platform specific initialization required for the CPU to access
  the hardware associated with a SerialPortLib instance.  This function does
  not initialize the serial port hardware itself.  Instead, it initializes
  hardware devices that are required for the CPU to access the serial port
  hardware.  This function may be called more than once.

  @retval RETURN_SUCCESS       The platform specific initialization succeeded.
  @retval RETURN_DEVICE_ERROR  The platform specific initialization could not be completed.

**/
RETURN_STATUS
EFIAPI
PlatformHookSerialPortInitialize (
  VOID
  );
```

#### D.1.2.5 BoardBootModeDetect

```c
EFI_BOOT_MODE
EFIAPI
BoardBootModeDetect (
  VOID
  );
```

#### D.1.2.6 BoardInitBeforeMemoryInit

```c
EFI_STATUS
EFIAPI
BoardInitBeforeMemoryInit (
  VOID
  );
```

#### D.1.2.7 SiliconPolicyUpdatePreMemory

```c
/**
  Performs silicon pre-memory policy update.

  The meaning of Policy is defined by silicon code.
  It could be the raw data, a handle, a PPI, etc.

  The input Policy must be returned by SiliconPolicyDonePreMemory().

  1) In FSP path, the input Policy should be FspmUpd.
  A platform may use this API to update the FSPM UPD policy initialized
  by the silicon module or the default UPD data.
  The output of FSPM UPD data from this API is the final UPD data.

  2) In non-FSP path, the board may use additional way to get
  the silicon policy data field based upon the input Policy.

  @param[in, out] Policy       Pointer to policy.

  @return the updated policy.
**/
VOID *
EFIAPI
SiliconPolicyUpdatePreMemory (
  IN OUT VOID *Policy
  );
```

#### D.1.2.8 ReportPostMemFv

```c
VOID
ReportPostMemFv (
  VOID
  );
```

#### D.1.2.9 BoardInitAfterMemoryInit

```c
EFI_STATUS
EFIAPI
BoardInitAfterMemoryInit (
  VOID
  );
```

#### D.1.2.10 SetCacheMtrrAfterMemoryDiscovered

_**TODO**: Add prototype_

#### D.1.2.11 BoardInitBeforeSiliconInit

```c
EFI_STATUS
EFIAPI
BoardInitBeforeSiliconInit (
  VOID
  );
```

#### D.1.2.12 SiliconPolicyUpdatePostMemory

```c
/**
  Performs silicon post-memory policy update.

  The meaning of Policy is defined by silicon code.
  It could be the raw data, a handle, a PPI, etc.

  The input Policy must be returned by SiliconPolicyDonePostMemory().

  1) In FSP path, the input Policy should be FspsUpd.
  A platform may use this API to update the FSPS UPD policy initialized
  by the silicon module or the default UPD data.
  The output of FSPS UPD data from this API is the final UPD data.

  2) In non-FSP path, the board may use additional way to get
  the silicon policy data field based upon the input Policy.

  @param[in, out] Policy       Pointer to policy.

  @return the updated policy.
**/
VOID *
EFIAPI
SiliconPolicyUpdatePostMemory (
  IN OUT VOID *Policy
  );
```

#### D.1.2.13 BoardInitAfterSiliconInit

```c
EFI_STATUS
EFIAPI
BoardInitAfterSiliconInit (
  VOID
  );
```

#### D.1.2.14 SetCacheMtrrAfterEndOfPei

```c
/**
  Update MTRR setting and set write back as default memory attribute.

  @retval  EFI_SUCCESS  The function completes successfully.
  @retval  Others       Some error occurs.
**/
EFI_STATUS
EFIAPI
SetCacheMtrrAfterEndOfPei (
  VOID
  )
```

### D.1.3 BoardPorting.DXE

#### D.1.3.1 SiliconPolicyUpdateLate

```c
/**
  Performs silicon late policy update.

  The meaning of Policy is defined by silicon code.
  It could be the raw data, a handle, a Protocol, etc.

  The input Policy must be returned by SiliconPolicyDoneLate().

  In FSP or non-FSP path, the board may use additional way to get
  the silicon policy data field based upon the input Policy.

  @param[in, out] Policy       Pointer to policy.

  @return the updated policy.
**/
VOID *
EFIAPI
SiliconPolicyUpdateLate (
  IN OUT VOID *Policy
  );
```

#### D.1.3.2 PlatformBootManagerBeforeConsole (*)

```c
/**
  Do the platform specific action before the console is connected.

  Such as:
    Update console variable;
    Register new Driver#### or Boot####;
    Signal ReadyToLock event.
**/
VOID
EFIAPI
PlatformBootManagerBeforeConsole (
  VOID
  );
```

#### D.1.3.3 BoardInitAfterPciEnumeration

```c
EFI_STATUS
EFIAPI
BoardInitAfterPciEnumeration (
  VOID
  );
```

#### D.1.3.4 PlatformBootManagerAfterConsole(*)

```c
/**
  Do the platform specific action after the console is connected.

  Such as:
    Dynamically switch output mode;
    Signal console ready platform customized event;
    Run diagnostics like memory testing;
    Connect certain devices;
    Dispatch additional option roms.
**/
VOID
EFIAPI
PlatformBootManagerAfterConsole (
  VOID
  );
```

#### D.1.3.5 BoardInitReadyToBoot

```c
EFI_STATUS
EFIAPI
BoardInitReadyToBoot (
  VOID
  );
```

D.1.3.6 PlatformCreateAcpiTable

_**TODO**: Add prototype_

D.1.3.7 PlatformUpdateAcpiTable

_**TODO**: Add prototype_

D.1.3.8 PlatformInstallAcpiTable

_**TODO**: Add prototype_

#### D.1.3.9 BoardInitEndOfFirmware

```c
EFI_STATUS
EFIAPI
BoardInitEndOfFirmware (
  VOID
  );
```

### D.1.4 BoardPorting.SMM

D.1.4.1 BoardEnableAcpiCallback

_**TODO**: Add prototype_

### D.1.5 SiliconPorting.SEC

D.1.5.1 TempRamInit

_**TODO**: Add prototype_

### D.1.6 SiliconPorting.PEI

#### D.1.6.1 SiliconPolicyInitPreMemory

```c
/**
  Performs silicon pre-memory policy initialization.

  The meaning of Policy is defined by silicon code.
  It could be the raw data, a handle, a PPI, etc.

  The returned data must be used as input data for SiliconPolicyDonePreMemory(),
  and SiliconPolicyUpdateLib.SiliconPolicyUpdatePreMemory().

  1) In FSP path, the input Policy should be FspmUpd.
  Value of FspmUpd has been initialized by FSP binary default value.
  Only a subset of FspmUpd needs to be updated for different silicon sku.
  The return data is same FspmUpd.

  2) In non-FSP path, the input policy could be NULL.
  The return data is the initialized policy.

  @param[in, out] Policy       Pointer to policy.

  @return the initialized policy.
**/
VOID *
EFIAPI
SiliconPolicyInitPreMemory (
  IN OUT VOID *Policy OPTIONAL
  );
```

#### D.1.6.2 SiliconPolicyDonePreMemory

```c
/*
  The silicon pre-memory policy is finalized.
  Silicon code can do initialization based upon the policy data.

  The input Policy must be returned by SiliconPolicyInitPreMemory().

  @param[in] Policy       Pointer to policy.

  @retval RETURN_SUCCESS The policy is handled consumed by silicon code.
*/
RETURN_STATUS
EFIAPI
SiliconPolicyDonePreMemory (
  IN VOID *Policy
  );
```

#### D.1.6.3 MemoryInit

```c
/**
  This function
    1. Calling MRC to initialize memory.
    2. Install EFI Memory.
    3. Capsule coalesce if capsule boot mode.
    4. Create HOB of system memory.

  @param  PeiServices Pointer to the PEI Service Table

  @retval EFI_SUCCESS If it completes successfully.

**/
EFI_STATUS
MemoryInit (
  IN EFI_PEI_SERVICES          **PeiServices
  );
```

#### D.1.6.4 SiliconPolicyInitPostMemory

```c
/**
  Performs silicon post-memory policy initialization.

  The meaning of Policy is defined by silicon code.
  It could be the raw data, a handle, a PPI, etc.

  The returned data must be used as input data for SiliconPolicyDonePostMemory(),
  and SiliconPolicyUpdateLib.SiliconPolicyUpdatePostMemory().

  1) In FSP path, the input Policy should be FspsUpd.
  Value of FspsUpd has been initialized by FSP binary default value.
  Only a subset of FspsUpd needs to be updated for different silicon sku.
  The return data is same FspsUpd.

  2) In non-FSP path, the input policy could be NULL.
  The return data is the initialized policy.

  @param[in, out] Policy       Pointer to policy.

  @return the initialized policy.
**/
VOID *
EFIAPI
SiliconPolicyInitPostMemory (
  IN OUT VOID *Policy OPTIONAL
  );
```

#### D.1.6.5 SiliconPolicyDonePostMemory

```c
/*
  The silicon post-mem policy is finalized.
  Silicon code can do initialization based upon the policy data.

  The input Policy must be returned by SiliconPolicyInitPostMemory().

  @param[in] Policy       Pointer to policy.

  @retval RETURN_SUCCESS The policy is handled consumed by silicon code.
*/
RETURN_STATUS
EFIAPI
SiliconPolicyDonePostMemory (
  IN VOID *Policy
  );
```

D.1.6.6 SiliconInit

_**TODO**: Add prototype_

### D.1.7 SiliconPorting.DXE

#### D.1.7.1 SiliconPolicyInitLate

```c
/**
  Performs silicon late policy initialization.

  The meaning of Policy is defined by silicon code.
  It could be the raw data, a handle, a protocol, etc.

  The returned data must be used as input data for SiliconPolicyDoneLate(),
  and SiliconPolicyUpdateLib.SiliconPolicyUpdateLate().

  In FSP or non-FSP path, the input policy could be NULL.
  The return data is the initialized policy.

  @param[in, out] Policy       Pointer to policy.

  @return the initialized policy.
**/
VOID *
EFIAPI
SiliconPolicyInitLate (
  IN OUT VOID *Policy
  );
```

#### D.1.7.2 SiliconPolicyDoneLate

```c
/*
  The silicon late policy is finalized.
  Silicon code can do initialization based upon the policy data.

  The input Policy must be returned by SiliconPolicyInitLate().

  @param[in] Policy       Pointer to policy.

  @retval RETURN_SUCCESS The policy is handled consumed by silicon code.
*/
RETURN_STATUS
EFIAPI
SiliconPolicyDoneLate (
  IN VOID *Policy
  );
```

D.1.7.3 SiliconInitAfterPciEnumeration

_**TODO**: Add prototype_

### D.1.8 SiliconPorting.SMM

#### D.1.8.1 PchSmmCoreDispatcher

```c
/**
  The callback function to handle subsequent SMIs.  This callback will be called by SmmCoreDispatcher.

  @param[in] SmmImageHandle             Not used
  @param[in] PchSmmCore                 Not used
  @param[in, out] CommunicationBuffer   Not used
  @param[in, out] SourceSize            Not used

  @retval EFI_SUCCESS                   Function successfully completed
**/
EFI_STATUS
EFIAPI
PchSmmCoreDispatcher (
  IN       EFI_HANDLE         SmmImageHandle,
  IN CONST VOID               *PchSmmCore,
  IN OUT   VOID               *CommunicationBuffer,
  IN OUT   UINTN              *SourceSize
  );
```

### D.1.9 Test.DXE

#### D.1.9.1 ExitPmAuth

```c
VOID
ExitPmAuth (
  VOID
  );
```

### D.1.10 Debug.SEC

#### D.1.10.1 SecStartup (*)

```c
/**
  Entry point to the C language phase of SEC. After the SEC assembly
  code has initialized some temporary memory and set up the stack,
  the control is transferred to this function.

  @param SizeOfRam           Size of the temporary memory available for use.
  @param TempRamBase         Base address of temporary ram
  @param BootFirmwareVolume  Base address of the Boot Firmware Volume.
**/
VOID
EFIAPI
SecStartup (
  IN UINT32                   SizeOfRam,
  IN UINT32                   TempRamBase,
  IN VOID                     *BootFirmwareVolume
  );
```

#### D.1.10.2 SecStartupPhase2 (*)

```c
/**
  Caller provided function to be invoked at the end of InitializeDebugAgent().

  Entry point to the C language phase of SEC. After the SEC assembly
  code has initialized some temporary memory and set up the stack,
  the control is transferred to this function.

  @param[in] Context    The first input parameter of InitializeDebugAgent().

**/
VOID
NORETURN
EFIAPI
SecStartupPhase2 (
  IN VOID                     *Context
  );
```

### D.1.11 Debug.PEI

#### D.1.11.1 PeiCore (*)

```c
/**
  This routine is invoked by main entry of PeiMain module during transition
  from SEC to PEI. After switching stack in the PEI core, it will restart
  with the old core data.

  @param SecCoreDataPtr  Points to a data structure containing information about the PEI core's operating
                         environment, such as the size and location of temporary RAM, the stack location and
                         the BFV location.
  @param PpiList         Points to a list of one or more PPI descriptors to be installed initially by the PEI core.
                         An empty PPI list consists of a single descriptor with the end-tag
                         EFI_PEI_PPI_DESCRIPTOR_TERMINATE_LIST. As part of its initialization
                         phase, the PEI Foundation will add these SEC-hosted PPIs to its PPI database such
                         that both the PEI Foundation and any modules can leverage the associated service
                         calls and/or code in these early PPIs
  @param Data            Pointer to old core data that is used to initialize the
                         core's data areas.
                         If NULL, it is first PeiCore entering.

**/
VOID
EFIAPI
PeiCore (
  IN CONST EFI_SEC_PEI_HAND_OFF        *SecCoreDataPtr,
  IN CONST EFI_PEI_PPI_DESCRIPTOR      *PpiList,
  IN VOID                              *Data
  );
```

#### D.1.11.2 PeiDispatcher (*)

```c
/**
  Conduct PEIM dispatch.

  @param SecCoreData     Pointer to the data structure containing SEC to PEI handoff data
  @param PrivateData     Pointer to the private data passed in from caller

**/
VOID
PeiDispatcher (
  IN CONST EFI_SEC_PEI_HAND_OFF  *SecCoreData,
  IN PEI_CORE_INSTANCE           *PrivateData
  );
```

#### D.1.11.3 SecTemporaryRamDone(*)

```c
/**
  TemporaryRamDone() disables the use of Temporary RAM. If present, this service is invoked
  by the PEI Foundation after the EFI_PEI_PERMANANT_MEMORY_INSTALLED_PPI is installed.

  @retval EFI_SUCCESS           Use of Temporary RAM was disabled.
  @retval EFI_INVALID_PARAMETER Temporary RAM could not be disabled.

**/
EFI_STATUS
EFIAPI
SecTemporaryRamDone (
  VOID
  );
```

#### D.1.11.4 DxeLoadCore (*)

```c
/**
   Main entry point to last PEIM

   @param This          Entry point for DXE IPL PPI
   @param PeiServices   General purpose services available to every PEIM.
   @param HobList       Address to the Pei HOB list

   @return EFI_SUCCESS              DXE core was successfully loaded.
   @return EFI_OUT_OF_RESOURCES     There are not enough resources to load DXE core.

**/
EFI_STATUS
EFIAPI
DxeLoadCore (
  IN CONST EFI_DXE_IPL_PPI *This,
  IN EFI_PEI_SERVICES      **PeiServices,
  IN EFI_PEI_HOB_POINTERS  HobList
  );
```

### D.1.12 Debug.DXE
```

#### D.1.12.1 DxeMain (*)

```c
/**
  Main entry point to DXE Core.

  @param  HobStart               Pointer to the beginning of the HOB List from PEI.

  @return This function should never return.

**/
VOID
EFIAPI
DxeMain (
  IN  VOID *HobStart
  );
```

#### D.1.12.2 CoreStartImage (*)

```c
/**
  Transfer control to a loaded image's entry point.

  @param  ImageHandle             Handle of image to be started.
  @param  ExitDataSize            Pointer of the size to ExitData
  @param  ExitData                Pointer to a pointer to a data buffer that
                                  includes a Null-terminated string,
                                  optionally followed by additional binary data.
                                  The string is a description that the caller may
                                  use to further indicate the reason for the
                                  image's exit.

  @retval EFI_INVALID_PARAMETER   Invalid parameter
  @retval EFI_OUT_OF_RESOURCES    No enough buffer to allocate
  @retval EFI_SECURITY_VIOLATION  The current platform policy specifies that the image should not be started.
  @retval EFI_SUCCESS             Successfully transfer control to the image's
                                  entry point.

**/
EFI_STATUS
EFIAPI
CoreStartImage (
  IN EFI_HANDLE  ImageHandle,
  OUT UINTN      *ExitDataSize,
  OUT CHAR16     **ExitData  OPTIONAL
  );
```

#### D.1.12.3 CoreAllEfiServicesAvailable (*)

```c
/**
  Return TRUE if all AP services are available.

  @retval EFI_SUCCESS    All AP services are available
  @retval EFI_NOT_FOUND  At least one AP service is not available

**/
EFI_STATUS
CoreAllEfiServicesAvailable (
  VOID
  );
```

#### D.1.12.4 BdsEntry (*)

```c
/**

  Service routine for BdsInstance->Entry(). Devices are connected, the
  consoles are initialized, and the boot options are tried.

  @param This            Protocol Instance structure.

**/
VOID
EFIAPI
BdsEntry (
  IN  EFI_BDS_ARCH_PROTOCOL *This
  );
```

IN EFI_BDS_ARCH_PROTOCOL ``*This

`);`

#### D.1.12.5 EfiBootManagerDispatchDeferredImages (*)

```c
/**
  Dispatch the deferred images that are returned from all DeferredImageLoad instances.

  @retval EFI_SUCCESS       At least one deferred image is loaded successfully and started.
  @retval EFI_NOT_FOUND     There is no deferred image.
  @retval EFI_ACCESS_DENIED There are deferred images but all of them are failed to load.
**/
EFI_STATUS
EFIAPI
EfiBootManagerDispatchDeferredImages (
  VOID
  );
```

#### D.1.12.6 BootBootOptions(*)

```c
/**
  Attempt to boot each boot option in the BootOptions array.

  @param BootOptions       Input boot option array.
  @param BootOptionCount   Input boot option count.
  @param BootManagerMenu   Input boot manager menu.

  @retval TRUE  Successfully boot one of the boot options.
  @retval FALSE Failed boot any of the boot options.
**/
BOOLEAN
BootBootOptions (
  IN EFI_BOOT_MANAGER_LOAD_OPTION    *BootOptions,
  IN UINTN                           BootOptionCount,
  IN EFI_BOOT_MANAGER_LOAD_OPTION    *BootManagerMenu OPTIONAL
  );
```

#### D.1.12.7 EfiSignalEventReadyToBoot (*)

```c
/**
  Create, Signal, and Close the Ready to Boot event using EfiSignalEventReadyToBoot().

  This function abstracts the signaling of the Ready to Boot Event. The Framework moved
  from a proprietary to UEFI 2.0 based mechanism. This library abstracts the caller
  from how this event is created to prevent to code form having to change with the
  version of the specification supported.

**/
VOID
EFIAPI
EfiSignalEventReadyToBoot (
  VOID
  );
```

#### D.1.12.8 UefiMain (*)

```c
/**
  The entry point for the application.

  @param[in] ImageHandle    The firmware allocated handle for the EFI image.
  @param[in] SystemTable    A pointer to the EFI System Table.

  @retval EFI_SUCCESS       The entry point is executed successfully.
  @retval other             Some error occurs when executing this entry point.

**/
EFI_STATUS
EFIAPI
UefiMain (
  IN EFI_HANDLE        ImageHandle,
  IN EFI_SYSTEM_TABLE  *SystemTable
  );
```

#### D.1.12.9 CoreExitBootServices (*)

```c
/**
  Terminates all boot services.

  @param  ImageHandle            Handle that identifies the exiting image.
  @param  MapKey                 Key to the latest memory map.

  @retval EFI_SUCCESS            Boot Services terminated
  @retval EFI_INVALID_PARAMETER  MapKey is incorrect.

**/
EFI_STATUS
EFIAPI
CoreExitBootServices (
  IN EFI_HANDLE   ImageHandle,
  IN UINTN        MapKey
  );
```

#### D.1.12.10 RuntimeDriverSetVirtualAddressMap (*)

```c
/**
  Changes the runtime addressing mode of EFI firmware from physical to virtual.

  @param  MemoryMapSize   The size in bytes of VirtualMap.
  @param  DescriptorSize  The size in bytes of an entry in the VirtualMap.
  @param  DescriptorVersion The version of the structure entries in VirtualMap.
  @param  VirtualMap      An array of memory descriptors which contain new virtual
                         address mapping information for all runtime ranges.

  @retval  EFI_SUCCESS            The virtual address map has been applied.
  @retval  EFI_UNSUPPORTED        EFI firmware is not at runtime, or the EFI firmware is already in
                                  virtual address mapped mode.
  @retval  EFI_INVALID_PARAMETER  DescriptorSize or DescriptorVersion is invalid.
  @retval  EFI_NO_MAPPING         A virtual address was not supplied for a range in the memory
                                  map that requires a mapping.
  @retval  EFI_NOT_FOUND          A virtual address was supplied for an address that is not found
                                  in the memory map.

**/
EFI_STATUS
EFIAPI
RuntimeDriverSetVirtualAddressMap (
  IN UINTN                  MemoryMapSize,
  IN UINTN                  DescriptorSize,
  IN UINT32                 DescriptorVersion,
  IN EFI_MEMORY_DESCRIPTOR  *VirtualMap
  );
```

### D.1.13 Debug.SMM

#### D.1.13.1 SmmIplEntry (*)

```c
/**
  The Entry Point for SMM IPL

  Load SMM Core into SMRAM, register SMM Core entry point for SMIs, install
  SMM Base 2 Protocol and SMM Communication Protocol, and register for the
  critical events required to coordinate between DXE and SMM environments.

  @param  ImageHandle    The firmware allocated handle for the EFI image.
  @param  SystemTable    A pointer to the EFI System Table.

  @retval EFI_SUCCESS    The entry point is executed successfully.
  @retval Other          Some error occurred when executing this entry point.

**/
EFI_STATUS
EFIAPI
SmmIplEntry (
  IN EFI_HANDLE        ImageHandle,
  IN EFI_SYSTEM_TABLE  *SystemTable
  );
```

#### D.1.D.1 SmmMain (*)

```c
/**
  The Entry Point for SMM Core

  Install DXE Protocols and reload SMM Core into SMRAM and register SMM Core
  EntryPoint on the SMI vector.

  Note: This function is called for both DXE invocation and SMRAM invocation.

  @param  ImageHandle    The firmware allocated handle for the EFI image.
  @param  SystemTable    A pointer to the EFI System Table.

  @retval EFI_SUCCESS    The entry point is executed successfully.
  @retval Other          Some error occurred when executing this entry point.

**/
EFI_STATUS
EFIAPI
SmmMain (
  IN EFI_HANDLE        ImageHandle,
  IN EFI_SYSTEM_TABLE  *SystemTable
  );
```

#### D.1.13.3 PiCpuSmmEntry (*)

```c
/**
  The module Entry Point of the CPU SMM driver.

  @param  ImageHandle    The firmware allocated handle for the EFI image.
  @param  SystemTable    A pointer to the EFI System Table.

  @retval EFI_SUCCESS    The entry point is executed successfully.
  @retval Other          Some error occurs when executing this entry point.

**/
EFI_STATUS
EFIAPI
PiCpuSmmEntry (
  IN EFI_HANDLE        ImageHandle,
  IN EFI_SYSTEM_TABLE  *SystemTable
  );
```

#### D.1.13.4 SmmRelocateBases (*)

```c
/**
  Relocate SmmBases for each processor.

  Execute on first boot and all S3 resumes

**/
VOID
EFIAPI
SmmRelocateBases (
  VOID
  );
```

#### D.1.13.5 _SmiEntryPoint (*)

_**TODO**: Add prototype_

#### D.1.13.6 SmmEntryPoint (*)

```c
/**
  The main entry point to SMM Foundation.

  Note: This function is only used by SMRAM invocation.  It is never used by DXE invocation.

  @param  SmmEntryContext           Processor information and functionality
                                    needed by SMM Foundation.

**/
VOID
EFIAPI
SmmEntryPoint (
  IN CONST EFI_SMM_ENTRY_CONTEXT  *SmmEntryContext
  );
```

#### D.1.13.7 PlatformEnableAcpiCallback

_**TODO**: Add prototype_
