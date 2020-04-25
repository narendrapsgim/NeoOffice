# Intructions for building NeoOffice 3.4.1

Important: NeoOffice 3.4.1 will build on **Mac OS X 10.6 Snow Leopard for Intel only**.

## Getting NeoOffice 3.4.1 sources

Download and extract the NeoOffice-3_4_1-28.tar.gz file from https://github.com/neooffice/NeoOffice/releases.

## Install build dependencies

1. Make sure that you have booted Mac OS X 10.6 into 32 bit mode by executing the following command and rebooting:

<pre>
   sudo systemsetup -setkernelbootarchitecture i386
</pre>

2. Make sure that you have downloaded and installed the following dependencies from http://developer.apple.com/ website. Note: NeoOffice 3.4.1 will not build if Xcode 4.x is installed:

   Xcode Tools v3.2.6

3. Make sure that you have installed the "gcp" and "pkg-config" commands. You can download, compile, and install these commands by downloading, compiling, and installing the following packages from the http://www.macports.org/ website. Note that you will need download and install the latest MacPorts Snow Leopard package to install MacPorts "port" command. The "port" command is then used to do the downloading, compiling, and installation of the following packages:

<pre>
   sudo /opt/local/bin/port install coreutils
   sudo /opt/local/bin/port install pkgconfig
   sudo /opt/local/bin/port install libIDL
   sudo /opt/local/bin/port install gperf
   sudo /opt/local/bin/port install flex
   sudo /opt/local/bin/port install wget
</pre>

   After running the above commands, execute the following command to ensure that 32 bit versions of the packages are available otherwise the build will fail:

<pre>
   sudo /opt/local/bin/port upgrade --enforce-variants active +universal 
</pre>

4. Make sure that you have downloaded and installed the following Perl module from the http://www.cpan.org/modules/index.html website. Note that you will need to follow the instructions on the website to download and install the Archive::Zip module:

   Archive::Zip

5. Make sure that you have downloaded and installed the Subversion client and have the "svn" command in your PATH. Subversion binaries can be downloaded from here:

   http://subversion.tigris.org/project_packages.html

## Build NeoOffice 3.4.1

Build NeoOffice 3.4.1 by invoking the following commands:

<pre>
   cd /absolute/path/of/extracted/source
   make GNUCP=/absolute/path/of/your/gcp/command LIBIDL_CONFIG=/absolute/path/of/your/libIDL-config-2/command PKG_CONFIG=/absolute/path/of/your/pkg-config/command
</pre>

If the build was successful, you should find the following files:

<pre>
   /absolute/path/of/extracted/source/install*/*.dmg 
</pre>
