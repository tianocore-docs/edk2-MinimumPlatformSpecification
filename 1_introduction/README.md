<!--- @file
  1 Introduction

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

# 1 Introduction

This specification details the required and optional elements for an EDK II
based platform design with the following objectives:

1. Define a structure that enables developers to consistently navigate source
   code, execution flow, and the functional results of bootstrapping a system.
2. Enable a minimal platform where minimal is defined as the minimal firmware
   implementation required to produce a basic solution that can be further
   extended to meet a multitude of client, server, and embedded market needs.
3. Minimize coupling between common, silicon, platform, and board packages.
4. Enable large granularity binary solutions.

A key aspect of these objectives is to improve the transparency and security
quality across the client, server, and embedded ecosystems.

This document assumes a working knowledge of the EDK II and UEFI Specifications.
The minimal platform defined supports the use of Intel® Firmware Support Package
\(FSP\), but does not require usage of the Intel® FSP API. The minimal platform
is binary component oriented, but designed to enable a highly optimized form for
embedded boot loaders.

