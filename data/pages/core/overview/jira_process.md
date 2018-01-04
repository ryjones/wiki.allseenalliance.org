# Use of Severity and Priority Settings in Jira Projects

*  Last Updated: Jun 11, 2015

*  Approved by Core WG: June 4, 2015


## Introduction

The AllJoyn project uses Jira for issue tracking.  Although Jira includes settings for both Severity and Priority, the AllJoyn project has primarily used the Priority setting as a catch-all, and has not systematically used Severity.  

As the project has grown and the workload on the Jira triage team has grown, due to the increasing volume of Jira tickets, the team has recognized that using both Priority and Severity settings would add useful context to the Jira tickets and also make the Jira triage process more efficient.
The goal of this document is to propose a common definition and a common application of the Priority and Severity settings.  A {{core:overview:severity_poster.pdf|poster}} has been created that summarizes the process for assigning severity.
## Definitions

### Priority

“Priority” refers to the relative ordering of Jira issues for resolution, as determined by the Jira triage team, using input from stakeholders.  Managers and developers use priority settings to determine which issues should be resolved before other issues.

Jira uses the Priority rankings P1, P2, P3, P4, and P5, with P1 being the highest priority and P5 being the lowest.  New issues default to P3.

Priority is a dynamic attribute.  It conveys the ordering of issues at a given moment in time.  Priority is subject to change as existing issues are resolved and new issues emerge.  So, the priority of a particular issue several months from a release may be quite different than the priority a few weeks from the release.  Priority settings change as business and technical interests change.
### Severity

“Severity” refers to the level of impact that the bug has on the system, as well as the frequency, or probability of occurrence (Figure 1).  Although the Jira application allows for severity to be applied to any issue type, we will only recognize the severity setting for “bugs”.  All other issue types (e.g. new feature, task) will be set to “None”.

The AllSeen Alliance will use the following severity settings:  Blocking, Critical, Major, and Minor.  Jira includes a fifth setting, “Moderate”; however, this setting won’t be recognized and will be converted to “Minor” if it is used in a Jira ticket.

Unlike the priority setting, severity should be fixed for the lifetime of the ticket, unless a mistake was made in determining the severity level.  The reason for this is that, unlike priority, severity is based on characterisitics of the issue, rather than current business or technical interests.  

{{:core:overview:severitysettingstable.jpg|}} 
### Frequency and Probability

Frequency and probability is a somewhat subjective assessment of the likelihood that an issue will occur in the “real world” and how often.  An issue that is readily reproducible by stress testing may still be considered low probability if the means by which the issue was generated is unlikely to occur outside of the stress test.

The triage team will determine the magnitude of the horizontal axis as follows:
 1.  Assign a 0 or 1 to each of frequency and probability (0 = low; 1 = high).  These assignments are based on input from the reporter.
 2.  Add the two values together

    * 0 maps to the left column in the table
    * 1 maps to the middle column in the table
    * 2 maps to the right column in the table
### Impact on System

The impact on the system is determined by assessing the effect on functionality, the ability to recover without user intervention, and the presence of workarounds.
Figure 2 illustrates the process for determining impact.
#### High Impact


*  Affects primary functionality (see Appendix A)
    * Recovery without intervention is unlikely
    * There are no workarounds

*  Security vulnerability
    * Authentication, message integrity, or system availability are at risk
#### Medium Impact


*  Affects primary functionality (see Appendix A)
    * Functionality may recover on its own
    * Or, there is a workaround

*  Affects secondary functionality
    * Recovery without intervention is unlikely
    * There are no workarounds
#### Low impact


*  Affects secondary functionality (see Appendix A)
    *  Functionality may recover on its own
    *  Or, there is a workaround

*  Affects tertiary functionality
{{:core:overview:jiraflowchart.jpg|}} 

## Setting severity for tasks and features

*  Severity settings for features and tasks relates exclusively to their importance with respect to the release they are scheduled for:
    * **Minor**: *nice to have*
    * **Major**: *desirable*, but best effort
    * **Critical**: *highly desirable*, but won’t block release if incomplete
    * **Blocking**: *required*, and will block release if not completed

*  These definitions have the following benefits *(these bullets will be removed when no longer in draft state)*:
    * Easier tracking of tasks required / desired for a release
    * Keeps severity and priority separate
      * Severity relates to the code base / release
      * Priority relates to workload management


## Roles

The priority and severity settings will be managed and used different, depending on the role of the user.
### Triage Team

The triage team is responsible for setting priority and severity.  This willl be done as part of regular, public meetings.  Stakeholders may attend the triage team meetings and express their opinion about the settings, or the triage team may solicit input from stakeholders on particular issues.
### Management

Management is responsible for ensuring that engineering resources are assigned according to the priority settings determined by the triage team.
### Development and Test Engineering

Engineers are responsible for identifying and documenting issues.  However, they are not responsible for setting the priority and severity levels, although they may offer their opinion.

In order to assist the triage team, the reporter will document the frequency with which the issue may be reproduced.  Jira includes a field for this purpose.  In addition, the reporter will offer an assessment of the probability of the issue occurring in a real-world deployment.

In addition, engineers are responsible for resolving issues as assigned by management, in order of the priority determined by the triage team.

## Appendix A

 
### Primary, Secondary, and Tertiary Functionality

#### Primary

*  Discovery

*  Session establishment

*  Methods, signals, and properties
    * Marshalling / Unmarshalling

*  LN-RN transports

*  RN-RN transports

*  Language bindings

*  Security
    * Authentication
    * Encryption

*  Unintentional app compatibility breakage

*  Protocol compatibility
    * Supported platform
    * Version 

#### Secondary

*  Observer

*  Presence

*  Router selection

*  Performance

*  Unsupported version of supported platforms

*  Policy DB (this is an optional feature)

*  API Documentation

*  Samples

#### Tertiary

*  Auth pinger

*  Raw sessions

*  Unsupported platforms

*  Non API documentation
    * Example: ReadMe
##  Feedback and requesting a change in process

Please refer to the process change and feedback [[https://wiki.allseenalliance.org/core/overview/wg_process#changing_process|linked here.
]]

This page is expected to evlove over time. Your feedback is encouraged. Please use the discussion widget at the bottom of this page to submit your feedback and ideas. 

If other working groups or projects choose to leverage this process and make changes to the process, please add your changes to the discussion below and the Core WG team will see if it should be added to this page. 

~~DISCUSSION~~
