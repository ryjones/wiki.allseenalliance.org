FIXME: This page is out of date with respect to branch names.

# OpenWRT

AllJoyn feeds exist on the following OpenWRT platform releases:

*  v12.09 - official tagged release

*  Attitude Adjustment - current stable release

*  Barrier breaker - current development version

Follow the below instructions to add AllJoyn to your OpenWRT environment.

## Patch OpenSSL


*  For Attitude Adjustment, use [39585](https///dev.openwrt.org/browser/branches/attitude_adjustment?rev=39585) or later, or apply [patch 4802](http://patchwork.openwrt.org/patch/4802/) (The 12.09 tagged release requires this patch. The latest version on the Attitude Adjustment branch already has the patch applied.)


*  For Barrier Breaker, use [39048](https///dev.openwrt.org/browser?rev=39048) or later, or apply [patch 4576](http://patchwork.openwrt.org/patch/4576/) (The latest version of Barrier Breaker, aka trunk, already has the patch applied.)

Note: If you do not need to build Google tests be sure that GTEST_DIR is not defined during the build.

## Edit Feed

Add __**only one**__ of these lines to your feeds.conf:

	
	# For the official OpenWrt v12.09 tagged release
	src-git alljoyn https://git.allseenalliance.org/gerrit/core/openwrt_feed;openwrt_12.09
	
	# For Attitude Adjustment
	src-git alljoyn https://git.allseenalliance.org/gerrit/core/openwrt_feed;attitude_adjustment
	
	# For Barrier Breaker
	src-git alljoyn https://git.allseenalliance.org/gerrit/core/openwrt_feed;barrier_breaker


## Update Feeds

	
	./scripts/feeds update -a


## Install the AllJoyn package definitions

	
	./scripts/feeds install -a -p alljoyn


## Enable the AllJoyn packages to build

	
	make menuconfig
	        Networking --->
	                `< >` alljoyn --->
	                        `< >` alljoyn-about
	                        `< >` alljoyn-c
	                        `< >` alljoyn-config --->
	                                `< >` alljoyn-config-samples
	                        `< >` alljoyn-controlpanel --->
	                                `< >` alljoyn-controlpanel-samples
	                        `< >` alljoyn-notification --->
	                                `< >` alljoyn-notification-samples
	                        `< >` alljoyn-sample_apps
	                        `< >` alljoyn-services_common

