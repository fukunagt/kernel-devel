# How to Make a Kernel Module

## Index
- Red Hat Enterprise Linux and Clones
  - [Amazon Linux](#amazon-linux)
  - [AlmaLinux](#almalinux)
  - [MIRACLE LINUX](#miracle-linux)
  - [Red Hat Enterprise Linux](#red-hat-enterprise-linux)
- SUSE
  - [openSUSE](#opensuse)
  - [SUSE Enterprise Linux](#suse-enterprise-linux)
- [Link](#link)

## Amazon Linux
### Amazon Linux 2
1. Run the following command.
   ```sh
   sudo yum install gcc make kernel-devel elfutils-libelf-devel -y
   ```

## AlmaLinux
### AlmaLinux 8
1. Run the following command.
   ```sh
   dnf install gcc make kernel-devel elfutils-libelf-devel -y
   ```
1. Save the source files.
1. Edit Makefile as below.
   ```
   $(MAKE) -C /lib/modules/$(shell uname -r)/build SUBDIRS=$(shell pwd) module
   ```
1. Run make command.

## MIRACLE LINUX
### MIRACLE LINUX 9
   ```sh
   dnf install gcc make kernel-devel elfutils-libelf-devel -y
   ```
## Red Hat Enterprise Linux
### Red Hat Enterprise Linux 8
1. Insert the DVD and mount it (e.g. /media).
1. Create a repository file (e.g. /etc/yum.repos.d/dvd.repo) as below.
   ```
   [InstallMedia-BaseOS]
   name=Red Hat Enterprise Linux 8 - BaseOS
   metadata_expire=-1
   gpgcheck=1
   enabled=1
   baseurl=file:///media/BaseOS/
   gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
   
   [InstallMedia-AppStream]
   name=Red Hat Enterprise Linux 8 - AppStream
   metadata_expire=-1
   gpgcheck=1
   enabled=1
   baseurl=file:///media/AppStream/
   gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
   ```
1. Run the following command.
   ```sh
   dnf install gcc make kernel-devel elfutils-libelf-devel -y
   ```
1. Save the source files.
1. Edit Makefile as below.
   ```
   $(MAKE) -C /lib/modules/$(shell uname -r)/build SUBDIRS=$(shell pwd) module
   ```
1. Run make command.

## openSUSE
### openSUSE Leap 15.4
1. If you have a proxy server, run the following command.
   ```sh
   export http_proxy=<your proxy server>
   ```
1. Run the following commands to install gcc and kernel-devel.
   ```sh
   zypper in gcc kernel-devel
   ```
1. Save the source files.
1. Edit Makefile as below.
   ```
   $(MAKE) -C /lib/modules/$(shell uname -r)/build M=$(shell pwd) modules
   ```
1. Run make command.

## SUSE Enterprise Linux
### SUSE Enterprise Linux 15
1. Insert the DVD.
1. Enable zypper DVD repository.
   1. Move to /etc/zypp/repos.d/.
   1. Open the follwing files with Vim.
      - Basesystem-Module_15.2-0.repo
      - SLES15-SP2-15.2-0.repo
      - Server-Applications-Module_15.2-0.repo
   1. Enable the repository.
      ```
      Before:
      enabled=0

      After
      enabled=1
      ```
1. Run the following commands to install gcc and kernel-devel.
   ```sh
   zypper in gcc kernel-devel
   ```
1. Save the source files.
1. Edit Makefile as below.
   ```
   $(MAKE) -C /lib/modules/$(shell uname -r)/build M=$(shell pwd) modules
   ```
1. Run make command.

<!--
## Ubuntu
### Ubuntu 22.04
- FIXME
1. Install
   ```
   sudo apt install gcc
   sudo apt install make
   ```
-->
## Link
- The Linux Kernel Module Programming Guide
  - For kernerl version 5.x
    - https://sysprog21.github.io/lkmpg/
  - For kernel version version is earlier than 5.x
    - https://tldp.org/LDP/lkmpg/2.6/html/index.html