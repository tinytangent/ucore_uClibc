uClibc - compiling user space program
=======================================

Compile uClibc
=======================

cp ./uclibc_config.linuxthread ./uClibc-0.9.33/.config

cd ./uClibc-0.9.33/

make menuconfig

Target Arch Features and Options -> Linux kernel header locate
set to `pwd`/../linux_header_x86_64.2.6.38/include (MUST enter fullpath!)

Library Installation Options
uClibc runtime libarary directory: `pwd`/install (MUST enter fullpath!)
uClibc development env dir: `pwd`/../install/usr (MUST enter fullpath!)

make -j6
make install

Install will be successful if ./install/ directory is created

Compile user program
=======================

	cd test1

see Makefile.x86_64 to understand compilng a sample C program

	make -f Makefile.x86_64

some user program will be compiled and linked

	./test1

try run user program on your x86 platform

Copy user program to ucore
==============================

user program is located at some directory like '_initial.big'

	cp ./test1 ${ucore_core_plus}/ucore/src/user-ucore/_initial.big/

update sfsimg
	
	make sfsimg

run ucore in amd64 arch

	make runamd64
	make kvmamd64

run user program in ucore

	Welcome to sh!
	$./test1

debug with gdb

	make debug


