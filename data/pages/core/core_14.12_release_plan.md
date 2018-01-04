# Core 14.12 Release Plan

## Introduction

Development leads are Todd Malsbary, Craig Dowell and Peter Krystad.  The QA lead is David McBride.

## Themes and Priorities

New Features:

*  Major Stabilization fixes for the system when it is under load.

*  Hardening and performance improvements of the UDP RN to RN transport

*  Integration of the About feature into the core framework; side effect is that the service/about APIs are deprecated.

*  Support for the Self-Join session feature

*  Auto-pinger feature

*  Migration of PropertyChanged signal from BusListener to ProxyBusObject

*  Blacklisting feature for TC RN discovery: blacklist RNs that the TC cannot connect to

*  Support for discovering RN using mDNS (i.e. NGNS) 


## Deliverables

Source:

*  AllJoyn Standard Library (C++, C, Java, Obj C)

*  AllJoyn Thin Library

AllJoyn Standard Library SDK:

*  Android

*  XCode 

*  Visual Studio 2012

AllJoyn Thin Library SDK:

*  Linux

*  Windows

## Milestones

 | Milestone        | Date       | Details                                                | 
 | ---------        | ----       | -------                                                | 
 | Dev Complete     | 2014/11/17 | SC on track, TC likely slip a couple of days           | 
 | Code Freeze      | 2014/12/10 | Some critical fixes were added post CF date            | 
 | QA Complete      | 2014/12/15 | complete                                               | 
 | Alliance Release | 2014/12/17 | complete                                               | 
 | 14.12a patch     | 2015/01/30 | AllJoyn.git only project updated\\ Released 2015/01/27 | 

## Expected Work Group Dependencies

N/A

## Compatibility with Previous Releases

There are no expected compatibility issues.
