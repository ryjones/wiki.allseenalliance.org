# Developer Support 15.09 Release Plan

## Introduction

Developer and QA: Mathew Martineau

## Themes and Priorities

Bring code generator forward for core 15.09. DDAPI support has been removed because DDAPI is now an archived project and will not have a 15.09 release.

## Deliverables

AllJoyn Code Generator for Thin Library and Android Java.

The main work is to update the thin library code generator to handle the ajtcl code reorganization.

## Milestones

 | Milestone         | Date       | Details | 
 | ---------         | ----       | ------- | 
 | Dev & QA Complete | 2015/11/20 |         | 
 | Final release     | 2015/11/30 |         | 

## Expected Work Group Dependencies

There are no known impacts on other work groups from the expected changes in the tools.

## Compatibility with Previous Releases

### Code Generator

Due to code reorganization, the output of codegen 15.09 will only work with ajtcl 15.09 (and, hopefully, future versions).

