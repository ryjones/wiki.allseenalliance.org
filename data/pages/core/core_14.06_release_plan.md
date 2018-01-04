# Core 14.06 Release Plan

## Introduction

Development leads are Todd Malsbary and Craig Dowell.  The QA lead is David McBride.

## Themes and Priorities

New Features:

*  Next Generation Name Service (NGNS)

*  UDP Transport

*  Security Enhancements

*  Policy DB

*  Sessionless Signal (SLS) Improvements

*  Events and Actions

*  WMI SPI Layer (WSL) for Thin Library

## Deliverables

Source:

*  AllJoyn Standard Library (C++, C, Java, Obj C, JavaScript, Unity)

*  AllJoyn Thin Library

AllJoyn Standard Library SDK:

*  Android

*  XCode 

*  Visual Studio 2012

AllJoyn Thin Library SDK:

*  Linux

*  Windows

## Milestones

 | Milestone        | Date       | Details | 
 | ---------        | ----       | ------- | 
 | Dev Complete     | 2014/05/23 |         | 
 | Code Freeze      | 2014/06/13 |         | 
 | QA Complete      | 2014/06/25 |         | 
 | Alliance Release | 2014/06/30 |         | 

## Expected Work Group Dependencies

AllJoyn Base Services

## Compatibility with Previous Releases

Newer thin library clients will be unable to authenticate with older thin library clients, due to SASL/PINX deprecation for thin library in this release. 
