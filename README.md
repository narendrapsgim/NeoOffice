# Intructions for building NeoOffice 2015

Important: NeoOffice 2015 will build on **Mac OS X 10.8 Mountain Lion only**.

## Getting NeoOffice 2015 sources

Download and extract the NeoOffice-2015_12.tar.gz file from https://github.com/neooffice/NeoOffice/releases.

## Install build dependencies

1. Make sure that you have downloaded and installed the following dependencies from http://developer.apple.com/ website:

   Xcode Tools v4.6.3

   After installing Xcode, install the XCode Command Line Tools by launching XCode and selecting the Xcode :: Preferences menu. In the dialog that appears, click on the Downloads tab and press the "Install" button for the "Command Line Tools" option.

   Warning: do *not* install Xcode 5 or a separately downloaded command line tools package as it will cause the "gcc" and "g++" to really use the clang compiler instead of the gcc compiler.

2. Download and install the Apple's Java 1.6 Development Kit (JDK) from the following URL. Note: the build will ignore Oracle's JDKs:

   http://support.apple.com/kb/DL1572

3. Make sure that you have installed the "gcp" and "pkg-config" commands. You can download, compile, and install these commands by downloading, compiling, and installing the following packages from the http://www.macports.org/ website. Note that you will need download and install the latest MacPorts Mountain Lion package to install MacPorts "port" command. The "port" command is then used to do the downloading, compiling, and installation of the following packages:

<pre>
   sudo /opt/local/bin/port install coreutils
   sudo /opt/local/bin/port install pkgconfig
   sudo /opt/local/bin/port install libIDL
   sudo /opt/local/bin/port install gperf
   sudo /opt/local/bin/port install flex
   sudo /opt/local/bin/port install wget
   sudo /opt/local/bin/port install gnutar
</pre>

   After running the above command, add "/opt/local/bin" to the end of your shell's PATH environment variable so that the build can find the "autoconf" and other commands.

4. Make sure that you have downloaded and installed the following Perl module from the http://www.cpan.org/modules/index.html website. Note that you will need to follow the instructions on the website to download and install the Archive::Zip module:

   Archive::Zip

5. Make sure that you have downloaded and installed the Subversion client and have the "svn" command in your PATH. Subversion binaries can be downloaded from here:

   http://subversion.tigris.org/project_packages.html

## Build NeoOffice 2015

Build NeoOffice 2015 by invoking the following commands:

<pre>
   cd /absolute/path/of/extracted/source
   make GNUCP=/absolute/path/of/your/gcp/command LIBIDL_CONFIG=/absolute/path/of/your/libIDL-config-2/command PKG_CONFIG=/absolute/path/of/your/pkg-config/command
</pre>

If the build was successful, you should find the following files:

<pre>
   /absolute/path/of/extracted/source/install*/*.dmg 
</pre>
