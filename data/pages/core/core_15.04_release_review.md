

# Core 15.04 Release Review

## Updates
Patch releases were made to the both the Standard Core and Thin Core projects after the initial 15.04 release: 15.04a and 15.04b.  The details of the changes are listed in the Change History section of the [Standard Core release notes](https///git.allseenalliance.org/cgit/core/alljoyn.git/tree/alljoyn_core/docs/ReleaseNotes.txt?h=RB15.04) and [Thin Core release notes](https///git.allseenalliance.org/cgit/core/ajtcl.git/tree/ReleaseNotes.txt?h=RB15.04). 

## Non-Code Aspects


*  [Documents](https///allseenalliance.org/developer-resources/alljoyn/docsdownloads)

*  [Building and Running](develop/building_and_running)

*  [Training](/training)

## Features, Issues Addressed and Known Issues

Please see the [Standard Core release notes](https///git.allseenalliance.org/cgit/core/alljoyn.git/plain/alljoyn_core/docs/ReleaseNotes.txt?h=RB15.04) and [Thin Core release notes](https///git.allseenalliance.org/cgit/core/ajtcl.git/tree/ReleaseNotes.txt?h=RB15.04) for the most relevant details.

For a complete list of Features check this [Core Jira query](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASACORE%20AND%20issuetype%20%3D%20%22New%20Feature%22%20AND%20fixVersion%20%3D%20%2215.04%22%20AND%20status%20%3D%20Closed).

For a complete list of closed issues check this [Core Jira query](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASACORE%20AND%20resolution%20in%28done%2C%20fixed%29%20AND%20TYPE%20in%20%28Bug%29%20and%20fixVersion%20in%20%28%2215.04%22%2C%20%2215.04a%22%2C%20%2215.04b%22%29%20ORDER%20BY%20priority%20DESC%2C%20key%20ASC). *Note*: this includes all bugs filed including issues filed as a result of changes between the last release and this one.

For a complete list of open issues check this [Core Jira query](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASACORE%20AND%20resolution%3DUnresolved%20AND%20TYPE%20in%20%28Bug%2C%20Task%29%20ORDER%20BY%20priority%20DESC%2C%20key%20ASC).


## Quality Assurance

We have a layered approach to testing that starts with verifying core functionality, such as messaging and security. Then, we execute platform-specific tests for each of the platforms listed above. This includes testing of transports, bindings, sample applications, as well as stress testing. We also conduct interoperability testing to ensure that, for example, AllJoyn applications running on a Windows laptop can interact with applications running on an Android phone. Finally, we do backward compatibility testing to ensure, for example, that a new routing node will communicate with an older routing node. 

Issues identified during testing are documented in our bug tracking system. A triage process assigns the bugs a priority and a release target. Naturally, the highest priority bugs are targeted for the next release. Once a bug has been resolved-fixed, then the bug fix is verified, and the bug is closed. 

### Feature Test

Feature test plans were completed for all of the major new features cited in the release notes referenced [above](#features_issues_addressed_and_known_issues).

### Regression Test

AllJoyn Standard Library was tested successfully on the following:


*  Full regression test
    * Linux Ubuntu 14.04 LTS (64 bit)
    * Windows 7/8.1 (64 bit)
    * Android JellyBean 4.1 (ARM)
    * iOS 8.1 (64-bit)
    * OSX 10.9 Lion
    * OpenWRT Barrier Breaker (BB) and Chaos Calmer (CC) branches

*  Smoke test
    * Android KitKat 4.4 (ARM)
    * Android Lollipop 5.0 (ARM)
    * iOS 8.2, 8.3 (64-bit)

AllJoyn Thin Library was tested successfully on the following:


*  Full regression test
    * Linux Ubuntu 14.04 LTS (64 bit)
    * Windows 7 (64 bit)


*  Developer ported platforms
    * OSX
    * STM32F407 (F4 Discovery board) with FreeRTOS
    * FRDM-K64F (Freescale Freedom board) with mbed


##  Toolchains used to build SDKs

 | SDK                           | Toolchain Used                    | 
 | ---                           | --------------                    | 
 | alljoyn-15.04.00-src.tar.gz   | N/a - source                      | 
 | ajtcl-15.04.00-src.tar.gz     | N/a - source                      | 
 | Core SDK - release (android)  | Android NDK r9d, Oracle Java 7    | 
 | Core SDK - debug (android)    | Android NDK r9d, Oracle Java 7    | 
 | Core SDK (osx/ios)            | Xcode 6.1                         | 
 | Windows SDK (64-bit) (VS2012) | Visual Studio 2012, Oracle Java 7 | 
 | Windows SDK (32-bit) (VS2012) | Visual Studio 2012, Oracle Java 7 | 
 | Windows SDK (64-bit) (VS2013) | Visual Studio 2013, Oracle Java 7 | 
 | Windows SDK (32-bit) (VS2013) | Visual Studio 2013, Oracle Java 7 | 
 | Windows Thin Core SDK         | Visual Studio 2013                | 
    

## Architectural Issues

There were no major architectural changes to the AllJoyn Core software.

## Security Issues

Support for x.509 ECC digital certificates were added, and support for RSA was removed.  See the [compatibility section in the Release Plan](core_15.04_release_plan#compatibility_with_previous_releases) for more details on the security changes.

## Compatibility

See the [compatibility section in the Release Plan](core_15.04_release_plan#compatibility_with_previous_releases) for details on compatibility.

## End-of-life


*  The Legacy Services/About APIs are deprecated.

*  Several APIs were deprecated in relation to the [ASACORE-1522](https///jira.allseenalliance.org/browse/ASACORE-1522) work.

*  Various transport masks were deprecated.  This work was originally part of 14.12b, but given the timing was close to this release it is being mentioned here. This work was captured in [ASACORE-1504](https///jira.allseenalliance.org/browse/ASACORE-1504).

*  RSA support was removed (as indicated in the [#security_issues](#security_issues) section above).
## Post-Mortem

The post mortem was held 6/22/15 @ 1PM PDT. {{:core:allseen-corewg_15-04_post_mortem.pdf|Post Mortem Meeting Slides}} [WebEx Recording](https///meetings.webex.com/collabs/url/9lIHQSNGgSoWkDxlwO5BC3rxHrqjguiu9Sti_NBmFAe00000)


