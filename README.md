# Embedded Linux 101

This page is organized to summarize the 101 of Embedded Linux. Most of the content is based on Yocto. The target board needed for these tutorials are Raspberry Pi or Beaglebone related. 

## Topics 

**1) Linux for Embedded Systems**

Why should I use Linux on my Embedded Systems? 

Because Linux is a multitasking operating system, file-based and real-time. 

Some Linux distributions: Android, Ångström Distribution, OpenWRT. For many of the fully fledged Linux distributions for desktop, server, and cloud, variants
targeting embedded systems are now also available:

- Debian (www.emdebian.org)
- Fedora (https://fedoraproject.org/wiki/Embedded)
- Gentoo (https://wiki.gentoo.org/wiki/Project:Embedded)
- SUSE (https://tr.opensuse.org/MicroSUSE)
- Ubuntu (https://wiki.ubuntu.com/EmbeddedUbuntu)

- **Embedded Linux Development Tools** 

Most of the work on the development using embedded Linux is related to develop a system environment, build our own Linux distribution. 

The tools available are: Baserock, Buildroot, OpenEmbedded and The Yocto Project. 

Building and maintaining an operating system is not a trivial task, the main aspects related to the building process are:  Bootloader, Kernel, Device Drivers, Life Cycle Management and App Software Management. 

**2)The Yocto Project**

The Yocto Project is an open source collaboration project that helps developers create custom Linux-based systems regardless of the hardware architecture.

In order to use Yocto make sure your build host meets the following requirements:

- 50 Gbytes of free disk space
- Runs a supported Linux distribution (i.e. recent releases of Fedora, openSUSE, CentOS, Debian, or Ubuntu).
- Git 1.8.3.1 or greater
- tar 1.27 or greater
- Python 3.4.0 or greater.

You must install essential host packages on your build host. The following command installs the host packages based on an Ubuntu distribution:

```sudo apt-get install gawk wget git-core diffstat unzip texinfo gcc-multilib \
   build-essential chrpath socat cpio python python3 python3-pip python3-pexpect \
   xz-utils debianutils iputils-ping libsdl1.2-dev xterm
``` 

Now we are ready to clone poky! Use `git clone git://git.yoctoproject.org/poky`. 


## References 

[Embedded Linux Systems with the Yocto Project](http://book.yoctoprojectbook.com/index)


