# AllJoyn package release and maintenance process proposal

Alljoyn framework is a set of projects where each one follows it's own release cadence. There are major versions of the Core functionality, and the rest of the projects release on their own convenience for those versions afterwards.

This proposal aims to ease the involvement of both the community and non-leader companies within the development and the release process.

## State of the process and flaws

The workflow established in all projects mainly involve a main company carrying the development, and a series of contributors and interested companies on the process. Apart from the development process, one of the most important steps is the testing cadence and the release.

The testing is usually done by the leading company, and sometimes the documentation on how the format of the source code of the release will be is scarce. Also, as workgroups are independent from each other, the release tarball layout is usually really different. In the worst cases, tarballs include code that is not part of the workgroup's repositories, but added on when the release is created.

There are some usual defects on the release process that this proposal is aiming to address:

*  External builds scripts are usually referenced, in worst cases as mandatory dependencies

*  External projects are built, sometimes using those objects within the compilation of the targeted project

*  Linking to dynamic libraries is not an option if unavailable for compilation

*  Non standard layout is followed

Although these defects sometimes arise for manual compilation, because the reference layout of the git repos is sometimes not met, or the version of each dependency is not the one expected, the real problem is when you try to automate the compilation of Alljoyn. Specifically, this proposal has been written around all the difficulties that arise when packaging for Linux desktop systems and Openwrt.

## Proposal


### Step one: Tarball contents

When other projects are packaged, the contents of the release tarball and the contents of the release tagged in the source version control tree should be *exactly the same*. This is really important because it allows to generate release packages from the source tree in a programmatic and standard way (using git archive for example). This has a series of implications on the git repository:

 1.  All the build scripts the project *mandatorily* relies on must be within the git source. In most of the cases, this would mean copying the referenced build scripts to the project tree.
 2.  External build scripts that are *optional* should be optionally compiled using some flag to enable their compilation.
 3.  External objects to the tree should not be used within the compilation. In scons this means that a new env should be created for/from them, without adding them to the project environment.
 4.  External distribution directories should not be referenced. Instead use some generic argument to extend the linking path, the include path or whatever.
 5.  If a referenced library is a dependency, it should be linked if not available for compilation


As you may observe, the first step is to make modular the projects. This will allow a packager to create packages of the alljoyn framework separately, and without possible ABI issues.

### Step two: Input and Output

Once the projects are independently buildable from each other, in order to make it easier for the packager (and the rest of the users) to compile the software, the projects should have the same input and output. This means that the same commands should do the same in all projects with this Step 2 implemented.

The input part is about how the user that is going to build the software decides about the configuration he wishes to apply. For example, specifying if the alljoyn-router should be compiled inside the binaries, being able to specify additional paths to look for, objects (alljoyn-router), libraries (other projects), binaries (packaging for gwagent), should be done the same way.

The proposed parameters would be the following:

 | Parameter           | Optional | Default                                  | Meaning                                                                                                                                                      | 
 | ---------           | -------- | -------                                  | -------                                                                                                                                                      | 
 | V                   | No       | 0                                        | Build verbosity                                                                                                                                              | 
 | VARIANT             | No       | debug                                    | Build variant, optimization level and debugging information generation                                                                                       | 
 | WS                  | No       | off                                      | Whitespace policy checker                                                                                                                                    | 
 | CC                  | No       | gcc                                      | Override the C compiler to use                                                                                                                               | 
 | CXX                 | No       | g++                                      | Override the CPP compiler to use                                                                                                                             | 
 | BUILD               | No       | samples,tests,java,cpp,ddapi,policydb,br | What to build, bindings, docs (pdf, html, etc.) and extra buildables (like tests or samples), support for X feature. Everything must be inside the same repo | 
 | EXTERNAL_BUILDS     | Yes      |                                          | This is the option that controls what external projects are built, folder project should be used, example, gwagent, base, alljoyn, etc.                      | 
 | ADDITIONAL_PREFIXES | No       |                                          | Additional prefixes to be added to the path, either binaries, libraries, sources etc. A generic way to expand path inclusion                                 | 

These variables are enough to contain most of the needed features for most projects.

**REVIEW: See if it's better to unify everything under BUILD, or separate by features to be compiled, taking into account that special stuff, like java version being used is left behind** 

The output part is about directory structure. Projects do usually use core/alljoyn/build_core, making the core build/ folder's layout the de-facto standard within the Alliance. This proposal wants to propose the following directory structure:

*  dist directory should contain distributables, distributed as they would be installed in a PREFIX with autotools

*  build directory should contain build objects (if any), replicating the **same** structure as in the root, prefixed by the VARIANT, this is src/main.c would generate build/debug/src/main.o.

*  headers should always have a path that is for the project and doesn't collide with others, TSC approving those prefixes (ajtcl/base, alljoyn/base, alljoyn/gwagent, etc.).

Here is a simplified version of the ajtcl proposed structure layout:

	
	% find dist
	dist
	dist/include
	dist/lib
	dist/bin
	dist/test
	
	% find build
	build
	build/debug
	build/debug/common
	build/debug/samples
	build/debug/src
	build/debug/src/crypto/
	build/debug/src/external/
	build/debug/src/target/
	build/debug/src/nvram/
	build/debug/src/malloc/
	build/debug/test
	build/debug/unit_test


As you can see, the number of folder levels is really trimmed down, and the separation between what should be installed in the system and what not is really clear. 
