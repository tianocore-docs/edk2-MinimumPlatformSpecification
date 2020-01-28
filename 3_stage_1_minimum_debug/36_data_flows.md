<!--- @file
  3.6 Data Flows

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

## 3.6 Data Flows

This section defines key data structures and the ways this data flows through
the system over time.

### 3.6.1 Serial Port Configuration

Serial port configuration spans build and boot. Serial port parameters come
from the board and are used for debug features, serial input/output devices
supporting local or remote consoles, and OS level debuggers.

1. Serial port default configuration options are defined in
the MdePkg.dec.

2. Serial port configuration options may be overwritten by
the BoardPkg.dsc.

3. Serial port configuration options are consumed by the
SerialPortLib library class implementation.

4. SerialPortLib library class is used by the
StatusCodeHandlerPei.inf component to initialize and display messages to a
serial port.

5. Serial port configuration options are published via a
SERIAL_PORT_CONFIGURATION_HOB.

6. SERIAL_PORT_CONFIGURATION_HOB is consumed by
MinPlatformSerialDxe.inf to produce EFI_SERIAL_IO_PROTOCOL.

### 3.6.2 Debug Configuration

| `PCD`                                                          | `Purpose`                                                  |
| -------------------------------------------------------------- | ---------------------------------------------------------- |
| gEfiMdeModulePkgTokenSpaceGuid.PcdSerialBaudRate               | Baud rate for the 16550 serial port                        |
| gEfiMdeModulePkgTokenSpaceGuid.PcdSerialUseMmio                | Enable serial port MMIO addressing                         |
| gEfiMdeModulePkgTokenSpaceGuid.PcdSerialUseHardwareFlowControl | Enable serial port HW flow control                         |
| gEfiMdeModulePkgTokenSpaceGuid.PcdSerialDetectCable            | Enable blocking Tx if no cable                             |
| gEfiMdeModulePkgTokenSpaceGuid.PcdSerialRegisterBase           | Register the serial port base address                      |
| gEfiMdeModulePkgTokenSpaceGuid.PcdSerialLineControl            | Serial port line control configuration                     |
| gEfiMdeModulePkgTokenSpaceGuid.PcdSerialFifoControl            | Serial port FIFO control                                   |
| gMinPlatformPkgTokenSpaceGuid.PcdSecSerialPortDebugEnable      | Enable serial port debug in SEC phase                      |
| gEfiMdePkgTokenSpaceGuid.PcdFixedDebugPrintErrorLevel          | Control build time optimization based on debug print level |
| gEfiMdePkgTokenSpaceGuid.PcdDebugPropertyMask                  | Control DebugLib behavior                                  |
| gEfiMdePkgTokenSpaceGuid.PcdDebugPrintErrorLevel               | Control run time debug print level                         |
| gEfiMdePkgTokenSpaceGuid.PcdReportStatusCodePropertyMask       | Control display of status codes                            |

###### Table 12 Stage I Debug Configuration
