# OpenWrt Package Development

The OpenWrt feed for AllJoyn is contained this git repository: https://git.allseenalliance.org/cgit/core/openwrt_feed.git/

## OpenWrt Setup

This assumes that you have the latest development version of the OpenWrt source build system downloaded and built once already for your desired target platform.  You can get full setup instructions from the [Build AllJoyn for OpenWrt](build_alljoyn_for_openwrt) page.

### Adding the AllJoyn Feed

If you do not have a ''feeds.conf'' file, create one by copying ''feeds.conf.default'' to ''feeds.conf''.  Add the following lines to your ''feeds.conf'' file:

`<file>`
src-git alljoyn_dev https://git.allseenalliance.org/gerrit/core/openwrt_feed
`</file>`


## Building Alternate Versions of AllJoyn Source

The package defintion Makefiles for AllJoyn in the master branch of the core/openwrt_feed.git repository do not reference any files that can be downloaded and built.  Therefore, you will need to use OpenWrt's source override mechanism in order to build source code you have on your local machine.  The instructions on this page are derived from
[http://wiki.openwrt.org/doc/devel/packages](http://wiki.openwrt.org/doc/devel/packages).

 1.  Checkout the branch you wish to build in your local copy of the git repository
 2.  Update your feed: ''./scripts/feed update alljoyn_dev''
 3.  Create a symbolic link to the .git directory of your source code:\\ ''ln -s /path/to/your/copy/of/the/git/repository/with/your/code/.git feeds/alljoyn_dev///`<package_name>`///git-src''
 4.  Install your package definition into the OpenWrt build system: ''./scripts/feeds install *`<package_name>`*''
 5.  Start ''make menuconfig''
 6.  Enable ''[*] Advanced configuration options (for developers)  --->''
 7.  Under that, enable ''[*]   Enable package source tree override''
 8.  Ensure that your package is enabled to be built
 9.  Exit ''make menuconfig'' saving your changes
 10.  Build your package: ''make package///`<package_name>`///{clean,compile}''

Note that this will only build the code that is currently checked into HEAD.  That means uncommitted changes sitting in your workspace will **not** be built.

## Anatomy of a Package Definition

### Example Makefile

FIXME To be written...

