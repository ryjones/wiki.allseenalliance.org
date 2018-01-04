## Designed for AllSeen: Appendices

[Return to Designed for AllSeen Certification](https///wiki.allseenalliance.org/certification)
### Appendix 1: List of test cases for each service

Below you can find the list of test cases in each test suite for each service under the scope of the AllSeen Alliance certification.  `<del>`Strikeout`</del>` means the test has been removed.

__Note__: The list below will be replaced by the TCCL once it has been approved.


*  About-v1-01;About announcement received

*  About-v1-02;Version property consistent with the About announcement

*  About-v1-03;GetObjectDescription() consistent with the About announcement

*  About-v1-04;Bus objects consistent with the About announcement

*  About-v1-05;Standardized interfaces match definitions

*  About-v1-06;GetAboutData() with default language

*  About-v1-07;GetAboutData() with each supported language

*  About-v1-08;GetAboutData() without a specified language

*  About-v1-09;GetAboutData() for an unsupported language

*  About-v1-10;GetContent() on the About DeviceIcon

*  About-v1-11;GetUrl() on the About DeviceIcon


*  EventsActions-v1-01;Description tag existence in introspection XML and identical XML across different description languages



*  Config-v1-01;System App AppId equals DeviceId

*  Config-v1-02;Call a Config interface method without proper authentication

*  `<del>`Config-v1-03;`</del>`  

*  Config-v1-04;GetConfigurations() method with default language

*  Config-v1-05;GetConfigurations() method with unspecified language

*  Config-v1-06;GetConfigurations() method for each supported language

*  Config-v1-07;GetConfigurations() method with unsupported language

*  Config-v1-08;UpdateConfigurations() method with a new DeviceName

*  `<del>`Config-v1-09`</del>`

*  `<del>`Config-v1-10`</del>`

*  `<del>`Config-v1-11`</del>`

*  Config-v1-12;UpdateConfigurations() method with a DeviceName containing special characters

*  Config-v1-13;UpdateConfigurations() method with an unsupported language

*  Config-v1-14;UpdateConfigurations() method with a DefaultLanguage of another language

*  Config-v1-15;UpdateConfigurations() method for DefaultLanguage with an unsupported language

*  Config-v1-16;UpdateConfigurations() method for DefaultLanguage with an unspecified language

*  `<del>`Config-v1-17`</del>`

*  `<del>`Config-v1-18`</del>`

*  Config-v1-19;UpdateConfigurations() method for an invalid field

*  Config-v1-20;ResetConfigurations() method for DeviceName

*  Config-v1-21;ResetConfigurations() method for DefaultLanguage (at least one supported language)

*  Config-v1-22;ResetConfigurations() method for DefaultLanguage (more than one supported language)

*  `<del>`Config-v1-23`</del>`

*  Config-v1-24;ResetConfigurations() method with an unsupported language

*  Config-v1-25;ResetConfigurations() method for an invalid field

*  Config-v1-26;Restart() method

*  Config-v1-27;Restart() method persists configuration changes

*  `<del>`Config-v1-28`</del>`

*  Config-v1-29;SetPasscode() method with a new value

*  Config-v1-30;SetPasscode() method with a one-character value

*  Config-v1-31;SetPasscode() method with special characters

*  Config-v1-32;Restart() method persists changed passcode

*  Config-v1-33;FactoryReset() method

*  Config-v1-34;FactoryReset() method clears configured data

*  Config-v1-35;FactoryReset() method resets the passcode


*  ControlPanel-v1-01;Verify all ControlPanel bus objects

*  ControlPanel-v1-02;Verify all Container bus objects

*  ControlPanel-v1-03;Verify all Property bus objects

*  ControlPanel-v1-04;Verify all LabelProperty bus objects

*  ControlPanel-v1-05;Verify all Action bus objects

*  ControlPanel-v1-06;Verify all Dialog bus objects

*  ControlPanel-v1-07;Verify all ListProperty bus objects

*  ControlPanel-v1-08;Verify all NotificationAction bus objects

*  ControlPanel-v1-09;Verify all HTTPControl bus objects

*  ControlPanel-v1-10;Verify all secured ControlPanel bus objects


*  Notification-Consumer-v1-01;Basic text message

*  Notification-Consumer-v1-02;Multiple languages

*  `<del>`Notification-Consumer-v1-03`</del>`;

*  Notification-Consumer-v1-04;Invalid language field

*  Notification-Consumer-v1-05;Message priority

*  Notification-Consumer-v1-06;Custom attributes

*  Notification-v1-01;Sending of notifications (Notification Producer)


*  Onboarding-v1-01;Offboard the DUT

*  Onboarding-v1-02;Onboard the DUT

*  Onboarding-v1-03;Session joined on Soft AP

*  `<del>`Onboarding-v1-04;Invalid authType provided to ConfigureWiFi() returns OutOfRange error`</del>`

*  Onboarding-v1-05;Nonexistent personal AP SSID provided to ConfigureWiFi()

*  Onboarding-v1-06;Invalid passphrase for personal AP provided to ConfigureWiFi()

*  Onboarding-v1-07;AuthType value of "any" provided to ConfigureWiFi()

*  Onboarding-v1-08;GetScanInfo() returns results or FeatureNotAvailable error

*  Onboarding-v1-09;Call Onboarding method without proper authentication

*  Onboarding-v1-10;Call Onboarding method after changing the passcode

*  Onboarding-v1-11;Factory reset

*  Onboarding-v1-12;Factory reset resets passcode


*  Audio-v1-01;Validate Stream bus objects

*  Audio-v1-02;Opening a Stream bus object

*  Audio-v1-03;Opening and closing a Stream bus object

*  Audio-v1-04;Closing an unopened Stream bus object

*  Audio-v1-05; Verify any AudioSink capabilities

*  Audio-v1-06; Verify any ImageSink capabilities

*  Audio-v1-07;Verify any Application.MetadataSink capabilities

*  Audio-v1-08;Configure any AudioSink port

*  Audio-v1-09;Configure any AudioSink bus object with an invalid configuration

*  Audio-v1-10;Configure any AudioSink bus object twice.

*  Audio-v1-11;Check for OwnershipLost signal

*  Audio-v1-12;Playback on an AudioSink

*  Audio-v1-13;Pausing a playback on an AudioSink

*  Audio-v1-14;Flushing a paused AudioSink

*  Audio-v1-15;Flushing a playing AudioSink

*  Audio-v1-16;Paused AudioSink remains paused after sending data

*  Audio-v1-17;Playing an empty AudioSink remains IDLE

*  Audio-v1-18;Flushing an idle AudioSink

*  Audio-v1-19;Sending data to an ImageSink

*  Audio-v1-20;Sending data to an Application.MetadataSink

*  Audio-v1-21;Setting the mute state on an AudioSink

*  Audio-v1-22;Setting the volume on an AudioSink

*  Audio-v1-23;Setting an invalid volume on an AudioSink

*  Audio-v1-24;Independence of mute and volume on an AudioSink

*  Audio-v1-25;Synchronize clocks on an AudioSink


*  LSF_Lamp-v1-01;Service Interface Version equals 1

*  LSF_Lamp-v1-02;Lamp Service Version equals 1

*  LSF_Lamp-v1-03;ClearLampFault() method

*  LSF_Lamp-v1-04;SetOnOff() property

*  LSF_Lamp-v1-05;SetHue() property

*  LSF_Lamp-v1-06;SetSaturation()

*  LSF_Lamp-v1-07;SetColorTemp()

*  LSF_Lamp-v1-08;SetBrightness()

*  LSF_Lamp-v1-09;TransitionLampState and verify state and signal

*  LSF_Lamp-v1-10;ApplyPulseEffect

*  LSF_Lamp-v1-11;Service interface XML matches

*  LSF_Lamp-v1-12;Parameters interface version equals 1

*  LSF_Lamp-v1-13;GetEnergyUsageMilliwatts

*  LSF_Lamp-v1-14;GetBrightnessLumens

*  LSF_Lamp-v1-15;Details interface version equals 1

*  LSF_Lamp-v1-16;GetMake

*  LSF_Lamp-v1-17;GetModel

*  LSF_Lamp-v1-18;GetType

*  LSF_Lamp-v1-19;GetLampType

*  LSF_Lamp-v1-20;GetLampBaseType

*  LSF_Lamp-v1-21;GetLampBeamAngle

*  LSF_Lamp-v1-22;GetDimmable

*  LSF_Lamp-v1-23;GetColor

*  LSF_Lamp-v1-24;GetVariableColorTemp

*  LSF_Lamp-v1-25;GetLampID

*  LSF_Lamp-v1-26;GetHasEffects

*  LSF_Lamp-v1-27;GetMinVoltage

*  LSF_Lamp-v1-28;GetMaxVoltage

*  LSF_Lamp-v1-29;GetMaxWattage

*  LSF_Lamp-v1-30;GetIncandescentEquivalent

*  LSF_Lamp-v1-31;GetMaxLumens

*  LSF_Lamp-v1-32;GetMinTemperature

*  LSF_Lamp-v1-33;GetMaxTemperature

*  LSF_Lamp-v1-34;GetColorRenderingIndex


*  LSF_Controller-v1-01;StandardizedInterfacesMatchDefinitions

*  LSF_Controller-v1-02;VersionField

*  LSF_Controller-v1-03;LightingReset

*  LSF_Controller-v1-04;LampInfo

*  LSF_Controller-v1-05;LampName

*  LSF_Controller-v1-06;LampDetails

*  LSF_Controller-v1-07;LampParameters

*  LSF_Controller-v1-08;LampStateFields

*  LSF_Controller-v1-09;LampStateTransition

*  LSF_Controller-v1-10;LampStatePulse

*  LSF_Controller-v1-11;LampStatePresets

*  LSF_Controller-v1-12;LampReset

*  LSF_Controller-v1-13;LampFaults

*  LSF_Controller-v1-14;LampGroupCRUD

*  LSF_Controller-v1-15;LampGroupName

*  LSF_Controller-v1-16;LampGroupStateTransition

*  LSF_Controller-v1-17;LampGroupStatePulse

*  LSF_Controller-v1-18;LampGroupReset

*  LSF_Controller-v1-19;LampGroupStatePresets

*  LSF_Controller-v1-20;DefaultLampState

*  LSF_Controller-v1-21;PresetCRUD

*  LSF_Controller-v1-22;PresetNameChange

*  LSF_Controller-v1-23;SceneCreate

*  LSF_Controller-v1-24;SceneUpdateDelete

*  LSF_Controller-v1-25;SceneApply

*  LSF_Controller-v1-26;SceneNameChanged

*  LSF_Controller-v1-27;MasterSceneCreate

*  LSF_Controller-v1-28;MasterSceneUpdateDelete

*  LSF_Controller-v1-29;MasterSceneApply

*  LSF_Controller-v1-30;MasterSceneNameChanged

*  LSF_Controller-v1-31;LeaderElectionBlobs

*  LSF_Controller-v1-32;LeaderElectionBlobChanged

*  LSF_Controller-v1-33;LeaderElectionOverthrow


*  GWAgent-v1-01;Interfaces Match Definition
### Appendix 2: Hints to troubleshoot adb commands

__What to do when adb command is not recognized:__

If your console does not detect the command make sure you have added “adb.exe” path to Windows’ environment variables. For instance: “C:\Users\rurc\development\adt-bundle-windows-x86_64-20140702\sdk\platform-tools”. 

Below are instructions on how to add an environment variable in Windows:

 1.  From the Desktop, right-click My Computer and click Properties.\\
 2.  Click Advanced System Settings link in the left column.\\
 3.  In the System Properties window click the Environment Variables button.\\
 4.  Add a new environment variable whose name is going to be “Path” and its value the path to the “platform-tools” folder where adb executable is located inside the Android SDK.\\

Otherwise you may execute “adb” using the full path, for example: “C:\Users\rurc\Development\adt-bundle-windows-x86_64-20140702\sdk\platform-tools\adb.exe” followed by its parameters.

__What to do when “adb devices” does not show my connected device:__

The expected output is this:

    List of devices attached
    3096d3ee        device

If you get something that different from the above please make sure your device is correctly detected in Windows’ device manager and that you have adb drivers installed in your Android SDK device manager.

### Appendix 3: List of adb command parameters needed for running the test cases

 | Parameter                                   | Description                                                                                                                                                                                                                   | 
 | ---------                                   | -----------                                                                                                                                                                                                                   | 
 | appId                                       | Globally unique identifier for the application given by its About interface’s AppId metadata field                                                                                                                          | 
 | deviceId                                    | Device identifier set by platform-specific means found in the About interface’s DeviceId metadata field                                                                                                                     | 
 | testSuiteList                               | Comma-separated list of the test suites to run (for example, org.alljoyn.validation.testing.suites.about.AboutTestSuite).                                                                                                     | 
 | testCaseName                                | Comma-separated list of the test cases to run (for example, About-v1-01, About-v1-02, About-v1-03).                                                                                                                           | 
 | enableInteractive                           | Determines if user interaction is required during test case execution. Default value is “false”. This parameter must be set to “true” for NotificationProducerTestSuite and NotificationConsumerTestSuite test cases. | 
 | userInputTimeoutValueInMS                   | Time in milliseconds to wait for a test to complete before considering it failed. This will override the default timeout value.                                                                                               | 
 | org.alljoyn.Onboarding.SoftApSsid           | SSID for the device’s Soft AP (required for OnboardingTestSuite test cases).                                                                                                                                                | 
 | org.alljoyn:Onboarding.SoftapSecurity       | Security type for the device’s Soft AP (required for OnboardingTestSuite test cases).                                                                                                                                       | 
 | org.alljoyn:Onboarding.SoftapPassphrase     | Passphrase for the device’s Soft AP (if the Soft AP has security).                                                                                                                                                          | 
 | org.alljoyn:Onboarding.PersonalApSsid       | SSID for the personal AP (required for OnboardingTestSuite test cases).                                                                                                                                                       | 
 | org.alljoyn:Onboarding.PersonalApSecurity   | Security type for the personal AP (required for OnboardingTestSuite test cases). Must be WPA or WP2.                                                                                                                          | 
 | org.alljoyn:Onboarding.PersonalApPassphrase | Passphrase for the personal AP (required for OnboardingTestSuite test cases).                                                                                                                                                 | 
### Appendix 4: List of valid values for the “testCaseName” parameter

 | testCaseName                | 
 | ------------                | 
 | About-v1-01                 | 
 | About-v1-02                 | 
 | About-v1-03                 | 
 | About-v1-04                 | 
 | About-v1-05                 | 
 | About-v1-06                 | 
 | About-v1-07                 | 
 | About-v1-08                 | 
 | About-v1-09                 | 
 | About-v1-10                 | 
 | About-v1-11                 | 
 | .                           | 
 | EventsActions-v1-01         | 
 | .                           | 
 | Config-v1-01                | 
 | Config-v1-02                | 
 | Config-v1-04                | 
 | Config-v1-05                | 
 | Config-v1-06                | 
 | Config-v1-07                | 
 | Config-v1-08                | 
 | Config-v1-12                | 
 | Config-v1-13                | 
 | Config-v1-14                | 
 | Config-v1-15                | 
 | Config-v1-16                | 
 | Config-v1-19                | 
 | Config-v1-20                | 
 | Config-v1-21                | 
 | Config-v1-22                | 
 | Config-v1-24                | 
 | Config-v1-25                | 
 | Config-v1-26                | 
 | Config-v1-27                | 
 | Config-v1-29                | 
 | Config-v1-30                | 
 | Config-v1-31                | 
 | Config-v1-32                | 
 | Config-v1-33                | 
 | Config-v1-34                | 
 | Config-v1-35                | 
 | .                           | 
 | ControlPanel-v1-01          | 
 | ControlPanel-v1-02          | 
 | ControlPanel-v1-03          | 
 | ControlPanel-v1-04          | 
 | ControlPanel-v1-05          | 
 | ControlPanel-v1-06          | 
 | ControlPanel-v1-07          | 
 | ControlPanel-v1-08          | 
 | ControlPanel-v1-09          | 
 | ControlPanel-v1-10          | 
 | .                           | 
 | Notification-Consumer-v1-01 | 
 | Notification-Consumer-v1-02 | 
 | Notification-Consumer-v1-04 | 
 | Notification-Consumer-v1-05 | 
 | Notification-Consumer-v1-06 | 
 | Notification-v1-01          | 
 | .                           | 
 | Onboarding-v1-01            | 
 | Onboarding-v1-02            | 
 | Onboarding-v1-03            | 
 | Onboarding-v1-05            | 
 | Onboarding-v1-06            | 
 | Onboarding-v1-07            | 
 | Onboarding-v1-08            | 
 | Onboarding-v1-09            | 
 | Onboarding-v1-10            | 
 | Onboarding-v1-11            | 
 | Onboarding-v1-12            | 
 | .                           | 
 | Audio-v1-01                 | 
 | Audio-v1-02                 | 
 | Audio-v1-03                 | 
 | Audio-v1-04                 | 
 | Audio-v1-05                 | 
 | Audio-v1-06                 | 
 | Audio-v1-07                 | 
 | Audio-v1-08                 | 
 | Audio-v1-09                 | 
 | Audio-v1-10                 | 
 | Audio-v1-11                 | 
 | Audio-v1-12                 | 
 | Audio-v1-13                 | 
 | Audio-v1-14                 | 
 | Audio-v1-15                 | 
 | Audio-v1-16                 | 
 | Audio-v1-17                 | 
 | Audio-v1-18                 | 
 | Audio-v1-19                 | 
 | Audio-v1-20                 | 
 | Audio-v1-21                 | 
 | Audio-v1-22                 | 
 | Audio-v1-23                 | 
 | Audio-v1-24                 | 
 | Audio-v1-25                 | 
 | .                           | 
 | LSF_Lamp-v1-01              | 
 | LSF_Lamp-v1-02              | 
 | LSF_Lamp-v1-03              | 
 | LSF_Lamp-v1-04              | 
 | LSF_Lamp-v1-05              | 
 | LSF_Lamp-v1-06              | 
 | LSF_Lamp-v1-07              | 
 | LSF_Lamp-v1-08              | 
 | LSF_Lamp-v1-09              | 
 | LSF_Lamp-v1-10              | 
 | LSF_Lamp-v1-11              | 
 | LSF_Lamp-v1-12              | 
 | LSF_Lamp-v1-13              | 
 | LSF_Lamp-v1-14              | 
 | LSF_Lamp-v1-15              | 
 | LSF_Lamp-v1-16              | 
 | LSF_Lamp-v1-17              | 
 | LSF_Lamp-v1-18              | 
 | LSF_Lamp-v1-19              | 
 | LSF_Lamp-v1-20              | 
 | LSF_Lamp-v1-21              | 
 | LSF_Lamp-v1-22              | 
 | LSF_Lamp-v1-23              | 
 | LSF_Lamp-v1-24              | 
 | LSF_Lamp-v1-25              | 
 | LSF_Lamp-v1-26              | 
 | LSF_Lamp-v1-27              | 
 | LSF_Lamp-v1-28              | 
 | LSF_Lamp-v1-29              | 
 | LSF_Lamp-v1-30              | 
 | LSF_Lamp-v1-31              | 
 | LSF_Lamp-v1-32              | 
 | LSF_Lamp-v1-33              | 
 | LSF_Lamp-v1-34              | 
 | .                           | 
 | LSF_Controller-v1-01        | 
 | LSF_Controller-v1-02        | 
 | LSF_Controller-v1-03        | 
 | LSF_Controller-v1-04        | 
 | LSF_Controller-v1-05        | 
 | LSF_Controller-v1-06        | 
 | LSF_Controller-v1-07        | 
 | LSF_Controller-v1-08        | 
 | LSF_Controller-v1-09        | 
 | LSF_Controller-v1-10        | 
 | LSF_Controller-v1-11        | 
 | LSF_Controller-v1-12        | 
 | LSF_Controller-v1-13        | 
 | LSF_Controller-v1-14        | 
 | LSF_Controller-v1-15        | 
 | LSF_Controller-v1-16        | 
 | LSF_Controller-v1-17        | 
 | LSF_Controller-v1-18        | 
 | LSF_Controller-v1-19        | 
 | LSF_Controller-v1-20        | 
 | LSF_Controller-v1-21        | 
 | LSF_Controller-v1-22        | 
 | LSF_Controller-v1-23        | 
 | LSF_Controller-v1-24        | 
 | LSF_Controller-v1-25        | 
 | LSF_Controller-v1-26        | 
 | LSF_Controller-v1-27        | 
 | LSF_Controller-v1-28        | 
 | LSF_Controller-v1-29        | 
 | LSF_Controller-v1-30        | 
 | LSF_Controller-v1-31        | 
 | LSF_Controller-v1-32        | 
 | LSF_Controller-v1-33        | 
 | .                           | 
 | GWAgent-v1-01               | 





 
###  Appendix 5: Logcat output example 

Below you can find an extract of the logcat output for example 5.

''08-20 09:57:51.510: E/SELinux(2021): selinux_android_seapp_context_reload: seapp_contexts file is loaded from /data/security/spota/seapp_contexts
08-20 09:57:51.631: E/ValidationInstrumentationTestRunnerHelper(2021): testCaseKeyWords: null
08-20 09:57:51.661: W/dalvikvm(2021): method Landroid/test/InstrumentationTestRunner$StringResultPrinter;.print incorrectly overrides package-private method with same name in Ljunit/textui/ResultPrinter;
08-20 09:57:51.661: I/TestRunner(2021): started: testAbout_v1_01_AboutAnnouncement(org.alljoyn.validation.testing.instrument.InstrumentationTestCaseWrapper)
08-20 09:57:51.711: E/PERMISSION_MGR(2021):    1.081 ****** ERROR PERMISSION_MGR lepDisp    ...ndroid/PermissionDB.cc:202 |  0x0001
08-20 09:57:51.721: E/NETWORK(2021):    1.090 ****** ERROR NETWORK lepDisp           common/os/posix/Socket.cc:283 |  0x0004
08-20 09:57:51.741: I/ioeAboutServiceImpl(2021): BusAttachment.registerBusObject(AnnouncmentReceiver) status = 'OK', ObjPath: '/About'
08-20 09:57:51.751: I/ioeAboutServiceImpl(2021): BusAttachment.registerSignalHandlers(AnnouncmentReceiver) status = 'OK'
08-20 09:57:51.751: I/ioeAboutServiceImpl(2021): BusAttachment.addMatch() status = OK
08-20 09:57:51.751: I/DeviceAnnounceHandler(2021): Waiting for About announcement signal from device: 4564545455454; appId: 6475a67c-4d00-481e-9e56-7fba5c514778
08-20 09:58:15.896: I/ServiceHelper(2021): Session established to peer: :j8WNeR7W.2
08-20 09:58:16.187: E/ALLJOYN_JAVA(2021):   25.565 ****** ERROR ALLJOYN_JAVA external     ...a/jni/alljoyn_java.cc:6042 |  0x909b
08-20 09:58:16.187: I/ServiceHelper(2021): Ignoring ALLJOYN_JOINSESSION_REPLY_ALREADY_JOINED error code
08-20 09:58:16.207: E/ALLJOYN_JAVA(2021):   25.587 ****** ERROR ALLJOYN_JAVA external     ...a/jni/alljoyn_java.cc:6170 |  0x908a
08-20 09:58:16.337: I/TestRunner(2021): finished: testAbout_v1_01_AboutAnnouncement(org.alljoyn.validation.testing.instrument.InstrumentationTestCaseWrapper)
08-20 09:58:16.337: I/TestRunner(2021): passed: testAbout_v1_01_AboutAnnouncement(org.alljoyn.validation.testing.instrument.InstrumentationTestCaseWrapper)''

###  Appendix 6: Terminology 

Some terms used are listed below
 | Term                        | Description                                                                                                                                                                                                                                                                               | 
 | ----                        | -----------                                                                                                                                                                                                                                                                               | 
 | adb commands                | A command line tool that, among others, allows you to communicate with a connected Android device                                                                                                                                                                                         | 
 | AllJoyn™ framework        | An open source IoT software framework and set of services that enables horizontal interoperability across product platforms and allows for proximal peer-to-peer discovery & communications over various transports and OSes                                                              | 
 | appId                       | Globally unique identifier  for the application given by its About interface’s AppId metadata field                                                                                                                                                                                     | 
 | DDMS                        | A debugging tool called the Dalvik Debug Monitor Server, which provides port-forwarding services, screen capture on the device, thread and heap information on the device, logcat, process, and radio state information, incoming call and SMS spoofing, location data spoofing, and more | 
 | deviceId                    | Device identifier set by platform-specific means found in the About interface’s DeviceId metadata field                                                                                                                                                                                 | 
 | DUT                         | Device Under Test. A real sample of the product device which is going to be subject to the testing                                                                                                                                                                                        | 
 | Self-Certification Tool     | An Android device hosting the Self-Certification Tool APK, used as the actual Self-Certification Tool. The Self-Certification Tool only supports Wi-Fi transport                                                                                                                          | 
 | Self-Certification Tool APK | An APK with the Self-Certification Tool software provided by the AllSeen Alliance that has to be installed on an Android device. The Android device together with the Self Certification Tool APK become the Self-Certification Tool                                                      | 
 | PC or laptop                | Any computer used as controller of the Self-Certification Tool. The control of the Self-Certification Tool takes place via adb commands                                                                                                                                                   | 
 | PID                         | Process Identifier. Is a number used to temporarily uniquely identify a process                                                                                                                                                                                                           | 
 | TCCL                        | Test Case Control List. A list of test cases that are required by the AllSeen Alliance to certify a product                                                                                                                                                                               | 
 | Wireless Access Point       | A device that allows wireless devices to connect to a wired network using Wi-Fi                                                                                                                                                                                                           | 

###  Appendix 6: Self-Certification Program User Guide 

{{:certification:self_certification_tool_users_guide_14.12.pdf|AllSeen Alliance Self-Certification Program User Guide}}




###  Appendix 7: Self-Certification Program Developer Guide 

{{:certification:cc-allseen_d06_d6.1_20self_20certification_20program_20developers_20guide_2014.06_20update_202-2.pdf|AllSeen Alliance Self-Certification Program Developer Guide}}
### Appendix 8: Self-Certification Logcat Viewer

{{:certification:allseen_viewer_1.1.1.zip|AllSeen Alliance Self-Certification Logcat Viewer}}

