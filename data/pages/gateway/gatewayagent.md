# Gateway Agent Project

## Gateway Agent Main Features


*  Provides an AllJoyn routing node that includes added routing management for connections with external network devices and services. As of version 15.04 use this in your device instead of a standard AllJoyn routing node - provides both local AllJoyn routing and managed interfaces with external protocols.

*  Supports plug-in Connector Apps to facilitate interoperable, third-party service connections with AllJoyn device applications. *Note: Connector Apps can be contributed as separate AllJoyn projects supporting the Gateway Agent, or developed as proprietary Connector Apps*

*  External access rights are managed by the local network owner, or with granted authority by a services provider

*  **Examples use cases:** *typically will be run in an always-on device in the LAN (hub, appliance) or a router or Internet gateway*
    * Provide secure remote access for AllJoyn mobile apps to AllJoyn devices that are in the local network at home
    * Support a third-party managed services for AllJoyn automation applications
    * Implement protocol conversion between an AllJoyn network segment and other non-AllJoyn automation devices and protocols.  i.e. between AllJoyn and popular layer 2 automation protocols (Z-wave, ZigBee, BLE, etc)
    * Join multiple local AllJoyn networks into a larger multiple segment network

## Releases

### 16.04

**In development - scheduled release by September 30, 2016**

This release will add the following to the 15.04 release:

*  Support for AllJoyn Core and Base Services 16.04

*  Prior to release compatibility fixes for 16.04 compatibility are found in the Master Branch of the Git repository.

*  Bug fixes

Note the package manager for AllJoyn.js modules has now been pushed out of the 16.04 release until the 16.10 release for Gateway Agent.  The release plan and schedule for 16.10 Gateway Agent has not been finalized.

### 15.04

**Scheduled for release by August 31, 2016**
[Gateway Agent 15.04 Release Plan](gateway/gateway_15.04_release_plan)

This release includes:

*  Released support for AllJoyn Core and Base Services at version 15.04. This is in the RB15.04 of the Git repository.

*  Use its built-in AllJoyn routing node, which replaces the need for a separate AllJoyn daemon.

*  Bug fixes.

*  Certification and Compliance test cases are unchanged from the 14.12 release

### 14.12

The Gateway Agent is released supporting AllJoyn Core 14.12. With this release, the main components are:


*  Gateway Management Application - note requires that you include a standard AllJoyn router as well.

*  Sample connector application (example for AllJoyn to Twitter)

*  Control Application (for Android and iOS) for managing the Gateway Agent service profile

#### Release information for 14.12 version


*  [Gateway Agent 14.12 Release Plan](gateway/gateway_14.12_release_plan)

*  Release Review - *documentation coming soon*

*  {{:gatewayagent:alljoyn_gateway_service_framework_interface_definition_14.12a.docx|AllJoyn Gateway Service Framework Interface Definition 14.12a}} Revised to resolve JIRA case ASAGW-54, see that case for details.

*  {{:gatewayagent:alljoyn_gateway_service_framework_14.12_test_case_specifications.docx|AllJoyn Gateway Service Framework 14.12 Test Case Specifications}}

#### Base Implementation Information (for AllSeen Alliance IP Policy)

The Gateway Agent project released version 14.12 of the Gateway Agent on 19 April 2015. This release is now a candidate for inclusion in the Base Implementation. It was presented to the TSC on 20 April 2015 and unanimously approved. The Alliance Board was notified on 21 April 2015 that this Base Implementation component was accepted. With this notification, the initial 90 day review period for 14.12 Gateway Agent began and will complete on 20 July 2015 at midnight PST. Upon completion of the review, the 14.12 Gateway Agent candidate will become an official component of the Base Implementation.  See https://allseenalliance.org/compliance for more information.

## Connector Projects

There are now multiple active Connector projects that are compatible with the Gateway Agent application.  The links to their project pages can be found on the Gateway Working Group wiki page at [Gateway Working Group](gateway/gateway).  In addition to the functionality that each offers, they are also great examples to review to consider other connectors for other purposes that you may wish to propose.

