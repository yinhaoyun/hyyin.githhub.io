Becasue the pacthes of Meltdown/Specture was introduced into Linux Kernel (and Windows).
Your Intel CPU Performance has been degraded after the Linux/Windows was updated.

However, there is a way to *Make your CPU fast again*.

# In Short

add the "mitigations=off" to kernel command line

`mitigations=off`

If you are using a kernel older than 5.1.13 then you should use this rather long one-liner instead:

`noibrs noibpb nopti nospectre_v2 nospectre_v1 l1tf=off nospec_store_bypass_disable no_stf_barrier mds=off mitigations=off`

Reference: https://linuxreviews.org/HOWTO_make_Linux_run_blazing_fast_(again)_on_Intel_CPUs

# How to modify the kernel parameter
For example, my Linux is Mint 19.

## 1. Modify the /etc/default/grub

`sudo vi /etc/default/grub'

Find the line: GRUB_CMDLINE_LINUX_DEFAULT

Original
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.runpm=0 elevator=noop"
```

Add `noibrs noibpb nopti nospectre_v2 nospectre_v1 l1tf=off nospec_store_bypass_disable no_stf_barrier mds=off mitigations=off` 
to the end of the parameters.

After
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.runpm=0 elevator=noop noibrs noibpb nopti nospectre_v2 nospectre_v1 l1tf=off nospec_store_bypass_disable no_stf_barrier mds=off mitigations=off"
```

## 2. update grub config

Run update-grub
```sudo update-grub```

## 3. Reboot and check /proc/cmdline

To check the paramemter is updated, reboot and `cat /proc/cmdline'.

# Performance Improvement Test

## UnixBench

## GeekBench 5
