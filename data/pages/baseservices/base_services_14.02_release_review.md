# Base Services 14.02 Release Review

## Features


*  Notification dismiss – Ability to propagate a notification dismiss to all devices on the proximal network

*  Notifications - detect Super Agent dropping off network

*  iOS Bindings for Control Panel, Config, and Notification services

*  Refactoring/reorganization of thin client service code and samples
## Non-Code Aspects

AllSeen Base Services documentation to be updated. See allseen.org
## Architectural Issues

None

## Security Issues

No changes
## Quality Assurance


Following AllJoyn Services QA: 
Notification Service	
Control Panel Service	
Onboarding Service	
Config Service		
About Service		

included comprehensive testing on the following components:
 Ubuntu 12.04	Android JB	iOS 7	OpenWRT	
## Known Issues

__Onboarding__ 

*  TPLink (trunk), Onboarding to WIFI with WEP Shared Key fails. Irrespective of the onboarding service, joining a wep(shared) network doesn't work on the TP-link.

*  CPP , There is no option in the config file to provision the Soft AP as hidden.

*  CPP, wifi passwords with spaces are not handled properly.

*  TPLink (trunk) -  The OpenWRT/TPLink842ND does not retain a unique Soft AP name. In 10-20% of the cases it shows a generic name that does not include the mac address id.

__Config__

*  CPP,ThinClient – DeviceName does not support multi languages.

*  ThinClient - Updating configuration to an unsupported field should throw org.alljoyn.Error.InvalidValue Exception.

*  ThinClient - Exception is not sent when changing deviceName to empty. 

*  ThinClient - Exception is not sent when changing the default language to empty. 

*  ThinClient - Exception is not sent when changing the deviceId. 

*  CPP- org.alljoyn.Error.LanguageNotSupported exception  is not sent  when SetConfig is called with an Invalid language .

## End-of-life

N/A
## Standards Compliance

N/A
## Schedule Post-Mortem

TBD
