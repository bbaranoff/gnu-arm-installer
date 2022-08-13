# gnu-arm-installer

WikiStart » OsmocomBB Firmware » Toolchain »

GNU ARM toolchain
This page will describe the procedure for compiling a GNU ARM toolchain.
We will build a toolchain consisting of:

GCC 4.8.2
Binutils 2.21.1
Newlib 1.19
Getting the buildscript
First of all, create a directory you want to use for building the toolchain, and download the buildscript [raw-gnu-arm-build.3.sh] there.
You will need to make it executable:

```bash

$ chmod +x gnu-arm-build.3.sh
Dependencies
In order to build the toolchain, you will need to install the following packages (assuming you're using a Debian-based distribution):

$ sudo apt-get install build-essential libgmp3-dev libmpfr-dev libx11-6 libx11-dev texinfo flex bison libncurses5 \
  libncurses5-dbg libncurses5-dev libncursesw5 libncursesw5-dbg libncursesw5-dev zlibc zlib1g-dev libmpfr4 libmpc-dev
Note: you maybe have to adjust some libncurses and libmpfr version numbers in the above for newer distributions (as of 2021). Use apt-cache search to figure it out.

```

Preparation
Open a shell in the directory of gnu-arm-build.sh and create the following directories:

```bash

$ mkdir build install src

```
Download the needed sources to src/:

```bash
$ cd src/
$ wget http://ftp.gnu.org/gnu/gcc/gcc-4.8.2/gcc-4.8.2.tar.bz2
$ wget http://ftp.gnu.org/gnu/binutils/binutils-2.21.1a.tar.bz2
$ wget ftp://sources.redhat.com/pub/newlib/newlib-1.19.0.tar.gz
```


On Ubuntu 18.04 and Debian 10, tweak the build script such that it applies gcc-4.8.2-ubuntu-18-04.diff after unpacking gcc sources.

Building the toolchain
```bash
$ cd ..
$ ./gnu-arm-build.3.sh 
```

I will build an arm-none-eabi cross-compiler:

  Prefix: <YOURPATH>/install
  Sources: <YOURPATH>/src
  Build files: <YOURPATH>/build

Press ^C now if you do NOT want to do this.
Hit enter and after some time hopefully end up with:

Build complete! Add <YOURPATH>/bin to your PATH to make arm-none-eabi-gcc and friends
accessible directly.
Making it accessible
If you're using bash, you can add the following in your ~/.bashrc file:

export PATH=$PATH:<YOURPATH>/install/bin
That's it. You can build OsmocomBB now (see Software Getting Started).


```bash
export PATH=$PATH:<YOURPATH>/install/bin
```
Credits:

This script is a slightly updated/modified version of the script found here.

The original version also builds Insight, but since we don't need that, we won't build it. If you want to, just remove the comments in the shellscript.

Files (4)
Updated by unrznbl over 1 year ago · 19 revisions

Powered by Redmine © 2006-2021 Jean-Philippe Lang
