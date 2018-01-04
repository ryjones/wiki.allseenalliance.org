# Core 15.09 Release Review

## Updates

Patch releases were made to the both the Standard Core and Thin Core projects after the initial 15.09 release: 15.09a.  The details of the changes are listed in the Change History section of the [Standard Core release notes](https///git.allseenalliance.org/cgit/core/alljoyn.git/tree/alljoyn_core/docs/ReleaseNotes.txt?h=RB15.09) and [Thin Core release notes](https///git.allseenalliance.org/cgit/core/ajtcl.git/tree/ReleaseNotes.txt?h=RB15.09).
## Non-Code Aspects


*  [Documents](https///allseenalliance.org/developer-resources/alljoyn/docsdownloads)

*  [Building and Running](develop/building_and_running)

*  [Training](/training)

## Features, Issues Addressed and Known Issues

Please see the [Standard Core release notes](https///git.allseenalliance.org/cgit/core/alljoyn.git/plain/alljoyn_core/docs/ReleaseNotes.txt?h=RB15.09) and [Thin Core release notes](https///git.allseenalliance.org/cgit/core/ajtcl.git/tree/ReleaseNotes.txt?h=RB15.09) for the most relevant details.

For a complete list of Features check this [Core Jira query](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASACORE%20AND%20issuetype%20%3D%20%22New%20Feature%22%20AND%20fixVersion%20%3D%20%2215.09%22%20AND%20status%20%3D%20Closed).

For a complete list of closed issues check this [Core Jira query](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASACORE%20AND%20resolution%20in(done%2C%20fixed)%20AND%20TYPE%20in%20(Bug)%20and%20fixVersion%20in%20(%2215.09%22)%20ORDER%20BY%20priority%20DESC%2C%20key%20ASC). *Note*: this includes all bugs filed including issues filed as a result of changes between the last release and this one.

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
    * Android Lollipop 5.0 (ARM)
    * OpenWRT Barrier Breaker (BB) branch
    * OpenWRT Chaos Calmer (CC) branch

*  Smoke test
    * Android JellyBean 4.1 (ARM)
    * Android KitKat 4.4 (ARM)

AllJoyn Thin Library was tested successfully on the following:


*  Full regression test
    * Linux Ubuntu 14.04 LTS (64 bit)


##  Toolchains used to build SDKs

 | SDK                          | Toolchain Used                  | 
 | ---                          | --------------                  | 
 | alljoyn-15.04.00-src.tar.gz  | N/a - source                    | 
 | ajtcl-15.04.00-src.tar.gz    | N/a - source                    | 
 | Core SDK - release (android) | Android NDK r10e, Oracle Java 7 | 
 | Core SDK - debug (android)   | Android NDK r10e, Oracle Java 7 | 

## Architectural Issues

The Security 2.0 feature ([ASACORE-1393](https///jira.allseenalliance.org/browse/ASACORE-1393)) introduces a whole new model and architecture for enabling security to AllJoyn enable IoT applications/devices.  Details can be found on the [Security 2.0 wiki page](security_enhancements).

The ARDP/UDP Transport for TC `<->` RN connections ([ASACORE-1686](https///jira.allseenalliance.org/browse/ASACORE-1686)) allows AllJoyn TC applications to connect to the routing node using the ARDP protocol which is less resource intensive on the routing node than using TCP, thus allowing for a larger number of connections.  This has be made the default transport for TC applications; however, fall-back to TCP will happen should the ARPD connection fail to be established.

## Security Issues

[Security Enhancements](Security Enhancements) ([ASACORE-1393](https///jira.allseenalliance.org/browse/ASACORE-1393))
 feature was added

## Compatibility

See the [compatibility section in the Release Plan](core_15.09_release_plan#compatibility_with_previous_releases) for details on compatibility.

## End-of-life

N/A

## Post-Mortem

Post-mortem was held on December 15th: {{:core:core_wg_1509_post_mortem.pdf|Meeting Notes}} [WebEx Recording](https///meetings.webex.com/collabs/#/files/detail?fileID=O37WAEA9L6XWIMFIG5PGQKH4YT-HIZ3&containerID=UCJD4O38TYYWNXMWVUZXYISO88-HIZ3&containerType=us).