You can contribute to the Gateway Agent by creating a Connector App. Connectors bridge one or more devices to your cloud or external networking service. Note that Connector Apps can be used in a stand alone fashion with a standard routing node as well as with the Gateway Agent's managed AllJoyn routing interface.

Connector code may be proprietary, but connectors are more useful to the public as open source projects. Although you would be creating a connector for free and public use, you can still profit from open-source connectors by charging the usage of your cloud services.

You can publish your connector app as part of the Allseen Gateway Agent code, exposing it to developers interested in using Connector apps.

Here is the process to contribute a Connector:
 1.  Propose a project to the Technical Steering Committee (TSC). See the [Proposing a Connector Project](https///wiki.allseenalliance.org/gateway/proposing_a_connector_project) page to understand how to do this.
 2.  The project will be introduced to the TSC at the next meeting and two weeks later they will vote on its approval.
 3.  Assuming the project is approved by the TSC the committers will be given access to the git repository.
 4.  It is suggested that at least one representative from the team working on the project attend the [Weekly Technical Meetings](https///wiki.allseenalliance.org/gatewayagent/gateway_wtm) while it is being developed.
 5.  Contributions to the repository will be submitted to Gerrit for review by other committers in AllSeen before being published to the repository. The [Contribution Training](https///wiki.allseenalliance.org/develop/contributing_source_code) article provides details on this process.

## Gateway Agent Getting Started

Please refer to the [Getting Started](gateway/getting_started) page for more information.

## Resources

*  Issue Tracker: [ASAGW Jira](https///jira.allseenalliance.org/browse/ASAGW)

*  Repository:
    * Browse: https://git.allseenalliance.org/cgit/gateway/gwagent.git/

*  Mailing List (shared with other Gateway Workgroup projects): `<allseen-gateway@lists.allseenalliance.org>` ([Subscribe](https///lists.allseenalliance.org/mailman/listinfo/allseen-gateway))

##  Weekly Technical Meetings

Working group weekly technical meetings for active contributors and for interested Alliance members and others interested in this working group.  Details of the schedule, and the Webex information are at the following page.


*  [Gateway Working Group Weekly Meetings](gateway/gateway_working_group_weekly_meetings)

## Contributors

The authoritative committer list is on the [Project Committers](tsc/committers#gateway) page. Names are also listed here to provide additional contact information.

#### Affinegy

*  Art Lancaster - Working Group Chair - `<alancaster@affinegy.com>`

*  Josh Spain - `<jspain@affinegy.com>`

*  Andrey Krokhin
#### Qualcomm Connected Experiences, Inc.

*  Ken Swinson

## Gateway Agent Documents

### Overview Presentations

*  Linux Collaboration Summit Feb 2015 - presentation on security best practices and the Gateway Agent's role in implementing these with AllJoyn {{:gateway:security_privacy_and_iot_linux_foundation_collab_2015-02.pdf|}}

*  AllSeen Gateway Agent Overview - as presented at CES 2015
    * {{:gateway:allseen_gateway_agent_overview_ces2015.pdf|PDF version - easier to view quickly}}
    * {{:gateway:allseen_gateway_agent_overview_ces2015.pptx|PowerPoint version - easier to include portions in other presentations}}

*  AllSeen Alliance Summit - 2014/11/11 Working Group Breakout Session Presentation (note this includes all slides from the Wednesday Nov 12 Keynote, and adds some addition slides on the demo provided in the breakout session).
    * {{:gateway:lancaster_allseen_summit_2014-11_breakout.pdf|}}
    * Video of keynote - [YouTube video of the AllSeen November Summit Gateway Agent keynote speech by Art Lancaster](http://youtu.be/vcc71BHnGQw)

### Design Documents and Specifications

 1.  **Interface Definition Document** See the 14.12 Release information section above on this page.
 2.   **Test Cases Specification Document** See the 14.12 Release information section above on this page.
 3.  **API Specification Linux Gateway Agent** This is the formal API specification for the Gateway Agent Connector Interface Service in Linux. Use this for developing Connector plug-ins to the Gateway Agent application. {{:gateway:gateway_connector_service_api_guide_linux_2015_0203.pdf|}}
 4.  **API Specification Control Application** This is the formal API specification for the Control Application interface of the Gateway Agent.  It is for developing Control Applications that configure the Service Profile and manage the Connector Plug-ins state for the Gateway Agent. An example is implemented in the Android Java Control Application. {{:gateway:gateway_controller_framework_api_guide_java_2015-0204a.pdf|}}
 5.  **High Level Design Document** - The specification document for the Gateway Agent Design.
    - **Update 3** - changes to interfaces. {{:gateway:alljoyn-gateway-agent-hld_rev1-update3.docx|Gateway Agent HLD - Update 3}}
    - **Update 2** - changes to interfaces, text and diagrams for capturing Connector Id (instead of App Id) as the unique identifier for the connector apps. {{:gateway:alljoyn-gateway-agent-hld_rev1-update2.docx|Gateway Agent HLD - Update 2}}     {{:gateway:alljoyn-gateway-agent-hld_rev1-update2-redline.docx|Gateway Agent HLD - Update 2 (Redline Version)}}
    - **Amendment 1** - Adds a Service Provider Mode optimized for broadband operators, automation services providers, or product with services providers. This details the TR-069 management features of the Gateway Agent for secure provisioning and management control by a services provider.  {{:gateway:gateway_agent_hld_amendment_1_service_provider_mode.pdf|Gateway Agent HLD Amendment 1}}
    - **Update 1** - revises component names for improved clarity and consistency for interaction with other projects. {{:gateway:allJoyn-gateway-agent-hld_rev1-update1.pdf|Gateway Agent HLD - Update 1}}
    - **Original version** - for prior continuity {{:gateway:alljoyn-gateway-agent-hld.pdf|}} {{{{:gateway:gateway_agent_hld_-_chinese.pdf|Unofficial Chinese version, Thanks to Junjie Zhao at LeTV}}
### Original Proposal and Proposal Presentation

 1.  The working group proposal document:  {{:tsc:technical_steering_committee:proposals:allseen_gateway_workinggroup_proposal_affinegy.pdf|Gateway Agent Proposal}}
 2.  Presentation to the TSC of the working group proposal:  {{:tsc:technical_steering_committee:proposals:gateway_working_group_proposal_presentation.pdf|}}

### Other Files

#### 14.12 release

*  [Android Gateway Controller Sample SDK](https///mirrors.kernel.org/allseenalliance/alljoyn/14.12/alljoyn-gwagent-14.12.00-android-sdk-rel.zip) (apk for Android sample app is at alljoyn-android\gwagent\alljoyn-gwagent-14.12.00-rel\tools\GatewayController.apk)

*  [iOS Gateway Controller Sample SDK](https///mirrors.kernel.org/allseenalliance/alljoyn/14.12/alljoyn-gwagent-14.12.00-ios-sdk-rel.zip)

####  Jenkins builds

*  [RB15.04](https///build.allseenalliance.org/ci/view/Gateway%20RB15.04/) - continuous builds against RB15.04

*  [RB14.12](https///build.allseenalliance.org/ci/view/Gateway%20RB14.12/) - continuous builds against RB14.12

*  [master](https///build.allseenalliance.org/ci/view/Gateway%20Master/) - continuous builds against master

*  [verify](https///build.allseenalliance.org/ci/view/Gateway%20verify/) - verify builds for gerrit patches (master and RB14.12 changes)

*  [tagged](https///build.allseenalliance.org/ci/view/Gateway%20tagged/) - tagged builds (for building from a release tag)
Views referenced above include jobs for building the Android Gateway Controller SDK, iOS Gateway Controller SDK, Documentation, Linux binaries, and OpenWrt ipks. The OpenWrt build currently produces ipks for the ar71xx platform based on the Barrier Breaker 14.07 release. Current testing platform is [TP-Link TL-WR842ND](http://wiki.openwrt.org/toh/tp-link/tl-wr842nd)

####  Gateway Agent Test Cases

*  "AllJoyn Gateway Agent" project in [TestLink](https///tl.allseenalliance.org/)

*  Spreadsheet used for initial import of test cases into TestLink {{gateway:gatewayagent_testcases_14.12.xlsx|}}
