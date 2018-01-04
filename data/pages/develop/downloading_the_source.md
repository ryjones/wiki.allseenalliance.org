# Downloading the Source

Download the source by using the repo tool (works on Linux and Mac) or by running individual git commands (works on all platforms).

Additionally, some platforms have additional details:

*  [OpenWRT](develop/openwrt)

## Download Using Repo

### Install Repo

Follow these instructions to [download the repo tool](http://source.android.com/source/downloading.html#installing-repo).

### Create Working Directory

	
	mkdir WORKING_DIRECTORY
	cd WORKING_DIRECTORY


### Init Repo Client

	
	repo init -u https://git.allseenalliance.org/gerrit/devtools/manifest


To sync with the most recent tags (including bugfix releases) for a given release number, e.g. [v14.06](release/14.06) or [v14.12](release/14.12):

	
	repo init -u https://git.allseenalliance.org/gerrit/devtools/manifest -b RB14.12 -m versioned.xml


Or, if you are working on a future release, run this to pull the tip from the release branch, e.g. RB15.04

	
	repo init -u https://git.allseenalliance.org/gerrit/devtools/manifest -b RB15.04


Note, you can safely ignore these "errors":

	
	curl: (22) The requested URL returned error: 404
	Server does not provide clone.bundle; ignoring.

### Download the Source

	
	repo sync


## Download Using Git

Run these commands to download the source by using individual git commands

	
	mkdir WORKING_DIRECTORY
	cd WORKING_DIRECTORY
	
	git clone https://git.allseenalliance.org/gerrit/core/alljoyn.git core/alljoyn
	git clone https://git.allseenalliance.org/gerrit/core/ajtcl.git core/ajtcl
	git clone https://git.allseenalliance.org/gerrit/services/base.git services/base
	git clone https://git.allseenalliance.org/gerrit/services/base_tcl.git services/base_tcl
	git clone https://git.allseenalliance.org/gerrit/data/datadriven_api.git data/datadriven_api
	git clone https://git.allseenalliance.org/gerrit/devtools/codegen.git devtools/codegen


Run these commands to optionally sync to a specific revision, like [v14.06](release/14.06) or [v14.02](release/14.02)

	
	export VER=v14.06
	git -C core/alljoyn checkout -b $VER $VER
	git -C core/ajtcl checkout -b $VER $VER
	git -C services/base checkout -b $VER $VER
	git -C services/base_tcl checkout -b $VER $VER
	
	# note on Windows, the commands look like this...
	set VER="v14.06"
	git -C core/alljoyn checkout -b %VER% %VER%
	

