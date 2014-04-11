#!/bin/bash
echo "This script upgrades the older version of OpenSSl included with OS X"
echo "to the most recent openssl-1.0.1g."
echo "Checking whether OpenSSL is older version..."

if [ "$(openssl version)" != "OpenSSL 1.0.1g 7 Apr 2014" ]; then
	echo "Insecure version of OpenSSl found. Upgrading..."
	echo "Checking whether xcode command line tools are installed..."
	if [ "$(pkgutil --pkg-info=com.apple.pkg.CLTools_Executables)" == "No receipt for 'com.apple.pkg.CLTools_Executables' found at '/'." ]; then
		xcode-select --install
	fi
	curl -o openssl-1.0.1g.tar.gz https://www.openssl.org/source/openssl-1.0.1g.tar.gz
	tar xvfz openssl-1.0.1g.tar.gz
	cd openssl-1.0.1g
	sudo ./configure --prefix=/usr/ darwin64-x86_64-cc
	sudo make
	sudo make install
	cd ..
	rm openssl-1.0.1g.tar.gz
	rm -rf openssl-1.0.1g
	osascript -e 'tell app "System Events" to display dialog "OpenSSL patched! OpenSSL upgraded to most recent version."'
	echo "OpenSSL upgraded to most recent version."
	echo "$(openssl version)"
else
	echo 'hello' > 'world.txt'
	osascript -e 'tell app "System Events" to display dialog "The current OpenSSL install is up to date. Version : OpenSSL 1.0.1g 7 Apr 2014"'
	echo "The current OpenSSL install is up to date. Version : OpenSSL 1.0.1g 7 Apr 2014"
	echo "Version : OpenSSL 1.0.1g 7 Apr 2014"
fi