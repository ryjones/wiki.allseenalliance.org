# Base Services 14.06 Release Review


## Features

*  Onboarding Manager for Android + sample app

*  Onboarding client 1.0 for iOS

*  Onboarding improvements for Openwrt

*  Onboarding SDKs for iOs and Android

## Non-Code Aspects

[https://allseenalliance.org/developer-resources/alljoyn/docsdownloads](https///allseenalliance.org/developer-resources/alljoyn/docsdownloads)

## Architectural Issues

OpenWRT Onboarding service library has been replaced with a daemon application so that there is only a single instance of Onboarding app running on a device. During onboarding, the onboarding application restarts the AllJoyn Routing Node.
## Security Issues

None

## Quality Assurance

New features:

*  Events & Actions sample applications (Event Picker and Rule Engine)

*  Onboarding 1.0 OpenWRT Enhancements

*  IOS Onboarder

*  Onboarding manager SDK
Regression:

*  NS 1.1, Config, Control panel on Java, IOS, CPP and C (TCL) bindings

*  Onboarding on C (TCL), Java and IOS binding

*  Backwards compatibility against 14.02 services


## Known Issues

### Compatibility Issues


*  The Android Onboarding Manager is incompatible with 14.02 C++ Onboardee implementation (Openwrt). 

*  The Android Onboarding Manager is compatible with 14.02 Thin Client Onboardee implementation. 

*  C++/OpenWRT application using 14.02 are not compatible to Onboarding service 14.06. they need to deal with Alljoyn Routing Node restart.

### Bugs

*  [ASABASE-9](https///jira.allseenalliance.org/browse/ASABASE-9) Onboarding process to wep configured networks failed and the TP-LINK WR842ND stays in Soft AP mode.

*  [ASABASE-85](https///jira.allseenalliance.org/browse/ASABASE-85) The Java Onboarding server (simulator) is not receiving auto type ANY. 

*  [ASABASE-108](https///jira.allseenalliance.org/browse/ASABASE-108) Connecting WiFi network with Gingerbread Android version handset can take longer than on newer version of Android.

*  [ASABASE-189](https///jira.allseenalliance.org/browse/ASABASE-189) Onboarding Script Offboard method should delete key1 as well 

*  [ASABASE-207](https///jira.allseenalliance.org/browse/ASABASE-207) OpenWRT Onboarding Fail when 'Any' is passed to configure Method and RouterSSID is Hidden

*  [ASABASE-27](https///jira.allseenalliance.org/browse/ASABASE-27) Notification should not be sent when giving an empty/null value for the appID 

*  [ASABASE-34](https///jira.allseenalliance.org/browse/ASABASE-34) IOS: It is not possible to scroll down to the bottom notification and perform an action/dismiss on it 

*  [ASABASE-73](https///jira.allseenalliance.org/browse/ASABASE-73) Add notification + actions to ac sample app

*  [ASABASE-127](https///jira.allseenalliance.org/browse/ASABASE-127) Remove the addMatch method call from the application layer of the sample applications 

*  [ASABASE-134](https///jira.allseenalliance.org/browse/ASABASE-134) Align with changes made to aj_introspect.c where wildcard object path '*' was replaced with '!' 

*  [ASABASE-145](https///jira.allseenalliance.org/browse/ASABASE-145) Setting DeviceName does not take effect in some applications 

*  [ASABASE-169](https///jira.allseenalliance.org/browse/ASABASE-169) Notification sample app does not display CPS from notification with actions 

*  [ASABASE-181](https///jira.allseenalliance.org/browse/ASABASE-181) No need to set password for router now that it is open 

*  [ASABASE-15](https///jira.allseenalliance.org/browse/ASABASE-15) command line parameters in Service Server Sample Application are ignored 

*  [ASABASE-209](https///jira.allseenalliance.org/browse/ASABASE-209) C++ AppID Is not Unique between same App Different Runs

*  [ASABASE-231](https///jira.allseenalliance.org/browse/ASABASE-231) Config client crashes on gingerbread android version
## End-of-life

None
## Standards Compliance

None
## Schedule Post-Mortem

Various post-mortems are scheduled or will be scheduled.

