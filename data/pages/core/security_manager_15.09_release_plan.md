# Security Manager 15.09 Release Plan

## Introduction

The development leads are:


*  Qeo: Kristof Martens

The Q.A. leads are:


*  Qeo: Kristof Martens
## Themes and Priorities

 | JIRA Key                                                             | Feature                                                                        | Contributor | 
 | --------                                                             | -------                                                                        | ----------- | 
 | [ASACORE-2010](https///jira.allseenalliance.org/browse/ASACORE-2010) | Claim factory reset application without out-of-band registration data          | QEO         | 
 | [ASACORE-2011](https///jira.allseenalliance.org/browse/ASACORE-2011) | Claim factory reset applications using out-of-band registration data           | QEO         | 
 | [ASACORE-2012](https///jira.allseenalliance.org/browse/ASACORE-2012) | Change security configuration of claimed applications                          | QEO         | 
 | [ASACORE-2013](https///jira.allseenalliance.org/browse/ASACORE-2013) | Change security configuration of offline applications                          | QEO         | 
 | [ASACORE-2014](https///jira.allseenalliance.org/browse/ASACORE-2014) | Provide platform independent CA/storage abstraction layer for security manager | QEO         | 
 | [ASACORE-2017](https///jira.allseenalliance.org/browse/ASACORE-2017) | Certificate revocation by blacklisting peers in the policy                     | QEO         | 
 | [ASACORE-2086](https///jira.allseenalliance.org/browse/ASACORE-2086) | Enforce syntax of DENY rules in policies                                       | QEO         | 
 | [ASACORE-1401](https///jira.allseenalliance.org/browse/ASACORE-1401) | AllJoyn Security Manager sample app for Windows                                | MSFT        | 

## Deliverables

Source:

*  Security Manager (C++)
    * The Security Manager API and its standard client implementation
    * A Storage API with a sample implementation
    * A sample implementation of a CLI based Security Manager
## Milestones

 | Milestone                       | Date       | Details | 
 | ---------                       | ----       | ------- | 
 | Release Branch creation         | 2015/09/23 | ✔     | 
 | Cut-off date for Release Branch | 2015/10/01 | ✔     | 
 | Alliance Release                | 2015/10/01 | ✔     | 

## Expected Work Group Dependencies

The Security Manager 15.09 delivery depends on:

*  AllJoyn: AllJoyn Standard Core - 15.09

## Compatibility with Previous Releases

No incompatibilities as this is the first release for security manager.
