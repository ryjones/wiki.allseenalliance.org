# Base Services 14.12 Release Review

## Features


*  Support for the 14.12 About framework in core.

*  Verified against the 14.12a core releases.

*  Added Windows releases for standard and thin client, 32 and 64-bit.

*  For more information, please see the [Release Notes](#Release Notes).

## Software Release


*  [Downloads](https///allseenalliance.org/developers/download)

*  [API Reference](https///allseenalliance.org/developers/develop/api-reference)

## Non-Code Aspects

### General Documentation


*  [Base Services](https///allseenalliance.org/developers/learn/base-services)

### Release Notes:


*  [Onboarding](https///git.allseenalliance.org/cgit/services/base.git/tree/onboarding/ReleaseNotes.txt?id=v14.12)

*  [ Configuration](https///git.allseenalliance.org/cgit/services/base.git/tree/config/ReleaseNotes.txt?id=v14.12)

*  [Notification](https///git.allseenalliance.org/cgit/services/base.git/tree/notification/ReleaseNotes.txt?id=v14.12)

*  [Control Panel](https///git.allseenalliance.org/cgit/services/base.git/tree/controlpanel/ReleaseNotes.txt?id=v14.12)

*  [Thin Client](https///git.allseenalliance.org/cgit/services/base_tcl.git/tree/ReleaseNotes.txt?id=v14.12)

## Architectural Issues

There were no major architectural changes in this release.

## Security Issues

There were no major security-related changes in this release.

## Quality Assurance

### Feature Test

No feature test plans were needed for this release.

### Regression Test

The base services standard client frameworks were tested successfully on the following platforms:


*  Linux Ubuntu v14.04 LTS (64-bit)

*  Android JellyBean 4.1 (ARM)

*  iOS 7.1 (32-bit)
    
The base services thin client frameworks were tested successfully on the following platforms:


*  Linux Ubuntu v14.04 LTS (64-bit)

### Compliance Testing

The base services standard client framework passed compliance testing for Config, ControlPanel, Notification, and Onboarding under the following scenario:


*  Test device: Nexus 5 with Android KitKat 4.4.2 (ARM) running [Compliance Test Suite v14.12](https///build.allseenalliance.org/baseservices/view/BaseV14.12_CoreV14.12a/job/Compliance_base-services_V14.12/3/)

*  DUT: TP-Link TL-WR842ND Ver2.1 running [ACServerSample v14.12, ConsumerSample v14.12, and OnboardingDaemon v14.12](https///build.allseenalliance.org/baseservices/view/BaseV14.12_CoreV14.12a/job/OpenWRT_BB_base-services_V14.12/5/) (under OpenWRT Barrier Breaker)

The base services thin client framework passed compliance testing for Config, ControlPanel, and Notification under the following scenario:


*  Test device: Nexus 5 with Android KitKat 4.4.2 (ARM) running [Compliance Test Suite v14.12](https///build.allseenalliance.org/baseservices/view/BaseV14.12_CoreV14.12a/job/Compliance_base-services_V14.12/3/)

*  DUT: Linux Ubuntu v14.04 LTS 64-bit running [ACServerSample v14.12 and NotificationConsumerSample v14.12](https///build.allseenalliance.org/baseservices/view/BaseV14.12_CoreV14.12a/job/linux-tcl-services_V14.12/4/)

## Issues Addressed in 14.12

Please see the [Release Notes](#Release Notes) for the subset believed most relevant, or see the 
[complete list of addressed issues](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASABASE%20AND%20resolution%20%3D%20Fixed%20AND%20fixVersion%20%3D%20%2214.12%22).

## Known Issues

Please see the [Release Notes](#Release Notes) for the subset believed most relevant, or see the 
[complete list of known issues](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASABASE%20AND%20labels%20%3D%20%22Known_Issues_in_14.12%22).

## Compatibility

Please see the [Release Notes](#Release Notes).

The Services/About APIs are deprecated.

## End-of-life

None
## Standards Compliance

None.

## Schedule Post-Mortem

Various post-mortems are scheduled or will be scheduled.
