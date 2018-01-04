# XMPP Connector Project

The XMPP Connector bridges two AllJoyn buses over XMPP. It is called a Connector because it is intended to be used as a [Gateway Agent](gateway/gatewayagent) Connector app because of its ability to reach outside the local network into an external network.

## XMPP Connector Main Features


*  Bridges a local AllJoyn bus to a remote AllJoyn bus over XMPP

*  Supports the AllJoyn Gateway Agent as a standard connector [see Gateway Agent Project](gateway/gatewayagent).  Also usable on its own with a standard AllJoyn router.

*  Allows easy configuration of XMPP parameters via a secured AllJoyn interface

*  Supported by XMPP standard servers with open source implemented APIs. A hosted XMPP server cloud service freely available for AllJoyn IOT product development, which commercial service available. (hosted by [Affinegy, Inc.](http://www.affinegy.com)).

*  Supports OpenWRT and Linux platforms. An Android mobile app version and SDK of XMPP connector is also available from Affinegy.

*  Easily customizable for OEMs

## Releases

This project has not yet released.

## Upcoming Releases

### 16.04

The initial XMPP Connector will be released to support AllJoyn Core 16.04. This release will also be tested and verified with Gateway Agent version 15.04. With this release the main components below are included.


*  XMPP Connector C++ source code and documentation

*  Free developer account and resources through [Affinegy's CHARIOT service](http://dev.chariot.global), courtesy of [Affinegy, Inc.](http://www.affinegy.com)

The XMPP Connector is currently at a beta level and highly functional for development usage. It is available in the AllSeen Git repository at [](https///git.allseenalliance.org/cgit/xmppconn.git/)

Release plan for 16.04 is coming soon - expected release by end of September 2016. [XMPP Connector Release Plan 16.04](XMPP Connector Release Plan 16.04)


## Contributors

The authoritative committer list is on the [Project Committers](tsc/committers#gateway) page. Names are also listed here to provide additional contact information.

#### Affinegy

*  Josh Spain - `<jspain@affinegy.com>` - project lead

*  Andrey Krokhin - `<akrokhin@affinegy.com>` - committer

## Resources

*  Mailing List: `<allseen-gateway@lists.allseenalliance.org>` ([Subscribe](https///lists.allseenalliance.org/mailman/listinfo/allseen-gateway))

*  Issue Tracker: TBD

*  Repository:
    * Browse: https://git.allseenalliance.org/cgit/xmppconn.git/

## Getting Started

TBD

## Documents

### Overview Presentations

*  {{:gateway:alljoyn_xmpp_connector_project_proposal.pdf|XMPP Connector Project Proposal}}

### Design Documents and Specifications

TBD

##  Jenkins builds

TBD

## Test Cases

TBD
