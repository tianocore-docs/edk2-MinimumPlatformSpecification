<!--- @file
  README.md for the Minimum Platform Specification

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

<img src="media/TianocoreTitlePageLogo.jpg" width="300" />

### {{ book.title }}

{% if book.draft %}
** DRAFT FOR REVIEW **
{% else %}
** {{ book.version }} **
{% endif %}

** {{ gitbook.time|date('MM/DD/YYYY hh:mm:ss') }} **
{% if book.udkrelease %}
** {{ book.udkrelease }} **
{% endif %}
### Acknowledgements

Redistribution and use in source (original document form) and 'compiled'
forms (converted to PDF, epub, HTML and other formats) with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code (original document form) must retain the
   above copyright notice, this list of conditions and the following
   disclaimer as the first lines of this file unmodified.

2. Redistributions in compiled form (transformed to other DTDs, converted to
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

Copyright (c) 2019, Intel Corporation. All rights reserved.


### Revision History

| Revision   | Revision History   | Date        |
| ---------- | ------------------ | ----------- |
| 0.7        | Initial release    | May   2019  |

THIS SPECIFICATION IS PROVIDED "AS IS" WITH NO WARRANTIES WHATSOEVER,

INCLUDING ANY WARRANTY OF MERCHANTABILITY, NONINFRINGEMENT, FITNESS

FOR ANY PARTICULAR PURPOSE, OR ANY WARRANTY OTHERWISE ARISING OUT OF ANY
PROPOSAL,

SPECIFICATION OR SAMPLE. Except for a limited copyright license to copy this
specification for internal use only, no license, express or implied, by
estoppel or otherwise, to any intellectual property rights is granted herein.

Intel disclaims all liability, including liability for infringement of any
proprietary rights, relating to implementation of information in this
specification. Intel does not warrant or represent that such implementation(s)
will not infringe such rights.

Designers must not rely on the absence or characteristics of any features or
instructions marked "reserved" or "undefined." Intel reserves these for future
definition and shall have no responsibility whatsoever for conflicts or
incompatibilities arising from future changes to them.

Intel and the Intel logo are trademarks or registered trademarks of Intel
Corporation or its subsidiaries in the United States and other countries.

* Other names and brands may be claimed as the property of others.

Copyright © 2019, Intel Corporation
