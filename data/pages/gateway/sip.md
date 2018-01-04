# SIP End2End Connector Project

SIP End2End Connector is intended to be used as a [Gateway Agent](gateway/gatewayagent) connector app. It extends AllJoyn as a proximal protocol to be able to interact with the external network, including the far-end AllJoyn devices and Cloud Apps. It establishes a standard end-to-end mechanism for secure interoperations and interconnections across WANs.

## Main Features


*  End-to-end interoperations in a standard and transparent way over  [SIP (Session Initiation Protocol)](https///en.wikipedia.org/wiki/Session_Initiation_Protocol)

*  Third party applications/extensions with standard [SIP](https///en.wikipedia.org/wiki/Session_Initiation_Protocol) application servers

*  [Presence](https///www.ietf.org/rfc/rfc3856.txt)/Notification/Messages/[QoS](https///en.wikipedia.org/wiki/Quality_of_service)/[AAA](http://datatracker.ietf.org/wg/aaa/documents/) support out of box

*  Standard and open [SIP](https///en.wikipedia.org/wiki/Session_Initiation_Protocol)/[IMS](https///en.wikipedia.org/wiki/IP_Multimedia_Subsystem) network framework

*  Cloud platform based on Node.js will be available very soon (hosted by   [SmartConn](http://www.smartconn.cc))
## Releases

This project has not yet released.

## Release Plan

### 15.04

The first version will be based on the 15.04 release of AllJoyn core, and will also align with the corresponding version of [Gateway Agent](gateway/gatewayagent). It will be released in 2nd half of 2016.

## Contributors

The authoritative committer list is on the [Project Committers](tsc/committers#gateway) page. Names are also listed here to provide additional contact information.

#### SmartConn

*  Wei Ren - `<renwei@smartconn.cc>` ([SmartConn](http://www.smartconn.cc)) - project lead

*  Thierry Luo - `<luoyongheng@smartconn.cc>` - committer

*  Nan Wang - `<wangnan@smartconn.cc>` - committer

## Resources


*  Mailing List: `<allseen-gateway@lists.allseenalliance.org>` ([Subscribe](https///lists.allseenalliance.org/mailman/listinfo/allseen-gateway))

*  Issue Tracker: TBD

*  Repository:
    * Browse: https://git.allseenalliance.org/cgit/ajsipe2e.git
    * Or **git clone https://git.allseenalliance.org/gerrit/ajsipe2e.git**
### Original Project Proposal

{{:tsc:technical_steering_committee:alljoyn_sip_end2end_connector_project_proposal.pdf|AllJoyn SIP End2End Connector Project Proposal}}

To build and run the SIP E2E connector, please refer to [Get Started](Get Started). Currently we support the 32-bit build on Windows and the 32-bit/64-bit build on Ubuntu. The SIP E2E connector now runs as a standalone program and we are modifying the connector such that it will work with the gateway agent.

### Documents

TBD.

##  Jenkins builds

TBD.

## Test Cases

TBD.
