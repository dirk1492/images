
Small Ubuntu 16.04 docker image

This is a arm64 port of the gcr.io/google_containers/ubuntu-slim image.
The odroid c2 kernel is too old to build this image. Please use QEMU with xenial-server-cloudimg-arm64-uefi1.img.

The size of this image is ~47MB (less than half than `ubuntu:16.04).
This is possible by the removal of packages that are not required in a container:
- dmsetup
- e2fsprogs
- init
- initscripts
- libcap2-bin
- libcryptsetup4
- libdevmapper1.02.1
- libkmod2
- libsmartcols1
- libudev1
- mount
- procps
- systemd
- systemd-sysv
- tzdata
- udev
- util-linux
- bash
