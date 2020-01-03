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

```python
sudo apt-get install gawk wget git-core diffstat unzip texinfo gcc-multilib \
build-essential chrpath socat cpio python python3 python3-pip python3-pexpect \
xz-utils debianutils iputils-ping libsdl1.2-dev xterm
``` 

Now we are ready to clone poky! Use `git clone git://git.yoctoproject.org/poky`. 


**3)OpenEmbedded Build System**

If you have built open source software packages for a Linux host system before, you may have noticed that the workflow follows a specific pattern.
Fetch -> Extract -> Patch -> Configure -> Build -> Install -> Package

Based on the OpenEmbebedded workflow, we can list: 

![alt tag](https://www.embarcados.com.br/wp-content/uploads/2016/07/yocto-environment.png)

Metadata files are subdivided into the categories configuration files and recipes.

Configuration Files

- BitBake Master Configuration File (`bitbake.conf`): This file contains all the default configuration settings.

- Layer Configuration (`layer.conf`): This file contains path settings and file patterns for the recipe files of the
layer. The layer.conf file can be found in the conf subdirectory of the layer.

- Build Environment Layer Configuration (`bblayers.conf`): The file bblayers.conf provides BitBake with information on what layers to include with the build process and the filesystem paths where they are found. Each build environment has its own bblayers.conf file, which can be found in the conf subdirectory of the build environment.

- Build Environment Configuration (`local.conf`): The local.conf file contains settings that apply to the particular build environment, such as paths to download locations, build outputs, and other files. 

- Distribution Configuration (`<distribution-name>.conf`): Distribution configuration files contain variable settings reflecting policies that apply for a
particular distribution built by the OpenEmbedded build system.


- Machine Configuration (`<machine-name>.conf`)

Recipes 

BitBake recipes form the core of the build system as they define the build workflow for each software package.


The script oe-init-build-env creates and initializes build environments. It is used in two ways: to create an empty build environment with default settings and to initialize a build environment that has previously been created. 

# Linux System Architecture 

A Linux OS can be divided into two levels, the kernel space and the user or application space.

All kernel code is executed in unrestricted or privileged mode. In this mode, any instruction of the instruction set of the architecture can be executed.
Application code, by contrast, is executed in restricted or user mode.

- Bootloader: typically just initializes the hardware necessary for the operating system kernel to boot. All other hardware and peripherals are initialized by the operating system itself at a later stage of the boot process.
- Kernel: the two primary functions of an operating system’s kernel are to manage the computer’s resources and allow other programs to execute and access the resources.

[List of Linux bootloaders](https://www.ubuntupit.com/best-linux-bootloader-for-home-and-embedded-systems/)


# Building a Custom Linux Distribution

The simplest method for adding packages and package groups to images is to add IMAGE_INSTALL to the conf/local.conf file of your build environment:

`IMAGE_INSTALL_append = ” <package> <package group>”` 

After configure a image becomes important to test it with QEMU emulator. Even though you eventually build a system for the target hardware of your product, using QEMU for testing makes good sense due the long build of each personalized image. To run QEMU, follow the steps:

- 1) `runqemu qemux86` 
- 2) `runqemu qemux86 core-image-minimal` 


- Extending a Core Image with a Recipe 

Adding packages and package groups to CORE_IMAGE_EXTRA_INSTALL and IMAGE_INSTALL and in conf/local.conf may be straightforward and quick, but doing so makes a project hard to maintain and complicates reuse. A better way is to extend a predefined image through a recipe. Listing 7-2 shows a simple recipe that extends
core-image-base. 

__INCOMPLETO__

# Software Package Recipes 



# Application Development

ADT provides application developers with all the necessary tools to write user space applications in C and C++ using the Linux and middleware APIs. These can be GNU Make–based, GNU Autotools–based, or CMakebased applications. After initializing the ADT environment, you can use the command-line to cross-build your applications..

Setting Up a Yocto Project ADT

- 1) Download the ADT Installer 
- 2) Build the ADT installer 
- 3) Build a Toolchain Installer to Create an ADT



## References 

[Yocto Toolchain Installation](http://variwiki.com/index.php?title=Yocto_Toolchain_installation)
[Embedded Linux Systems with the Yocto Project](http://book.yoctoprojectbook.com/index)
[Embarcados Portal](https://www.embarcados.com.br/linux-para-a-raspberry-pi-3-usando-yocto/)
[Raspberry Pi cross compile](https://www.embarcados.com.br/cross-compiling-com-a-raspberry-pi/)


