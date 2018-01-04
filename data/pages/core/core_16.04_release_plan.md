# Core 16.04 Release Plan

## Introduction

The development lead is Way Vadhanasin

The QA lead is Kris Schuff

## Themes and Priorities

**New Features**:
Full list in [ JIRA](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASACORE%20AND%20issuetype%20%3D%20%22New%20Feature%22%20AND%20fixVersion%20%3D%20%2216.04%22%20ORDER%20BY%20status%20ASC)
 | JIRA Key/Link                                                                                   | Features                                                                                                                                        | 
 | -------------                                                                                   | --------                                                                                                                                        | 
 | [ASACORE-964](https///jira.allseenalliance.org/browse/ASACORE-964)                              | Support for unified introspection XML format                                                                                                    | 
 | [ASACORE-1393](https///jira.allseenalliance.org/browse/ASACORE-1393)                            | Security 2.0 (developer preview)                                                                                                                | 
 | [ASACORE-2055](https///jira.allseenalliance.org/browse/ASACORE-2055)                            | New password-based authentication mechanism ECDHE_SPEKE                                                                                         | 
 | [ASACORE-2254](https///jira.allseenalliance.org/browse/ASACORE-2254)                            | Support for a "const" annotation of interface description properties                                                                            | 
 | [ASACORE-2599](https///jira.allseenalliance.org/browse/ASACORE-2599)                            | StartManagement/EndManagement notifications for Security 2.0 apps                                                                               | 
 | [ASACORE-2607](https///jira.allseenalliance.org/browse/ASACORE-2607)                            | C APIs for Security 2.0                                                                                                                         | 
 | [ASACORE-2607](https///jira.allseenalliance.org/browse/ASACORE-2607)                            | XML-based Security 2.0 methods for handling Manifests, Policies and Rules                                                                       | 
 | [ASACORE-2660](https///jira.allseenalliance.org/browse/ASACORE-2660)                            | Reject attempts to Claim Security 2.0 app using an authentication mechanism that is not present in app's ClaimCapabilities                      | 
 | [ASACORE-2662](https///jira.allseenalliance.org/browse/ASACORE-2662)                            | Additional C APIs for InterfaceDescription                                                                                                      | 
 | [ASACORE-2710](https///jira.allseenalliance.org/browse/ASACORE-2710)                            | Support for multiple Security 2.0 Manifests for a single app                                                                                    | 
 | [ASACORE-2750](https///jira.allseenalliance.org/browse/ASACORE-2750)                            | Each Security 2.0 Manifest must be signed                                                                                                       | 
 | [secmgr wiki info](https///wiki.allseenalliance.org/release/15.09?s[]=securitymgr#release_1509) | Security Manager application (secmgr) is now a sample app of the Standard Core release. Secmgr was previously released outside of Core in 15.09 | 

## Deliverables

Source:

*  AllJoyn Standard Library (C++, C, Java)

*  AllJoyn Thin Library

AllJoyn Standard Library SDK:

*  Android


## Milestones

 | Milestone        | Date       | Details    | 
 | ---------        | ----       | -------    | 
 | Dev Complete     | 2016/03/18 | ✔        | 
 | Code Freeze      | 2016/04/22 | 2016/04/28 | 
 | QA Complete      | 2016/04/28 | ✔        | 
 | Alliance Release | 2016/04/30 | ✔        | 





## Expected Work Group Dependencies

None.

## Compatibility with Previous Releases

 See the [compatibility section in the Release Review](core_16.04_release_review?&#compatibility) for details on compatibility.
