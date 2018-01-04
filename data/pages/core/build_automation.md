# Core Build Automation

Build automation for core projects is implemented at https://build.allseenalliance.org/ci/

Each change that is [contributed](develop/Contributing Source Code) to a core project goes through a [verification build](https///build.allseenalliance.org/ci/view/verify/).

In general, the builds are done with default values in an environment like that specified in the [Developer Guides](https///allseenalliance.org/developer-resources). Whitespace checks are on by default.

Current builds are:

*  [core/alljoyn.git](https///git.allseenalliance.org/gerrit/#/admin/projects/core/alljoyn)
    * Windows - VS2012 x64, Server 2012
      * `scons -j 8 MSVC_VERSION=11.0 V=1 OS=win7 CPU=x86_64 BINDINGS=c,cpp,java WS=off DOCS=html BR=on VARIANT=debug`
    * OS X 10.8 - Xcode 5.1.1
      * `xcodebuild -project alljoyn_darwin.xcodeproj -scheme alljoyn_core_osx -configuration Debug`
    * Linux - Ubuntu 12.04 x64 with kernel 3.2
      * `scons -j 8 OS=linux CPU=x86_64 VARIANT=debug BINDINGS=c,cpp,java WS=check DOCS=html BR=off POLICYDB=off`

*  [core/ajtcl.git](https///git.allseenalliance.org/gerrit/#/admin/projects/core/ajtcl)
    * Windows - VS2012 x64, Server 2012
      * `scons -j 8 MSVC_VERSION=11.0 OS=win7 CPU=x86 WS=off VARIANT=release`
    * Linux - Ubuntu 12.04 x64 with kernel 3.2
      * `<code>`scons -j 8 OS=linux CPU=x86_64 VARIANT=debug
scons -c
scons -j 8 OS=linux CPU=x86_64 VARIANT=release`</code>`


