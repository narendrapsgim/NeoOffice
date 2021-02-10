# Intructions for building NeoOffice 2017

Important: NeoOffice 2017 will build on **macOS 10.12 Sierra or macOS 10.14 Mojave only**.

## Getting NeoOffice 2017 sources

Download and extract the NeoOffice-2017_25.tar.gz file from https://github.com/neooffice/NeoOffice/releases.

## Install build dependencies

1. Make sure that you have downloaded and installed the following dependencies from http://developer.apple.com/ website:

   + macOS 10.12 Sierra:
     - Xcode v8.3.3
     - Command Line Tools for Xcode v8.3.2
   + macOS 10.14 Mojave:
     - Xcode v10.3
     - Command Line Tools for Xcode v10.3

2. Download and install Oracle's Java 1.8 Development Kit (JDK) from the following URL:

   http://www.neooffice.org/neojava/javadownload.php

   Important: the build will fail if Oracle's Java 9 or 10 are installed so be sure to delete such versions from the /Library/Java/JavaVirtualMachines folder before starting the build.

3. Install the following Mac Ports packages by downloading, compiling, and installing the following packages from the http://www.macports.org/ website. Note that you will need download and install the latest MacPorts package to install the MacPorts "port" command. The "port" command is then used to do the downloading, compiling, and installation of the following packages:

<pre>
   sudo /opt/local/bin/port install autoconf -x11
   sudo /opt/local/bin/port install automake -x11
   sudo /opt/local/bin/port install cvs -x11
   sudo /opt/local/bin/port install gnutar -x11
   sudo /opt/local/bin/port install xz -x11
</pre>

   After running the above command, add "/opt/local/bin" to the end of your shell's PATH environment variable so that the build can find the "autoconf" and other commands.

After running the above command, add "/opt/local/bin" to the end of your shell's PATH environment variable so that the build can all of the commands installed by /opt/local/bin/port command in the previous step.

4. Installed the Perl Archive::Zip module using the following command. You may need to run this command more than once as the unit tests may fail the first time that you run it:

<pre>
   sudo cpan -i Archive::Zip
</pre>

5. Disable System Integrity Protection (SIP). SIP must be disabled as it causes exporting DYLD_* environment variables in makefiles to fail which will break the build. To disable SIP, reboot into Recovery mode, run the following command in the Terminal, and then reboot normally:

<pre>
   csrutil disable
</pre>

## Build NeoOffice 2017

Build NeoOffice 2017 by invoking the following commands:

<pre>
   cd /absolute/path/of/extracted/source
   make
</pre>

Important note: if the build fails in the build.neo_tests make target, uncheck iCloud Drive in the System Preferences iCloud panel and reinvoke the above commands to continue the build.

If the build was successful, you should find the following files:

<pre>
   /absolute/path/of/extracted/source/install*/*.dmg 
</pre>
