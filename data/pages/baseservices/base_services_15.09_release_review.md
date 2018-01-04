# Base Services 15.09 Release Review

## Features


*  The Onboarding service is included in this release, but it is not tested or supported.

*  The Control Panel service source code is available in the source code repository, but it is not included in this release, and it is not tested or supported.

*  The (experimental) Time service source code has been moved to the [feature/time](https///git.allseenalliance.org/cgit/services/base.git/tree/time?h=feature/time) branch.

*  Verified against the 15.09a AllJoyn Core release.

*  For more information, please see the [Release Notes](#Release Notes).

## Software Release


*  [Downloads](https///allseenalliance.org/framework/download)

*  [API Reference](https///allseenalliance.org/framework/documentation/develop/api-reference)

## Non-Code Aspects

### General Documentation


*  [Base Services](https///allseenalliance.org/framework/documentation/learn/base-services)

### Release Notes:


*  [ Configuration](https///git.allseenalliance.org/cgit/services/base.git/tree/config/ReleaseNotes.txt?id=v15.09)

*  [Notification](https///git.allseenalliance.org/cgit/services/base.git/tree/notification/ReleaseNotes.txt?id=v15.09)

*  [Onboarding](https///git.allseenalliance.org/cgit/services/base.git/tree/onboarding/ReleaseNotes.txt?id=v15.09)

*  [Thin Client](https///git.allseenalliance.org/cgit/services/base_tcl.git/tree/ReleaseNotes.txt?id=v15.09)

## Architectural Issues

There were no major architectural changes in this release.

## Security Issues

This release does not support the Security 2.0 feature introduced in AllJoyn Core.

There were no major security-related changes in this release.

## Quality Assurance

### Feature Test

No feature test plans were needed for this release.

### Regression Test

The base services standard client frameworks were tested successfully on the following platforms:


*  Linux Ubuntu v14.04 LTS (64-bit)

*  Android KitKat 4.4.2 (ARM)
    
The base services thin client frameworks were tested successfully on the following platforms:


*  Linux Ubuntu v14.04 LTS (64-bit)

### Compliance Testing

The base services standard client framework passed compliance testing for Config and Notification under the following scenario:


*  Test device: Nexus 5 with Android KitKat 4.4.2 (ARM) running [Compliance Test Suite v15.09](https///build.allseenalliance.org/baseservices/view/BaseV15.09_CoreV15.09a/job/BaseV15.09_CoreV15.09a_ComplianceServicesV15.09_Android/2/)

*  DUT: Linux Ubuntu v14.04 LTS 64-bit running [ConfigService v15.09, ConsumerService v15.09, and ProducerService v15.09](https///build.allseenalliance.org/baseservices/view/BaseV15.09_CoreV15.09a/job/BaseV15.09_CoreV15.09a_SC_Linux/2/)

The base services thin client framework passed compliance testing for Config and Notification under the following scenario:


*  Test device: Nexus 5 with Android KitKat 4.4.2 (ARM) running [Compliance Test Suite v15.09](https///build.allseenalliance.org/baseservices/view/BaseV15.09_CoreV15.09a/job/BaseV15.09_CoreV15.09a_ComplianceServicesV15.09_Android/2/)

*  DUT: Linux Ubuntu v14.04 LTS 64-bit running [NotifConfig v15.09](https///build.allseenalliance.org/baseservices/view/BaseV15.09_CoreV15.09a/job/BaseV15.09_CoreV15.09a_TCL_Linux/2/)

## Issues Addressed in 15.09

Please see the [Release Notes](#Release Notes) for the subset believed most relevant, or 
[search for addressed issues](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASABASE%20AND%20resolution%20%3D%20Fixed%20AND%20fixVersion%20%3D%20%2215.09%22).

## Known Issues

Please see the [Release Notes](#Release Notes) for the subset believed most relevant, or 
[search for known issues](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASABASE%20AND%20status%20in%20(Open%2C%20%22In%20Progress%22%2C%20Reopened%2C%20New%2C%20%22Monitor%20%2F%20On%20Hold%22)%20AND%20fixVersion%20in%20(15.09a%2C%20%22Next%20Major%20Release%22)).

## Compatibility

Please see the [Release Notes](#Release Notes).

## End-of-life

None

## Standards Compliance

None

## Schedule Post-Mortem

Various post-mortems are scheduled or will be scheduled.
