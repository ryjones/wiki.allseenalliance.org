# AllJoyn.js Version 15.04 Release Notes

## Fully Validated Platforms

 1.  Linux Ubuntu 14.04 LTS (64 bit)

See the [release review page](alljoyn-js/alljoyn.js_15.04_release_review) for the current state of other platforms that have
not been verified.

## Features added in Version 15.04

This is the first official release of AllJoyn.js, what follows is an overview of
the project and its features 

AllJoyn.js integrates AllJoyn Thin Client with Base Services and the Duktape JavaScript engine and runtime environment. The Duktape JS engine has support for full ECMAScript 5.0 features as well as some borrowed features from the E6 draft. AllJoyn.js includes two high level modules, AllJoyn and IO. The AllJoyn module provides wrappers for Thin Client functionality like making method calls, sending signals, getting/setting properties. It also provides API’s for base services functionality including Control Panel, Config, Notification, and Onboarding. The IO module exposes API’s to manipulate real hardware like GPIO, PWM, ADC, DAC, I2C, SPI, and UART (Note: This functionality is platform specific and dependent on the target's BSP). AllJoyn.js also supports real time debugging, exposed via an AllJoyn interface, which allows you to set breakpoints, step line by line through code, evaluate JS on the fly, and manipulate variables in real time.

Other features include:

*  Over-the-air script installation

*  Lockdown feature for product deployment and security

*  Console service to interact with an AllJoyn.js device

*  Python GUI debugger (using the console service)

*  100% event driven, non-blocking

*  Low memory footprint (128K RAM minimum, 500K flash minimum)

[Additional details listed in the Release Plan wiki page](alljoyn-js/alljoyn.js_15.04_release_plan)

## Issues Addressed in Version 15.04

This is the first release.

[Complete list of fixed issues](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASACORE%20AND%20component%20%3D%20%22AllJoyn%20JS%22%20AND%20status%20%3D%20Closed )

## Known Issues in Version 15.04


*  ASACORE-2330 AllJoyn.js Python debugger does not build on windows (without hack)

*  ASACORE-2317 add alljoyn.js content

*  ASACORE-2224 Update AllJoyn.js console to run against SC master

*  ASACORE-2085 AllJoyn JS does not allow you to connect to a specific device ID or app name.

*  ASACORE-2074 alljoynjs timer drift over time

*  ASACORE-2052 alljoynjs crashed with POOL_MALLOC

*  ASACORE-1496 Dynamic allocation inconsistency in alljoyn-js table handling

[Complete list of open issues](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASACORE%20AND%20component%20%3D%20%22AllJoyn%20JS%22%20AND%20status%20in%20(Open%2C%20%22In%20Progress%22%2C%20New))

## Compatibility

This is the initial Alljoyn.js release, and as such doesn't have any
compatibility issues with previous versions.  However, it is dependent on the following
components and versions.

*  AllJoyn Thin Client 15.04b

*  Base Services 15.04

*  Duktape 1.2.1


## Change history


*  15.04 - Initial release

