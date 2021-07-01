# kernel-devel
- How to develop a kernel module.

## Index
- [Red Hat Enterprise Linux](#red-hat-enterprise-linux)
- [AlmaLinux](#almalinux)
- [SUSE Enterprise Linux](#suse-enterprise-linux)
- [Ubuntu](#ubuntu)
- [Link](#link)

## Red Hat Enterprise Linux
### Red Hat Enterprise Linux 8
- FIXME 

## AlmaLinux
### AlmaLinux 8
1. Run the following command.
   ```sh
   dnf install gcc
   dnf install make
   dnf install kernel-devel
   dnf install elfutils-libelf-devel
   ```
1. Save the source files.
1. Edit Makefile as below.
   ```
   $(MAKE) -C /lib/modules/$(shell uname -r)/build SUBDIRS=$(shell pwd) module
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
   zypper in gcc
   zypper in kernel-devel
   ```
1. Save the source files.
1. Edit Makefile as below.
   ```
   $(MAKE) -C /lib/modules/$(shell uname -r)/build M=$(shell pwd) modules
   ```
1. Run make command.

## Ubuntu
### Ubuntu 20.04
- FIXME

## Link
- The Linux Kernel Module Programming Guide
  - https://tldp.org/LDP/lkmpg/2.6/html/index.html