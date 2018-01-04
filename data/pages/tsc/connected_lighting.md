# Connected Lighting Project

The Connected Lighting Project develops the Lighting Service Framework (LSF) providing an open and common way of communicating with AllJoyn-based connected lighting products, regardless of manufacturer. This will enable lighting manufacturers to make their products interoperable with each other as well as other connected things, and provide 3rd party application developers with a common interface (API) to communicate with lights across manufacturers.

Examples of features of LSF include the ability to group lamps together and control their hue, saturation, brightness, and color temperature to match a users preference or mood. Other features include the ability to personalize the lighting experience to an individuals tastes and preferences by setting lighting Scenes, and the ability for users to add lighting Effects like pulsing lights for notifications purposes. 

To participate in the working group, please ([Subscribe](https///lists.allseenalliance.org/mailman/listinfo/allseen-lighting)) to the the Mailing List: `<allseen-lighting@lists.allseenalliance.org>` 


*  AllSeen Summit Presentation - November 2014 - {{:tsc:lighting:connectedlighting_allseen_summit_nov_2014_v04.pdf| Download the Presentation}}

*  For an Overview Presentation on LSF from Uplinq 2014, please [ Watch via YouTube](http://youtu.be/3lNzNj5ytqM?list=PLxeazpXYyqtNm2EnCbfSzy7aKOkHjiaSi ) and [ View the Presentation](http://www.slideshare.net/QualcommDeveloperNetwork/80-connected-lighting-vogelsangfok919gg45 )

*  Connected Lighting Working Group [ Announcement](https///allseenalliance.org/announcement/allseen-alliance-launches-initiative-advance-smart-lighting-0 )

*  Blog post by Marc Alexander, CTO LIFX, Working Group Chair [ Read](https///allseenalliance.org/news/blogs/2014/10/shining-light-internet-everything )

### What's New (Last Update: July 29th)

*  October 23th 2015 - Lighting 15.04 Released. [ Release Note](https///wiki.allseenalliance.org/lighting/lighting_15.04_release_review )

*  July 29th 2015 - Lighting 15.04 Feature-Complete milestone has reached and code is available

*  June 9th 2015 - Getting Started with Android Sample and Lighting SDK [ Getting Started](https///wiki.allseenalliance.org/lighting/Building_Android_Sample_with_Lighting_SDK )

*  April 10th 2015 - Lighting 14.12 Released.  [ Release Note](https///wiki.allseenalliance.org/lighting/lighting_14.12_release_review )

*  March 18th 2015 - Added Getting Started Guide for Lighting SDK for iOS

*  February 2nd 2015 - Added Lighting Controller Test Case Specification

*  December 18th - Beta Lighting SDK for iOS 14.06 Released. [ More Here](https///wiki.allseenalliance.org/tsc/connected_lighting?&#lighting_sdk_beta )

*  November 14th - Lighting Service Framework 14.06 Released. [ Read More](https///allseenalliance.org/news/blogs/2014/11/open-interoperable-approach-lighting )

*  November 11th - Added AllSeen Summit Nov 2014 Presentation - {{:tsc:lighting:connectedlighting_allseen_summit_nov_2014_v04.pdf| Download}}

*  November 8th - Updates to the LSF [Sample apps](https///wiki.allseenalliance.org/tsc/connected_lighting#sample_applications) and [ Beta Lighting SDK for Android](https///wiki.allseenalliance.org/tsc/connected_lighting#lighting_sdk ).

*  November 8th - Update to Luminaire in [ Google Play](https///play.google.com/store/apps/details?id=com.qualcomm.luminaire )
# LSF Architecture

The LSF is a multi-tier architecture with components that reside inside and outside the Lamp (light bulb), and will run over any IP bearer capable of running AllJoyn. Components include:
 1.  Lamp Service
 2.  Lighting Controller Service
 3.  Sample Applications for Android and iOS
 4.  Lighting SDK beta for Android (and iOS, see [Roadmap)](https///wiki.allseenalliance.org/tsc/connected_lighting?&#roadmap)

### 1. Lamp Service

The Lamp Service is implemented by the Lamp (light bulb) Manufacturer inside the connected Lamp firmware to make the Lamp LSF compatible.  The Lamp Service is designed to run in a very small footprint (1KB SRAM/5KB Flash) on an embedded RTOS in the Lamps Microcontroller (MCU), and works in conjunction and is dependent on the AllJoyn Thin Client [ ajtcl](https///git.allseenalliance.org/cgit/core/ajtcl.git ) and [ base_tcl](https///git.allseenalliance.org/cgit/services/base_tcl.git/ ).  If you are building lamp hardware and want to make it compatible with the Lighting Service Framework and certified "Designed for AllSeen", you will need to implement the Lamp Service in your Lamp and pass the Lamp Service tests included in the certification tool.


*  15.04
    * Lamp Service 15.04 Getting Started Guide:{{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_15.04_lamp_service.docx|Doc}} | {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_15.04_lamp_service.pdf|pdf}}
    * Lamp Service 15.04 [ Source](https///git.allseenalliance.org/cgit/lighting/service_framework.git/tree/thin_core_library/lamp_service?id=v15.04 ) written in C
    * Lamp Service 15.04 Build Instructions for Linux [ Configure](https///build.allseenalliance.org/lighting/view/RB15_04/job/Lighting_Service_Framework_LSF_RB15.04/configure )
    * Note: [ C&C WG](https///certify.alljoyn.org/ ) is handling the release of Interface doc.

*  14.12
    * Lamp Service 14.12 Getting Started Guide:{{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_14.12_lamp_service.docx|Doc}} | {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_14.12_lamp_service.pdf|pdf}}
    * Lamp Service 14.12 Interface Definition (For Certification): {{:compliance:LSF_Lamp_Service_14.12_Interface_Specification.docx|Doc}} | {{:compliance:LSF_Lamp_Service_14.12_Interface_Specification.pdf|pdf}}
    * Lamp Service 14.12 Test Case Specification (For Certification): {{:compliance:LSF_Lamp_Service_14.12_Test_Case_Specifications.docx|Doc}} | {{:compliance:LSF_Lamp_Service_14.12_Test_Case_Specifications.pdf|pdf}}
    * Lamp Service 14.12 [ Source](https///git.allseenalliance.org/cgit/lighting/service_framework.git/tree/thin_core_library/lamp_service?id=v14.12 ) written in C
    * Lamp Service 14.12 Build Instructions for Linux [ Configure](https///build.allseenalliance.org/lighting/view/v14_12/job/Lighting_Service_Framework_LSF_v14_12/configure )

*  14.06
    * Lamp Service 14.06 Getting Started Guide: {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_14.06_lamp_service.docx|Doc}} | {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_14.06_lamp_service.pdf|pdf}}
    * Lamp Service 14.06 Interface Definition (For Certification): {{:compliance:alljoyn_lamp_service_14.06_interface_definition.docx|Doc}}
    * Lamp Service 14.06 Test Case Specification (For Certification): {{:compliance:alljoyn_lamp_service_14.06_test_case_specifications.docx|Doc}} | {{:compliance:alljoyn_lamp_service_14.06_test_case_specifications.pdf|pdf}}
    * Lamp Service 14.06 [ Source](https///git.allseenalliance.org/cgit/lighting/service_framework.git/tree/thin_core_library/lamp_service?id=v14.06 ) written in C
    * Lamp Service 14.06 Build Instructions for Linux [ Configure](https///build.allseenalliance.org/lighting/job/Lighting_Service_Framework_LSF_v14_06/configure )

*  Designed for AllSeen [ Certification Process](https///allseenalliance.org/certification ) and [ FAQ](https///allseenalliance.org/certification/faq )

Who should implement the Lamp Service?
 1.   Lamp Manufacturers building IP connected Lamps
### 2. Lighting Controller Service

The Lighting Controller Service is a mandatory component of the LSF and works in conjunction with and is dependent on the [ AllJoyn Core Standard Client and Router](https///git.allseenalliance.org/cgit/core/alljoyn.git/tree/alljoyn_core ). It stores group, scene, and preset information and discovers and connects with devices on the same network running Lamp Service.  If multiple Lighting Controller Services are running on the same network, they arbitrate and one becomes a Leader and the rest become Followers. Group, Scene, and Preset information is synchronized between Leaders and Followers, and if a Leader leaves the network a Follower will be promoted and take over controlling the Lamps. Lighting Controller Service runs outside of the Lamp on a Hub, Router, Switch, Gateway, or any other Linux-based device (such as [ OpenWrt)](https///openwrt.org/ ) on the same network as the Lamps. It can also be bundled in with the mobile application running on an Android or iOS Smartphone or Tablet that the end user uses to discover and control the Lamps. The Lighting Controller Service footprint is roughly 270KB Flash / 25KB RAM not including the AllJoyn Core.


*  15.04
    * Lighting Controller Service 15.04 Getting Started Guide: {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_15.04_lighting_controller_service.docx|Doc}} | {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_15.04_lighting_controller_service.pdf|pdf}}
    * Lighting Controller Service 15.04 [ Source](https///git.allseenalliance.org/cgit/lighting/service_framework.git/tree/standard_core_library?id=v15.04 ) written in C
    * Lighting Controller Service 15.04 Build Instructions for Linux [ Configure](https///build.allseenalliance.org/lighting/view/RB15_04/job/Lighting_Service_Framework_LSF_RB15.04/configure )
    * Note: [ C&C WG](https///certify.alljoyn.org/ ) is handling the release of Interface doc.

*  14.12
    * Lighting Controller Service 14.12 Getting Started Guide: {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_14.12_lighting_controller_service.docx|Doc}} | {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_14.12_lighting_controller_service.pdf|pdf}}
    * Lighting Controller Service 14.12 [ Source](https///git.allseenalliance.org/cgit/lighting/service_framework.git/tree/standard_core_library?id=v14.12 ) written in C
    * Lighting Controller Service 14.12 Build Instructions for Linux [ Configure](https///build.allseenalliance.org/lighting/view/v14_12/job/Lighting_Service_Framework_LSF_v14_12/configure )
    * Lighting Controller Service 14.12 Interface Definition (For Certification): {{:compliance:controller_service_14.12_interface_definition.docx|Doc}} | {{:compliance:controller_service_14.12_interface_definition.pdf|pdf}}
    * Lighting Controller Service 14.12 Test Case Specifications (For Certification) {{:compliance:Controller_Service_14.12_Test_Case_Specification.docx|Doc}} | {{:compliance:Controller_Service_14.12_Test_Case_Specification.pdf|pdf}}

*  14.06
    * Lighting Controller Service 14.06 Getting Started Guide: {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_14.06_lighting_controller_service.docx|Doc}} | {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_14.06_lighting_controller_service.pdf|pdf}}
    * Lighting Controller Service 14.06 [ Source](https///git.allseenalliance.org/cgit/lighting/service_framework.git/tree/standard_core_library?id=v14.06 ) written in C
    * Lighting Controller Service 14.06 Build Instructions for Linux [ Configure](https///build.allseenalliance.org/lighting/job/Lighting_Service_Framework_LSF_v14_06/configure )
    * Lighting Controller Service 14.06 Interface Definition (For Certification): {{:tsc:compliance:Controller_Service_14.06_Interface_Definition.docx|Doc}}
    * Lighting Controller Service 14.06 Test Case Specifications (For Certification) - [ pdf](https///wiki.allseenalliance.org/_media/compliance/lighting_controller_service_14_2006_test_case_specification_20_282_29.pdf ) 

*  Designed for AllSeen [ Certification Process](https///allseenalliance.org/certification ) and [ FAQ](https///allseenalliance.org/certification/faq )

__Lighting Controller Support for AllJoyn Events & Actions__

A significant and powerful feature of the Lighting Controller Service is that it exposes every Scene as an [ AllJoyn Event & Action](https///allseenalliance.org/docs-and-downloads/documentation/guide-using-alljoyn-events-and-actions-feature ). Events and Actions are loosely coupled integrations that enable just in time interoperability.  

*  **Actions** allow Scenes in the Lighting Controller to be discovered, introspected, and invoked dynamically by other devices and applications. This makes it very easy for other devices to trigger a Scene. The Lighting Controller automatically exposes every Scene as an action with a text descriptor that includes the Scene name.  Create a new Scene and that Scene is instantly discoverable and invokable as an AllJoyn Action.   

*  **Events** allow Scenes in the Lighting Controller to notify other devices and applications when a Scene is applied, allowing other devices to react when they receive the Scene's Event. The Lighting Controller automatically triggers an Event whenever a Scene is invoked.  The Event is discoverable with a text descriptor that includes the Scene name.  Create a new Scene and that Scene is instantly discoverable and will emit an Event when the Scene is applied.

Actions are an extremely powerful way of integrating IoT products using AllJoyn. For example, a Hub, Gateway, or Router running the Lighting Controller can host a rules engine to discover all devices on the network emitting Events (Including the Lighting Controller itself) and allow the consumer to create rules that bind those events to Lighting Scenes exposed as Actions.  This can (for example), allow the door lock to launch a "Welcome Home" scene when the door is unlocked or allow the wearable baby monitor to pulse the lights when the baby is waking up. All of this can be accomplished proximally on the local network without the need to go to the cloud. 


*  Events & Actions Description: [ Read](https///allseenalliance.org/developers/learn/core/events-and-actions )

*  Events & Actions API Guide: [ Read](https///allseenalliance.org/developers/develop/api-guide/events-and-actions )

*  Events & Actions Overview: {{:release:allseenalliance_events_actions_sept2014.pptx|PPT}}

*  Events & Actions Presentation Overview: [ Watch on YouTube](https///www.youtube.com/watch?v=4xpasmpBf0Q&list=PL4IDeLjCA5CP7whTaPrEKBdXzj9Fa1-Fm#t=2303 )

*  Events & Actions Interface Definition (For Certification): {{:compliance:alljoyn_events_actions_feature_interface_definition.docx | Doc}} |{{:compliance:alljoyn_events_actions_feature_interface_definition.pdf | pdf}}

*  Events & Actions Test Case Specifications (For Certification): {{:compliance:alljoyn_events_actions_14.06_test_case_specificatons.docx | Doc}}

*  Events & Actions Browser Android Application: [ Source](https///git.allseenalliance.org/cgit/core/alljoyn.git/tree/alljoyn_core/samples/eventaction/Android?h=refs/heads/RB14.06 )

*  Notifier Application in Google Play generates Events: [ Download](https///play.google.com/store/apps/details?id=com.qualcomm.qce.notifier&hl=en )

Who should implement the Lighting Controller Service?
 1.  Lamp Manufacturers bundling the Lighting Controller in their Hub or Gateway
 2.  Lamp Manufacturers bundling the Lighting Controller in their iOS or Android Application
 3.  CE Manufacturers who develop routers, gateways, hubs, or other Connected Devices running Linux who want their products to interoperate with AllJoyn-based lamps out of the box. For example, a CE OEM who builds a Home Automation Controller may elect to implement the Lighting Controller within their hub to make it interoperable with Lamps in the AllJoyn lighting Ecosystem.
 4.  Connected Device Manufacturers who developer appliances, white or brown goods, or other Connected Devices running Linux who want their products to interoperate with AllJoyn-based lighting out of the box.
 5.  Application Developers who want their applications to be able to discover and control AllJoyn-based Lamps. 
### 3. Sample Applications

The Sample Applications are turnkey applications for iOS and Android that can be used by a Lamp Manufacturer to jumpstart the development of their own branded AllJoyn LSF-compatible mobile applications. The Sample Applications provide a full implementation including Lamp discovery, controlling lamp preferences (Hue, Saturation, Color Temperature, Brightness), Creating and managing Presets, Groups, and Scenes, and adding Effects. 


*  15.04
    * Sample Application for Android 15.04: [ Source](https///git.allseenalliance.org/cgit/lighting/apps.git/tree/?id=v15.04 ) | [ APK Download](https///build.allseenalliance.org/lighting/view/v15_04/job/Lighting_Sample_App_Android_v15_04/LABEL=rac-ord-asa-ci-android-1,MODE=alliance,VARIANT=release/7/artifact/release/LSFSampleApp_Android_01_01_0459.apk )
    * Sample Application for Android 15.04 Build Instructions [ Configure](https///build.allseenalliance.org/lighting/view/RB15_04/job/Lighting_Sample_App_Android_RB15.04/configure )
    * Sample Application for iOS 15.04:[ Binary](https///build.allseenalliance.org/lighting/view/RB15_04/job/Lighting_Sample_App_iOS_RB15.04/1/artifact/release/LSFSampleApp_iOS_01_01_0512.ipa ) Note: iOS Binary IPA is not signed, needs to be built from source. Contact mailing list with questions: [ Here](allseen-lighting@lists.allseenalliance.org )
    * Sample Application for iOS 15.04 Build Instructions:[ Configure](https///build.allseenalliance.org/lighting/view/RB15_04/job/Lighting_Sample_App_iOS_RB15.04/configure )
    *  Lighting Controller Service 15.04 Client [ Source](https///git.allseenalliance.org/cgit/lighting/service_framework.git/tree/standard_core_library/lighting_controller_client/?id=v15.04 ) written in `<nowiki>`C++`</nowiki>` for low level interfacing with the Lighting Controller Service.
    * Note: [ C&C WG](https///certify.alljoyn.org/ ) is handling the release of Interface doc.

*  14.12
    * Sample Application for Android 14.12: [ Source](https///git.allseenalliance.org/cgit/lighting/apps.git/tree/?id=v14.12 ) | [ APK Download](https///build.allseenalliance.org/lighting/view/v14_12/job/Lighting_Sample_App_Android_v14_12/12/artifact/release/LSFSampleApp_Android_14_12_debug.apk )
    * Sample Application for Android 14.12 Build Instructions [ Configure](https///build.allseenalliance.org/lighting/view/v14_12/job/Lighting_Sample_App_Android_v14_12/configure )
    * Sample Application for iOS 14.12:[ Binary](https///build.allseenalliance.org/lighting/view/v14_12/job/Lighting_Sample_App_iOS_v14_12/10/artifact/release/LSFSampleApp.ipa ) Note: iOS Binary IPA is not signed, needs to be built from source. Contact mailing list with questions: [ Here](allseen-lighting@lists.allseenalliance.org )
    * Sample Application for iOS 14.12 Build Instructions:[ Configure](https///build.allseenalliance.org/lighting/view/v14_12/job/Lighting_Sample_App_iOS_v14_12/configure )
    *  Lighting Controller Service 14.12 Client [ Source](https///git.allseenalliance.org/cgit/lighting/service_framework.git/tree/standard_core_library/lighting_controller_client?id=v14.12 ) written in `<nowiki>`C++`</nowiki>` for low level interfacing with the Lighting Controller Service.

*  14.06
    * Sample Application for Android 14.06: [ Source](https///git.allseenalliance.org/cgit/lighting/apps.git/tree/?id=v14.06 ) | [ APK Download](https///build.allseenalliance.org/lighting/view/v14_06/job/Lighting_Sample_App_Android_v14_06/lastSuccessfulBuild/artifact/release/LSFSampleApp_Android_01_00_0794_debug.apk )
    * Sample Application for Android 14.06 Build Instructions [ Configure](https///build.allseenalliance.org/lighting/job/Lighting_Sample_App_Android_v14_06/configure )
    * Sample Application for iOS 14.06:[ Binary](https///build.allseenalliance.org/lighting/job/Lighting_Sample_App_iOS_v14_06/1/artifact/release/LSFSampleApp.ipa ) Note: iOS Binary IPA is not signed, needs to be built from source. Contact mailing list with questions: [ Here](allseen-lighting@lists.allseenalliance.org )
    * Sample Application for iOS 14.06 Build Instructions:[ Configure](https///build.allseenalliance.org/lighting/job/Lighting_Sample_App_iOS_v14_06/configure )
    * Lighting Controller Service 14.06 Client [ Source](https///git.allseenalliance.org/cgit/lighting/service_framework.git/tree/standard_core_library/lighting_controller_client?id=v14.06 ) written in `<nowiki>`C++`</nowiki>` for low level interfacing with the Lighting Controller Service.

Who should use the Sample Applications?
 1.  Lamp Manufacturers who want to developer their own custom branded applications for lighting control
 2.  Application Developers who want low-level API's for interfacing with the Lighting Controller Service such as creating Scenes, Groups, and Presets.  Application Developers should start with the Lighting SDK, which includes many of the standard functions for interfacing with Lamps using higher level API's that can speed development.
    
    
### 4. Lighting SDK (beta)

The Lighting SDK provides Application Developers with a high level toolset for discovering and manipulating LSF-compatible lamps, allowing them to discover individual or groups of lamps, manipulate their Hue, Saturation, Color Temperature, and Brightness and discover and apply Scenes. Starting in v15.04, the Lighting SDK provides a complete set of APIs such as manipulating groups, scenes, and presets.  v15.04 Sample Applications (for both Android and iOS) are completely written using v15.04 Lighting SDK.  These SDKs are also available in [Alliance Download](https///allseenalliance.org/developers/download)


*  15.04
      * Android
        * Lighting SDK 15.04 for Android Getting Started Guide: {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_15.04_lighting_sdk_android.docx|Doc}} | {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_15.04_lighting_sdk_android.pdf|pdf}}
        * Lighting SDK 15.04 for Android: [ Download (zip)](https///build.allseenalliance.org/lighting/view/v15_04/job/Lighting_SDK_Android_v15_04/LABEL=rac-ord-asa-ci-android-1,MODE=alliance,VARIANT=release/8/artifact/release/Lighting_SDK_beta_Android_01_01_0457.zip)
        * Lighting SDK 15.04 for Android Build Instructions: [Configure](https///build.allseenalliance.org/lighting/view/RB15_04/job/Lighting_SDK_Android_RB15.04/configure )
        * Lighting SDK 15.04 Tutorials [ View](https///git.allseenalliance.org/cgit/lighting/apps.git/tree/tutorial-app/android/?id=v15.04 )
      * iOS
        * Lighting SDK 15.04 for iOS Getting Started Guide: {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_15.04_lighting_sdk_ios.docx|Doc}} | {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_15.04_lighting_sdk_ios.pdf|pdf}}
        * Lighting SDK 15.04 for iOS (Beta): [ Download (zip)](https///build.allseenalliance.org/lighting/view/RB15_04/job/Lighting_SDK_iOS_RB15.04/1/artifact/release/Lighting_SDK_beta_iOS_01_01_0554.zip)
        * Lighting SDK 15.04 for iOS (Beta) Build Instructions: [Configure](https///build.allseenalliance.org/lighting/view/RB15_04/job/Lighting_SDK_iOS_RB15.04/configure ) 
        * Lighting SDK 15.04 iOS Tutorials [ View](https///git.allseenalliance.org/cgit/lighting/apps.git/tree/tutorial-app/iOS/?id=v15.04 )

*  14.12
      * Android
        * Lighting SDK 14.12 for Android Getting Started Guide: {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_14.12_lighting_sdk_android.docx|Doc}} | {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_14.12_lighting_sdk_android.pdf|pdf}}
        * Lighting SDK 14.12 for Android (Beta): [ Download](https///build.allseenalliance.org/lighting/view/v14_12/job/Lighting_SDK_Android_v14_12/15/artifact/release/Lighting_SDK_Android_14_12_beta.zip)
        * Lighting SDK 14.12 for Android (Beta) Build Instructions: [Configure](https///build.allseenalliance.org/lighting/view/v14_12/job/Lighting_SDK_Android_v14_12/configure )
        * Lighting SDK 14.12 Java Tutorial Project [ View](https///git.allseenalliance.org/cgit/lighting/apps.git/tree/tutorial-app/android/LSFTutorial/src/org/allseen/lsf/tutorial/TutorialActivity.java?id=v14.12 )
        * Lighting SDK 14.12 Beta for Android [ Source](https///git.allseenalliance.org/cgit/lighting/apps.git/tree/tutorial-app/android/LSFTutorial?id=v14.12 )
      * iOS
        * Lighting SDK 14.12 for iOS Getting Started Guide: {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_14.12_lighting_sdk_ios.docx|Doc}} | {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_14.12_lighting_sdk_ios.pdf|pdf}}
        * Lighting SDK 14.12 for iOS (Beta): [ Download](https///build.allseenalliance.org/lighting/view/v14_12/job/Lighting_SDK_iOS_v14_12/5/artifact/release/Lighting_SDK_iOS_14_12_beta.zip)
        * Lighting SDK 14.12 for iOS (Beta) Build Instructions: [Configure](https///build.allseenalliance.org/lighting/view/v14_12/job/Lighting_SDK_iOS_v14_12/configure ) 
        * Lighting SDK 14.12 iOS Tutorial Project [ View](https///git.allseenalliance.org/cgit/lighting/apps.git/tree/tutorial-app/iOS/LSFTutorial/LSFTutorial/LSFTutorialViewController.m?id=v14.12 )
        * Lighting SDK 14.12 Beta for iOS [ Source](https///git.allseenalliance.org/cgit/lighting/apps.git/tree/tutorial-app/iOS/LSFTutorial?id=v14.12 )

*  14.06
    * Android
        * Lighting SDK 14.06 for Android Getting Started Guide: {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_14.06_lighting_sdk_android.docx|Doc}} | {{:tsc:lighting:getting_started_alljoyn_lighting_service_framework_14.06_lighting_sdk_android.pdf|pdf}}
        * Lighting SDK 14.06 for Android (Beta): [ Download](https///build.allseenalliance.org/lighting/view/v14_06/job/Lighting_SDK_Android_v14_06/lastSuccessfulBuild/artifact/release/Lighting_SDK_beta_Android_01_00_0325.zip)
        * Lighting SDK 14.06 for Android (Beta) Build Instructions: [Configure](https///build.allseenalliance.org/lighting/job/Lighting_SDK_Android_v14_06/configure )
        * Lighting SDK 14.06 Java Tutorial Project [ View](https///git.allseenalliance.org/cgit/lighting/apps.git/tree/tutorial-app/android/LSFTutorial/src/org/allseen/lsf/tutorial/TutorialActivity.java?id=v14.06 )
        * Lighting SDK 14.06 Beta for Android [ Source](https///git.allseenalliance.org/cgit/lighting/apps.git/tree/tutorial-app/android/LSFTutorial?id=v14.06 )
    * iOS
        * Lighting SDK 14.06 for iOS Getting Started Guide: {{:tsc:lighting:getting_started_lighting_sdk_14.06_ios.pdf|pdf}} 
        * Lighting SDK 14.06 for iOS (Beta): [ Download](https///build.allseenalliance.org/lighting/job/Lighting_SDK_iOS_Master/8/artifact/release/Lighting_SDK_beta_iOS_01_00_0125.zip)
        * Lighting SDK 14.06 for iOS (Beta) Build Instructions: [Configure](https///build.allseenalliance.org/lighting/job/Lighting_SDK_iOS_Master/configure ) 
        * Lighting SDK 14.06 iOS Tutorial Project [ View](https///git.allseenalliance.org/cgit/lighting/apps.git/tree/tutorial-app/iOS/LSFTutorial/LSFTutorial/LSFTutorialViewController.m?id=5e590fc1c13ba085102c2363bff90ef2e6cdd493 )
        * Lighting SDK 14.06 Beta for iOS [ Source](https///git.allseenalliance.org/cgit/lighting/apps.git/tree/tutorial-app/iOS/LSFTutorial?id=5e590fc1c13ba085102c2363bff90ef2e6cdd493 )


Who should use the Lighting SDK?

*  Mobile Application Developers who want to quickly begin interfacing with AllJoyn compatible lamps.
# Getting Started

 1.  Watch the Overview Presentation on LSF from Uplinq 2014: [ Watch via YouTube](http://youtu.be/3lNzNj5ytqM?list=PLxeazpXYyqtNm2EnCbfSzy7aKOkHjiaSi ) and [ View the Presentation](http://www.slideshare.net/QualcommDeveloperNetwork/80-connected-lighting-vogelsangfok919gg45 )
 2.  Download and install the V.14.06 Sample Application for Android on an Android Smartphone (Device 1): [ APK Download](https///build.allseenalliance.org/lighting/view/v14_06/job/Lighting_Sample_App_Android_v14_06/lastSuccessfulBuild/artifact/release/LSFSampleApp_Android_01_00_0794_debug.apk )
 3.  Download and install the Lamp Simulator Application, called Luminaire, from Google Play on another Android Smartphone (Device 2): [ Download from Google Play](https///play.google.com/store/apps/details?id=com.qualcomm.luminaire )
 4.  Make sure that both the Sample Application running on Device 1 and Luminaire running on Device 2 are both on the same Wi-Fi network. 
 5.  Launch Luminaire on Device 2 and enable the Lighting Controller via the on/off switch under the Controller tab. 
 6.  Launch the Sample Application on Device 1.
 7.  You should now see the virtual lamp in Luminaire from the Sample Application, and can control its properties just like a physical bulb, e.g. control Hue, Saturation, Color Temperature, and Brightness and create Presets, Groups, and Scenes that include Effects. Protip: Run multiple instances of Luminaire on separate devices to simulate multiple lamps.
 8.  Download the [ Lighting SDK 14.06 for Android (Beta):](https///build.allseenalliance.org/lighting/view/v14_06/job/Lighting_SDK_Android_v14_06/lastSuccessfulBuild/artifact/release/Lighting_SDK_beta_Android_01_00_0325.zip) which can be used to manipulate the virtual lamp in Luminaire.  
 9.  Create a Scene with the LSF Sample and Experiment with the Scenes Events and Actions exposed via Luminaire's instance of the Lighting Controller. Events & Actions are powerful ways to interoperate with the LSF.
 10.  If you're new to Android development, see [Building a sample Android app using the AllJoyn Lighting SDK](https///wiki.allseenalliance.org/lighting/Building_Android_Sample_with_Lighting_SDK)
# Features

The Features of the Lighting Service Framework include a common implementation into the open source, which accomplish the following: 

 1.  Controlling individual state of a Lamp such as On/Off, Hue, Saturation, Color Temperature, or Brightness. 
 2.  Managing Groups of Lamps, including creating, naming, and deleting groups allowing them to be controlled together as if they were a single lamp.
 3.  Saving lighting preferences called "Presets" allowing a particular state to be named stored for future use. 
 4.  Applying lighting Effects like pulsing the Lamps or transitioning them to a particular state over time.
 5.  Creating Lighting Scenes and Master Scenes comprised of Lamps or groups of Lamps and associated preferences and Effects that can be applied to set a mood or ambiance. 

For a complete list of features please see the AllSeen Summit [Presentation](https///wiki.allseenalliance.org/_media/tsc/lighting/connectedlighting_allseen_summit_nov_2014_v04.pdf)

# Release Planning

*  v15.04
       * [Lighting 15.04 Release Review](https///wiki.allseenalliance.org/lighting/lighting_15.04_release_review)

*  v14.12
       * [Lighting 14.12 Release Review](https///wiki.allseenalliance.org/lighting/lighting_14.12_release_review)


# Dependencies

The project is dependent on the 14.12 of AllJoyn Core and Base Services. Please refer to each component (above) for details.  There are no external dependencies. 

# Committers and Contributors

===Maintainer:=== 


*  Marc Alexander, CTO, LIFX

#### Committers:


*  Bharanee Rathna, Engineer, LIFX 

*  Marc Alexander, CTO, LIFX

*  Dean Camera, Engineer, LIFX 

*  Shane Hanna, Engineer, LIFX 

*  Eric Rongo, Senior Engineer, Qualcomm Connected Experiences

*  Padma Narayanan, Senior Engineer, Qualcomm Connected Experiences

*  David Diplock, Staff Engineer, Qualcomm Connected Experiences

*  Jason Fullen, Engineer, Qualcomm Connected Experiences

===Contributors:=== 


*  Brian Vogelsang, Director Product Management, Qualcomm Connected Experiences (brian at qce.qualcomm.com}

*  Kenny Fok, Director Engineering, Qualcomm Connected Experiences
 

# Resource

*  Mailing List: `<allseen-lighting@lists.allseenalliance.org>` ([Subscribe](https///lists.allseenalliance.org/mailman/listinfo/allseen-lighting))

*  Issue Tracker: [ASALIGHT JIRA](https///jira.allseenalliance.org/browse/ASALIGHT)

*  Overview Presentation on LSF at Uplinq 2014: [http://youtu.be/3lNzNj5ytqM?list=PLxeazpXYyqtNm2EnCbfSzy7aKOkHjiaSi](http://youtu.be/3lNzNj5ytqM?list=PLxeazpXYyqtNm2EnCbfSzy7aKOkHjiaSi)
# Projects

*  Lighting Service Framework Repository 
    * Clone: [https://git.allseenalliance.org/gerrit/lighting/service_framework](https///git.allseenalliance.org/gerrit/lighting/service_framework)
    * Browse: [https://git.allseenalliance.org/cgit/lighting/service_framework.git/](https///git.allseenalliance.org/cgit/lighting/service_framework.git/)

*  Lighting Sample Apps and SDK Repository 
    * Clone: [https://git.allseenalliance.org/gerrit/lighting/apps](https///git.allseenalliance.org/gerrit/lighting/apps)
    * Browse: [https://git.allseenalliance.org/cgit/lighting/apps.git/](https///git.allseenalliance.org/cgit/lighting/apps.git/)


# Roadmap

Features being considered for Q3 2015, based on AllJoyn Core 14.12.  


*  Support for AllJoyn Core 14.12

*  Lighting SDK Support for creating presets, groups, and scenes.

*  Lighting SDK Support for bundled Lighting Controller

*  Sample Apps for Android and iOS developed on Lighting SDK

