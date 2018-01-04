# Lighting 14.12 Release Review

## Features


*  Support for the 14.12 About framework in core.

*  Verified against the 14.12b core and 14.12 base services releases.

*  Added OpenWRT BB & CC Controller Service reference builds in [Jenkins](https///build.allseenalliance.org/lighting/view/v14_12/)

*  For more information, please see the [Release Notes](#Release Notes).

## Software Release


*  [SDK Downloads](https///allseenalliance.org/developers/download)

*  [Sample App 14.12 for Android](https///build.allseenalliance.org/lighting/view/v14_12/job/Lighting_Sample_App_Android_v14_12/12/artifact/release/LSFSampleApp_Android_14_12_debug.apk)

*  [Sample App 14.12 for iOS (unsigned)](https///build.allseenalliance.org/lighting/view/v14_12/job/Lighting_Sample_App_iOS_v14_12/10/artifact/release/LSFSampleApp.ipa)

*  [LSF Binaries 14.12 for Linux (Ubuntu v14.04 LTS 64-bit)](https///build.allseenalliance.org/lighting/view/v14_12/job/Lighting_Service_Framework_LSF_v14_12/13/artifact/release/service_framework_linux_x64_14_12.zip)

## Non-Code Aspects

### General Documentation:

*  [Connected Lighting](https///wiki.allseenalliance.org/tsc/connected_lighting)

*  [API Reference](https///allseenalliance.org/developers/develop/api-reference)
### Release Notes:


*  [Service Framework](https///git.allseenalliance.org/cgit/lighting/service_framework.git/tree/ReleaseNotes.txt?id=v14.12)

*  [Apps](https///git.allseenalliance.org/cgit/lighting/apps.git/tree/ReleaseNotes.txt?id=v14.12)

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

*  Android KitKat 5.0 (ARM)

*  Android KitKat 4.4.2 (ARM)

Controller Service:


*  OpenWRT-based (MIPS)

*  Android KitKat 5.0 (ARM)

*  Android KitKat 4.4.2 (ARM)

Controller Client: (via Sample Apps)

*  Android KitKat 5.0 (ARM)

*  Android KitKat 4.4.2 (ARM)

*  iOS 7.1.1 (32-bit)
    
### Compliance Testing

The Lighting Controller Service passed compliance tests under the following scenario:


*  Test device: Nexus 5 with Android KitKat 4.4.2 (ARM) running the [Compliance Test Suite](https///build.allseenalliance.org/baseservices/view/BaseRB14.12_CoreRB14.12/job/Compliance_base-services_RB14.12/103/artifact/tests/java/components/validation-tests/HEAD/validation-tests-it/target/validation-tests-it-14.12.01-SNAPSHOT.apk)

*  DUT(s): 
     * An OpenWRT-based platform running Controller Service, and 
     * Nexus 5 with Android KitKat 4.4.2 (ARM) running the Controller Service

The Lighting Lamp Service passed compliance tests under the following scenario:


*  Test device: Nexus 5 with Android KitKat 4.4.2 (ARM) running the [Compliance Test Suite](https///build.allseenalliance.org/baseservices/view/BaseRB14.12_CoreRB14.12/job/Compliance_base-services_RB14.12/103/artifact/tests/java/components/validation-tests/HEAD/validation-tests-it/target/validation-tests-it-14.12.01-SNAPSHOT.apk)

*  DUT: Nexus 5 with Android KitKat 4.4.2 (ARM) running the Lamp Service

## Issues Addressed in 14.12

Please see the [Release Notes](#Release Notes) for the subset believed most relevant, or see the 
[complete list of addressed issues](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASALIGHT%20AND%20resolution%20%3D%20Fixed%20AND%20fixVersion%20%3D%20%2214.12%22).

## Known Issues

Please see the [Release Notes](#Release Notes) for the subset believed most relevant, or see the 
[complete list of known issues](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASALIGHT%20AND%20status%20in%20(Open%2C%20%22In%20Progress%22%2C%20Reopened%2C%20New)%20AND%20(%22Release%20Version%20Found%20In%22%20%3D%20%2214.12%22%20OR%20affectedVersion%20in%20(%2214.12%22))).

## Compatibility

Please see the [Release Notes](#Release Notes).

## End-of-life

None.

## Standards Compliance

None.

## Schedule Post-Mortem

Various post-mortems are scheduled or will be scheduled.
