uClibc - compiling user space program
=======================================

Compile uClibc
=======================

	cp ./config-uclib.x86_64 ./uClibc/.config
	cd ./uClibc/
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


