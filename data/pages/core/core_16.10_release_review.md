# Core 16.10 Release Review

## Updates

None
 
## Non-Code Aspects


*  [Documents](https///allseenalliance.org/developer-resources/alljoyn/docsdownloads)

*  [Building and Running](develop/building_and_running)

*  [Training](/training)

## Features, Issues Addressed and Known Issues

Please see the [Standard Core release notes](https///git.allseenalliance.org/cgit/core/alljoyn.git/plain/alljoyn_core/docs/ReleaseNotes.txt?h=RB16.10) and [Thin Core release notes](https///git.allseenalliance.org/cgit/core/ajtcl.git/tree/ReleaseNotes.txt?h=RB16.10) for the most relevant details.

For a complete list of Features check this [Core Jira query](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASACORE%20AND%20issuetype%20%3D%20%22New%20Feature%22%20AND%20fixVersion%20%3D%20%2216.10%22%20AND%20status%20%3D%20Closed).

For a complete list of closed issues check this [Core Jira query](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASACORE%20AND%20resolution%20in(done%2C%20fixed)%20AND%20TYPE%20in%20(Bug)%20and%20fixVersion%20in%20(%2216.10%22)%20ORDER%20BY%20priority%20DESC%2C%20key%20ASC). *Note*: this includes all bugs filed including issues filed as a result of changes between the last release and this one.

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
    * OpenWRT Chaos Calmer (CC) branch
    * iOS
    * Windows 7 and 10

*  Smoke test
    * Android Lollipop 5.0 (ARM64)
    * OSX
    * Windows 8.1

AllJoyn Thin Library was tested successfully on the following:


*  Full regression test
    * Linux Ubuntu 14.04 LTS (64 bit)

*  Smoke test
    * Windows 10



## Architectural Issues

None

## Security Issues

[Security Enhancements](Security Enhancements) ([ASACORE-1393](https///jira.allseenalliance.org/browse/ASACORE-1393))
 feature is officially released!

## Compatibility

**SCL **

*  Security 2.0 developer and wire APIs have changed from the Developer Previewversions in 15.09 and 16.04

*  ASACORE-3353: Codegen'ed apps cannot interop with non-apps. An application that introspects and finds multiple annotations that are dependent on ordering (e.g., org.allJoyn.Bus.Struct.*) based on AllJoyn 16.04 should treat these annotations as unusable. To determine the AllJoyn framework version, an application can query the About data. This was fixed in 16.10.


**TCL**

*  Security 2.0 developer and wire APIs have changed from the Developer Previewversions in 15.09 and 16.04

## End-of-life

N/A

## Post-Mortem

December 15, 2016 {{:core:ajosp-corewg-12-15-16.pdf|Meeting Slides}}[WebEx Recording](https///oregonstate.webex.com/oregonstate/ldr.php?RCID=8eaf6285ea0628b131881fdd94e74123){{:core:16.10_retrospective_ai.pdf|Action Items}}
