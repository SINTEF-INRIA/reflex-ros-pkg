default: gccarm.repo-added gccarm.installed openocd dfu
# edited by: Christian Heider, updated to work Ubuntu 16.04.

# potentially this could be smarter if it detects the OS/distro or whatever.
dfu:
	sudo apt-get update
	sudo apt-get install dfu-util

gccarm.installed:
	# sudo add-apt-repository ppa:terry.guo/gcc-arm-embedded # Broken link
	# sudo apt-get update
	# sudo apt-get install gcc-arm-none-eabi

	sudo apt-get update
	sudo apt-get install gcc-arm-embedded
	touch gccarm.installed

gccarm.repo-added:
	touch gccarm.repo-added
	sudo add-apt-repository ppa:team-gcc-arm-embedded/ppa
	# if crash due to non-compatable version of Ubuntu
	# check Team-GCC-arm-embedded, and change a release you can use, change by: 
	# sudo nano /etc/apt/sources.list.d/tema-gcc-arm-embedded-ubuntu-ppa-`lsb_release --codename | cut -f2`.list
	# Replace releasename with a viable one from Team-GCC-arm-embedded. 
	# Then re run make.

openocd-source:
	# git clone git://git.code.sf.net/p/openocd/code openocd-source
	git clone https://github.com/ntfreak/openocd.git openocd-source

openocd: openocd-source
	sudo apt-get install automake texinfo libusb-1.0-0-dev texi2html -y
	cd openocd-source && ./bootstrap && ./configure --prefix=$(shell pwd)/openocd --enable-ftdi && make && sudo make install
