<!--- @file
  8.6 Network Stack Feature Example

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

## 8.6 Network Stack Feature Example
***
**Note:** The network stack example is presently incomplete and
no longer accurately represents the latest vision for advanced features.
This section will be updated to provide more accurate examples in the future.
***
### 8.6.1 Overview

The UEFI network stack supports IP4 and IP6, UDP, TCP/IP, MFTP, iSCSI, ARP,
DHCP, and PXE. Refer to the UEFI specification for related interfaces. More
details on UEFI networking can be found online such as the following resource
[UEFI Driver Network Boot Devices Guide](https://www.intel.com/content/dam/doc/guide/uefi-driver-networkboot-devices-guide.pdf).

### 8.6.2 Firmware Volumes

| `Name`    | `Content` | `Compressed` | `Parent FV` |
| --------- | --------- | ------------ | ----------- |
| FvNetwork | Network   | Yes          | FvAdvanced  |

#### 8.6.3 Modules

The network stack can be considered a relatively complicated UEFI Driver Model
compliant feature stack. The majority of the modules are board and silicon
independent so no porting is expected for the following components.

##### 8.6.3.1 UEFI Components (DXE)

| `Item`             | `Producing Package` | `Libraries Consumed` |
| ------------------ | ------------------- | -------------------- |
| SnpDxe.inf         | MdeModulePkg        |                      |
| DcpDxe.inf         | MdeModulePkg        |                      |
| MnpDxe.inf         | MdeModulePkg        |                      |
| VlanConfigDxe.inf  | MdeModulePkg        |                      |
| ArpDxe.inf         | MdeModulePkg        |                      |
| Dhcp4Dxe.inf       | MdeModulePkg        |                      |
| Ip4Dxe.inf         | MdeModulePkg        |                      |
| Mtftp4Dxe.inf      | MdeModulePkg        |                      |
| Tcp4Dxe.inf        | MdeModulePkg        |                      |
| Udp4Dxe.inf        | MdeModulePkg        |                      |
| UefiPxeBcDxe.inf   | NetworkPkg          |                      |
| IScsiDxe.inf       | MdeModulePkg        |                      |
| Ip6Dxe.inf         | NetworkPkg          |                      |
| TcpDxe.inf         | NetworkPkg          |                      |
| Udp6Dxe.inf        | NetworkPkg          |                      |
| Dhcp6Dxe.inf       | NetworkPkg          |                      |
| Mtftp6Dxe.inf      | NetworkPkg          |                      |
| UndiRuntimeDxe.inf | OptionRomPkg        |                      |

##### 8.6.3.2 Platform Architecture Libraries

None

#### 8.6.4 Required Functions

None

### 8.6.5 Configuration

None. `PcdEfiNetworkSupport` exists to allow user or build to disable network
option ROM dispatch by the PCI Bus driver. That PCD is enabled by default and
is detailed in Common Optimizations.

### 8.6.6 Data Flows

None

### 8.6.7 Control Flows

None

### 8.6.8 Build Files

These are the advanced feature module build files (i.e. INF files) included in
a board to build and include the FvNetwork.fv in the FvAdvanced firmware
volume.

### 8.6.9 Test Point Results

There are currently no test points defined for the network stack.

### 8.6.10 Functional Exit Criteria

TBD

### 8.6.11 Feature Enabling Checklist

TBD

### 8.6.12 Common Optimizations

#### 8.6.12.1 Performance

| `PCD`                                                | `Default` | `Purpose`                                                                  |
| ---------------------------------------------------- | --------- | -------------------------------------------------------------------------- |
| gEfiMdeModulePkgTokenSpaceGuid.PcdEfiNetworkSupport  | TRUE      | This causes PciBus driver to skip loading network option ROM if set FALSE. |

#### 8.6.12.2 Size

1. Remove IPv4

2. Remove PXE

3. Remove iSCSI

4. ...
