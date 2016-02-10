# pycharm-dpkg
Creates Debian package for Jetbrains's PyCharm

**Note: pycharm-dpkg is deprecated, please use [package-jetbrains-ide](https://github.com/baderas/package-jetbrains-ide)!**


SYNOPSIS
--------

    ./build-package [-f <flavor>] [-v <version>] -u

DESCRIPTION
--------

`build-package` will create a platform-specific package of Jetbrains's
PyCharm. The packages can be installed using platform
specific/native tools and/or distributed from local package repositories.

It currently only supports building packages of the stable builds of PyCharm, 
either by downloading the latest version directly from Jetbrains's servers 
or by being pointed to a build output directory and use that.

This is a adopted version from trygvis's [intellij-idea-dpkg](https://github.com/trygvis/intellij-idea-dpkg)
with following limitations:
* No support for EAP version
* No support for Solaris Builds
* Professional Edition is untested (but implemented!)
* Only tested on Debian Jessie

OPTIONS
--------

* `-f <flavor>`

    The PyCharm flavor to package. 'flavor' can be one of 'professional' and 'community'
    for PyCharm Professional Edition or PyCharm Community Edition respectively.

    This option will be stored in `$HOME/.pycharm-dpkg` so you
    don't have to specifiy it in the next run.

* `-F`

    Force a build of a package, even if there is a package with the same
    version in the repository.

* `-s <directory>`

    Sets <directory> to be the input directory when creating the
    package. This is used to build packages from custom builds of PyCharm.

    Note that you have to specify the version explicitly.

* `-u`

    Updates the package repository with the appropriate command for
    the platform.

    For debian this means dpkg-scanpackages is used.

* `-v <version>`

    The version of the build to use. If not specified the script will
    automatically download the newest stable version.

EXAMPLES
-------

Example 1: Creating a package of the latest Community Edition.

    ./build-package

The flavor can be overridden with `-f`. This option will also be
remembered for the next run.

Example 2: Creating a Debian package of the 4.0.6 build of the Community Edition.

    ./build-package -f community -v 4.0.6

Example 3: Creating a Debian from a custom build of IDEA:

    ./build-package -f community -v 1.2.3 -s pycharm-community-1.2.3

BUGS
----

The scripts are not bullet proof, so there might certainly be bugs in
them. The scripts also depend on jetbrains to not change the way they
package and distribute the tar files.

This is just a first adoption of trygvis's [intellij-idea-dpkg](https://github.com/trygvis/intellij-idea-dpkg)
and works for me, but it is still very untested!

If you find a bug, please file a bug on GitHub:
http://github.com/baderas/pycharm-dpkg/issues

If you want to contribute, please add a pull request on GitHub:
http://github.com/baderas/pycharm-dpkg/pulls
