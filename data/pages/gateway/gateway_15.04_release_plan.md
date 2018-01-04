# Gateway Agent 15.04 Release Plan

## Introduction

Dev Lead: Josh Spain

QA Lead: Jes Golka

## Themes and Priorities

The 15.04 release of the Gateway Agent is designed to be compatible with AllJoyn Core and Base Services 15.04.

This release will no longer be dependent on the standalone AllJoyn daemon, but will instead use a built-in routing node. It will therefore act as and should be used in place of the standalone daemon.

### Changes

The following changes are made to this release:

*  Support for AllJoyn Core and Base Services 15.04

*  Bug fixes

*  No support for iOS (the code exists but has not been updated or tested)

### Components

The following major components are available in this release:

   * Gateway Management App (Linux/C++)
   * Gateway Connector API (Linux/C++)
   * Gateway Controller API (Android/Java)

### Samples

The following samples are provided in this release:

   * Gateway Connector Linux sample (Linux/C++)
   * Gateway Controller Android sample (Android/Java)

## Deliverables

The following deliverables are provided to the community:

   * Gateway Agent Linux SDK
   * Gateway Controller Android SDK
   * OpenWrt feed
   * Developer Documentation

## Milestones

 | Milestone              | Date       | Details  | 
 | ---------              | ----       | -------  | 
 | API Freeze             | 2016/03/01 | complete | 
 | Feature Freeze         | 2016/05/31 | "        | 
 | QA Complete            | 2016/08/12 | "        | 
 | Documentation Complete | 2016/08/31 |          | 




## Expected Work Group Dependencies


*  Core 15.04

*  Base Services 15.04

## Compatibility with Previous Releases


*  14.12

