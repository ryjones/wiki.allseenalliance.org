# Lighting 15.04 Release Review

## Features


*  Controller Service support for top level Effect and Scene Element objects.

*  Controller Service support for optimized lamp data retrieval.

*  Bundled Controller Service support.

*  Verified against the 15.04b core and 15.04 base services releases.

*  For more information, please see the [Release Notes](#Release Notes).

## Software Release


*  [SDK Downloads](https///allseenalliance.org/framework/download)

*  [Sample App 15.04 for Android (release build)](https///build.allseenalliance.org/lighting/view/v15_04/job/Lighting_Sample_App_Android_v15_04/5/LABEL=rac-ord-asa-ci-android-1,MODE=alliance,VARIANT=release/) (the  [debug build](https///build.allseenalliance.org/lighting/view/v15_04/job/Lighting_Sample_App_Android_v15_04/5/LABEL=rac-ord-asa-ci-android-1,MODE=alliance,VARIANT=debug/) is also available)

*  [Sample App 15.04 for iOS (unsigned)](https///build.allseenalliance.org/lighting/view/v15_04/job/Lighting_Sample_App_iOS_v15_04/2/)

*  [LSF Binaries 15.04 for Linux (Ubuntu v14.04 LTS 64-bit)](https///build.allseenalliance.org/lighting/view/v15_04/job/Lighting_Service_Framework_LSF_v15_04/16/)

## Non-Code Aspects

### General Documentation:

*  [Connected Lighting](https///wiki.allseenalliance.org/tsc/connected_lighting)

*  [API Reference](https///allseenalliance.org/framework/documentation/develop/api-reference)
### Release Notes:


*  [Service Framework](https///git.allseenalliance.org/cgit/lighting/service_framework.git/tree/ReleaseNotes.txt?id=v15.04)

*  [Apps](https///git.allseenalliance.org/cgit/lighting/apps.git/tree/ReleaseNotes.txt?id=v15.04)

## Architectural Issues

There were no major architectural changes in this release.

## Security Issues

There were no major security-related changes in this release.

## Quality Assurance

### Feature Test

No feature test plans were needed for this release.

### Regression Test

The Lighting framework were tested successfully on the following platforms:

Lamp Service:


*  MQX 4.0.2 (MIPS)

*  Android Lollipop 5.1.1 (ARM)

*  Android KitKat 4.4.2 (ARM)

Controller Service:


*  OpenWRT-based (MIPS)

*  Android Lollipop 5.1.1 (ARM)

*  Android KitKat 4.4.2 (ARM)

*  iOS 8.4.1 (64/32-bit)

Controller Client: (via Sample Apps)

*  Android Lollipop 5.1.1 (ARM)

*  Android KitKat 4.4.2 (ARM)

*  iOS 8.4.1 (64/32-bit)
    
### Compliance Testing

The Lighting Controller Service passed compliance tests under the following scenario:


*  Test device: Nexus 5 with Android KitKat 4.4.2 (ARM) running the [Compliance Test Suite](https///build.allseenalliance.org/baseservices/view/BaseRB15.04_CoreRB15.04/job/Compliance_RB15.04/191/)

*  DUT(s): 
     * An OpenWRT-based platform running Controller Service, and 
     * Nexus 5 with Android KitKat 4.4.2 (ARM) running the Controller Service

The Lighting Lamp Service passed compliance tests under the following scenario:


*  Test device: Nexus 5 with Android KitKat 4.4.2 (ARM) running the [Compliance Test Suite](https///build.allseenalliance.org/baseservices/view/BaseRB15.04_CoreRB15.04/job/Compliance_RB15.04/191/)

*  DUT: Nexus 5 with Android KitKat 4.4.2 (ARM) running the Lamp Service

## Issues Addressed in 15.04

Please see the [Release Notes](#Release Notes) for the subset believed most relevant, or see the 
[complete list of addressed issues](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASALIGHT%20AND%20resolution%20%3D%20Fixed%20AND%20fixVersion%20%3D%20%2215.04%22).

## Known Issues

Please see the [Release Notes](#Release Notes) for the subset believed most relevant, or see the 
[complete list of known issues](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASALIGHT%20AND%20status%20in%20(Open%2C%20%22In%20Progress%22%2C%20Reopened%2C%20New)%20AND%20(%20affectedVersion%20in%20(%2215.04%22))).

## Compatibility

Please see the [Release Notes](#Release Notes).

## End-of-life

None.

## Standards Compliance

None.

## Schedule Post-Mortem

Various post-mortems are scheduled or will be scheduled.
