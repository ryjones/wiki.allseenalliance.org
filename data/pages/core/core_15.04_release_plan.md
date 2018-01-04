# Core 15.04 Release Plan

## Introduction

Development leads are

*  Microsoft: Arvind Padole

*  QCE: Marcello Lioy

*  Qeo: Dominique Chanet 
The QA lead is David McBride.

## Themes and Priorities

**New Features**:
Full list in [ JIRA](https///jira.allseenalliance.org/i#issues/?filter=10810)
 | JIRA Key                                                             | Feature                                                | Contributor | 
 | --------                                                             | -------                                                | ----------- | 
 | [ASACORE-1392](https///jira.allseenalliance.org/browse/ASACORE-1392) | Remove excessive name transfer for all sessions        | QCE         | 
 | [ASACORE-1383](https///jira.allseenalliance.org/browse/ASACORE-1383) | Move essential DDAPI functionality to Alljoyn core     | QEO         | 
 | [ASACORE-803](https///jira.allseenalliance.org/browse/ASACORE-803)   | Router Selection Algorithm Definition and Mechanism    | QCE         | 
 | [ASACORE-1404](https///jira.allseenalliance.org/browse/ASACORE-1404) | Experimental : UDP Transport for TC `<->` RN connections | QCE         | 


## Deliverables

Source:

*  AllJoyn Standard Library (C++, C, Java, Obj C)

*  AllJoyn Thin Library

AllJoyn Standard Library SDK:

*  Android

*  XCode 

*  Visual Studio 2013

AllJoyn Thin Library SDK:

*  Linux

*  Windows

## Milestones

 | Milestone        | Date       | Details | 
 | ---------        | ----       | ------- | 
 | Dev Complete     | 2015/03/20 |         | 
 | Code Freeze      | 2015/04/20 |         | 
 | QA Complete      | 2015/04/27 |         | 
 | Alliance Release | 2015/04/29 |         | 

## Expected Work Group Dependencies

The change due to [ASACORE-1342](https///jira.allseenalliance.org/browse/ASACORE-1342) will require that all sample and test apps be updated with the new *Init* and *Shutdown* calls.

## Compatibility with Previous Releases

*  The AllJoyn Protocol Version changed from 11 to 12. While routers will support applications using older versions, the reverse is not true; i.e. applications requiring version 12 router features of will not work with older routers.

*  Uncrustify (white space checker) was migrated from v0.57 to v0.61; not updating the tool chain will cause the builds to break (ASACORE-1026)

*  Applications are now required to call ''AllJoynInit()'' before any other AllJoyn  calls,and ''AllJoynShutdown()'' after all other AllJoyn calls are complete ([ASACORE-1342](https///jira.allseenalliance.org/browse/ASACORE-1342)); as such, it is a change to the developer APIs, not to the wire  protocol and will not impact inter-version inter-operability.  Details and discussion can be found in this [mail thread](https///lists.allseenalliance.org/pipermail/allseen-core/2015-March/001287.html) on the Core WG mail list archive as well as in the [Jira ticket](https///jira.allseenalliance.org/browse/ASACORE-1342).

*  The names that are exchanged between Routers have changed ([ASACORE-1392](https///jira.allseenalliance.org/browse/ASACORE-1392));   specifically the number of names exchanged between 15.04 nodes has been greatly reduced, but is not expected to create inter-version compatibility issues as the original behavior is executed when interacting with older routers.  The change also has some API changes that *may* have an impact on developers.  Details can be found in the [Jira ticket](https///jira.allseenalliance.org/browse/ASACORE-1392) and any discussion can also be found in this [mail thread](https///lists.allseenalliance.org/pipermail/allseen-core/2015-March/001258.html) on the Core WG mail list archive.

*  The handling of ProxyBusObjects has changed to make them more sharable. Public APIs were deprecated and new calls were added. PropertyChangedListener  callbacks get passed a new instance of ProxyBusObject that references the state nformation of the ProxyBusObject the listener was registered with.  If a derived class was registered instead, the PropertyChangedListener cannot cast the returned ProxyBusObject instance back into the derived class.  If information from the derived class needs to be delivered to the callback, then it must be passed in as a context pointer. More details can be found in  [ASACORE-1522](https///jira.allseenalliance.org/browse/ASACORE-1522).

*  Header compression support was removed ([ASACORE-1534](https///jira.allseenalliance.org/browse/ASACORE-1534)).  This will only be an issue in the case where some applications are enabling header compression. This is unlikely as the feature was added to support sending small signals over BT carriers, and BT hasn't been a supported transport since pre-AllSeen AllJoyn releases.

*  Multipoint session member attach does not work in some backward compatibility scenarios ([ASACORE-1738](https///jira.allseenalliance.org/browse/ASACORE-1738))

*  The default configuration of the Windows Routing Node (daemonlib.dll) has changed to accept connections on TCP port 9955 instead of TCP port 9956 ([ASACORE-2000](https///jira.allseenalliance.org/browse/ASACORE-2000)); the default bus connect spec on Windows has been changed accordingly. Older Windows apps (using the older default bus connect spec) will no longer be able to connect to a 15.04a routing node. These apps should be recompiled using the new default connect spec. They may also require changes to your firewall settings.

*  Another impact of [ASACORE-2000](https///jira.allseenalliance.org/browse/ASACORE-2000) is 15.04a Bundled Routers now only accept connections on ephemeral TCP and UDP ports and don’t accept any connections using other transports. This means that applications using the default bus connect spec can no longer connect to a 15.04a Bundled Router on the local machine that is using the default bundledConfig settings.

*  The ''SessionListener::SessionLost(SessionId sessionId)'' callback (which has been deprecated since before 14.02) has been removed ([ASACORE-2048](https///jira.allseenalliance.org/browse/ASACORE-2048)). Applications should instead use ''SessionListener::SessionLost(SessionId sessionId, SessionLostReason reason)''. Existing applications recompiled with this release will notice that their ''SessionLost(SessionId sessionId)'' callback will no longer be called. By example the following sample source code has been updated with this change:
    * ''alljoyn_core/samples/eventaction/SimpleRulesEngine/Rule.cc''
    * ''services/about/cpp/samples/AboutClientSample/AboutClientSessionListener.cc''

**Security related**

*  The removal of PIN_KEYX from Standard Core Library ([ASACORE-1641](https///jira.allseenalliance.org/browse/ASACORE-1641)) will introduce inter-version inter-operability issues in the following scenarios (Details and discussion can be found in this [mail thread](https///lists.allseenalliance.org/pipermail/allseen-core/2015-March/001259.html) on the Core WG mail list archive.):
    * Pre-14.06 TC applications will not be able to connect to secured 15.04 Routing Nodes.
    * Any pre-15.04 applications that expose or use secure interfaces and only support PIN_KEYX will no longer work with their 15.04 or later peers. 

*  Support for DBUS_COOKIE_SHA1 authentication was removed ([ASACORE-1713](https///jira.allseenalliance.org/browse/ASACORE-1713)) - this means that as of 15.04 it will not be possible to use the Standard Core Library with the D-Bus Daemon if that authentication method is required.

*  Support for RSA authentication has been removed ([ASACORE-1716](https///jira.allseenalliance.org/browse/ASACORE-1716)); X.509-based certificate authentication is instead supported with ECDSA ([ASACORE-1561](https///jira.allseenalliance.org/browse/ASACORE-1561)).

*  Support for SPKI certificates for ECDHE_ECDSA was removed; as there were no public APIs exposing this functionality the impact of this change is expected to be minimal.

