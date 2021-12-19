---
title: ndctl
layout: pmdk
---

# NAME

cxl-write-labels - write data to the label area on a memdev

# SYNOPSIS

>     cxl write-labels <mem> [-i <filename>]

# DESCRIPTION

The region label area is a small persistent partition of capacity
available on some CXL memory devices. The label area is used to and
configure or determine the set of memory devices participating in
different interleave sets. Read data from the input filename, or stdin,
and write it to the given \<mem> device. Note that the device must not
be active in any region, or actively registered with the nvdimm
subsystem. If it is, the kernel will not allow write access to the
device’s label data area.

# OPTIONS

\<memory device(s)>  
A *memX* device name, or a memdev id number. Restrict the operation to
the specified memdev(s). The keyword *all* can be specified to indicate
the lack of any restriction.

`-s; --size=`  
Limit the operation to the given number of bytes. A size of 0 indicates
to operate over the entire label capacity.

`-O; --offset=`  
Begin the operation at the given offset into the label area.

`-v`  
Turn on verbose debug messages in the library (if libcxl was built with
logging and debug enabled).

`-i; --input`  
input file

# SEE ALSO

[cxl-read-labels](cxl-read-labels.md), [cxl-zero-labels](cxl-zero-labels.md), CXL-2.0
9.13.2