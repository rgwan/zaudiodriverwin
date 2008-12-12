
BUILDING THE HULA AND XMIDI DRIVERS

Prerequisites:

In addition to the actual huladrv source code, you'll also need to
install the following items

        1.   A recent Windows DDK distribution.   I use Windows
             DDK 3790.1830, although this will probably change over time.
	     Also make sure that you install the patch for this build:
	     Patch the DDK with the files available in 
             \\valinor\TechCenter\UDAMirror\UDA Miscellaneous Tools\DDK patch\ddkp1830.zip. 
             Unzip the contents of ddkp1830.zip over your DDK install.

        2.   In order to build the installer, you'll want to check out the
             Installer source code.   This can be found in
             ctlsg_cvs:/Vcs/Atc/Project/Installer

        3.   You will need to add the HULAROOT variable to your environment.
             It should point to the huladrv directory.  You also should set
	     the INSTALLROOT variable so that it points to the Installer
	     directory.

        4.   You will need to have some of the udasw build tools available.
             Most folks choose to check out udasw\bin\win and it to their
             path.   It may be that you don't need everything that is there;
             I leave that as an exercise to the reader.


General Procedure:
        1.  Start up a shell in the DDK build environment of your choice.
        2.  Make sure that you have the HULAROOT environment variable set.
        3.  Make sure that you have the bldpkg.cmd in you PATH.  A copy can
            be found in %HULAROOT%\bin\win\scripts.
        4.  Change your current directory to %HULAROOT%
        5.  Type
                        bldpkg -@ hula.pkg %INSTALLROOT%
                    or
                        bldpkg -@ xmidi.pkg %INSTALLROOT%

        6.  When bldpkg is finished, you should end up with an installable
            driver in the package subdirectory.


Miscellaneous tips and suggestions:
	* The top-of-trunk contains a merged USB2.0/USB1.0 driver.  There are
	  branch tags for the Xmidi, original Hula, and MicroPod releases, 
	  so if you're doing a bug fix for one of these projects you might
	  want to start with the appropriate branch rather than top-of-trunk.

	* You can pass flags to the underlying build system using the -build flag.
	  For example, bldpkg -build -cef -@ hula.pkg %INSTALLROOT% will perform
	  a clean build.

	* Use -retail off to create a debug build.

        * Don't forget to have the version numbers updated whenever you
          branch the tree!  The CTL installation team should be able to
          help you with this if you run into trouble.


ADDENDUM:
	Note the .dsw file in the build directory.  This can be used to build the 
	driver.
