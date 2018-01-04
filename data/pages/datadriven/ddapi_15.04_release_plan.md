# (Data-driven API) 15.04 Release Plan

## Introduction

*  Dev lead : Kristof Martens

*  QA lead : Kristof Martens

## Themes and Priorities

Bring the DDAPI implementation in line with Core release 15.04. The only substantial code change we did was to use the new About API (introduced in R14.12), instead of the deprecated previous About API.

For R15.04, the DDAPI project did not invest time in the creation of new features or language bindings. Instead, the project is focused on contributing the essential functionality directly to the Core (Standard Client) project. The DDAPI as a separate API is on track to be phased out as soon as all relevant Core contributions have been done.

## Deliverables

Source:


*  Data-driven API Library (C++)

## Milestones

 | Milestone              | Date       | Details  | 
 | ---------              | ----       | -------  | 
 | API Freeze             | 2015/05/01 | complete | 
 | Feature Freeze         | 2015/05/01 | complete | 
 | Documentation Complete | 2015/05/19 | complete | 
 | QA Complete            | 2015/05/30 | complete | 



## Expected Work Group Dependencies


*  alljoyn: AllJoyn Standard client and router 15.04: 
      * Data-driven API library depends on the AllJoyn core library 

*  codegen: AllJoyn code generator 15.04:
      * Data-driven API code generator depends on the AllJoyn code generator

## Compatibility with Previous Releases

This release is fully forward and backward compatible with the DDAPI R14.12 release.
