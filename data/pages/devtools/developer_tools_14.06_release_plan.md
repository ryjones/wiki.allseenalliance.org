# Developer Tools 14.06 Release Plan

## Introduction

This plan is not yet complete. Similar to release 14.02, the code generator will be released later than other components in order to devote QA resources to other working groups for the main 14.06 release date.


*  Dev Lead: Mathew Martineau

*  QA Lead: David McBride

## Themes and Priorities

This release cycle focuses on enhancements to the Code Generator to work with version 14.06 of the core and implement new Java capabilities.

## Deliverables

#### Code Generator

The AllJoyn code generator gains a major new feature to create Android Java code for the standard library Java bindings. Full Android Java applications, including ready-to-build workspaces, will be generated from the XML API description. One application implements the described objects and interfaces and another application interacts with the APIs.

In addition, the Thin Library code generator will be updated to work with the 14.06 Thin Library APIs.

## Milestones

 | Milestone              | Date       | Details                                                           | 
 | ---------              | ----       | -------                                                           | 
 | Feature Freeze         | 2014/06/06 |                                                                   | 
 | Documentation Complete | TBD        | Need documentation scope and estimate                             | 
 | QA Complete            | TBD        | QA engineers are not available until after the core 14.06 release | 

## Expected Work Group Dependencies

The code generator depends on two projects from the Core Working Group, the Standard Library Java bindings (part of core/alljoyn) and the Thin Library (core/ajtcl). This version of the code generator does not use new AllJoyn Java APIs added in 14.06.

## Compatibility with Previous Releases

Version 14.06 of the code generator creates applications suitable for use with version 14.06 of the core standard and thin libraries. To use older versions of the core libraries, also use an older version of the code generator.
