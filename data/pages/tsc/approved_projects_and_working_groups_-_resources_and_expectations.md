# Approved Projects and Working Groups: Resources and Expectations

Once the TSC has approved a project or working group, the participants in the project or working group have some work to do in order to provide an appropriate overview, configure important infrastructure, and satisfy Compliance and Certification requirements.

## Participant Registration

Ensure that all of the committers and contributors have [registered AllSeen Alliance accounts](https///allseenalliance.org/user/register). ***Important:** Do not use spaces or apostrophes in your AllSeen Alliance usernames. This interferes with gerrit use.*

This establishes that they have agreed to the terms and conditions for contributing to the AllSeen Alliance. Logging in is required for anything more than read-only access to the wiki, code repositories, Jira, and other AllSeen Alliance sites.

Before requesting that individuals get specific gerrit or Jira permissions, have them log in to both [gerrit](https///git.allseenalliance.org/gerrit/) and [Jira](https///jira.allseenalliance.org/).

## Wiki Page

Create/edit a Wiki page to include an adequate overview of project, including how someone outside the project can engage/participate in the project.

Any registered Alliance user can edit existing wiki pages if they are logged in to the wiki. The login link is in the upper right corner of each wiki page. To request page creation and media upload access, please email [bpreston@linuxfoundation.org](bpreston@linuxfoundation.org)
 

*  Working Group Example: https://wiki.allseenalliance.org/tsc/connected_lighting

*  Project Example: https://wiki.allseenalliance.org/core/security_enhancements

## Infrastructure Setup

Important services need to be configured for each project:


*  Git repository and gerrit code review: https://git.allseenalliance.org/

*  Jira issue tracker: https://jira.allseenalliance.org/

In addition, a [mailing list](https///lists.allseenalliance.org/) may be needed if an existing list does not fit the needs of the project. Some typical mailing list scenarios are:


*  New working group: Always request a mailing list

*  New project in an existing working group: Use the working group mailing list

*  New project without a working group: See if an [existing list](https///lists.allseenalliance.org/) is a good fit for your project. If an existing list does not work or your project will have significant traffic, request a new list.

To request Git/gerrit, Jira, and mailing lists, send email to [allseen-infrastructure@lists.allseenalliance.org](allseen-infrastructure@lists.allseenalliance.org) and include the following information:


*  Proposed git repository name and description
    * The naming convention is "`<project>`.git". Keep it reasonably short.
      * Workgroup names are no longer included in the naming convention since a project may be associated with different workgroups (or no workgroup) over time.
    * Look at the [project list](https///git.allseenalliance.org/gerrit/#/admin/projects/) for examples.
    * Make sure all of the committers and maintainers have logged in to https://git.allseenalliance.org/gerrit so their user IDs will be ready to have permissions assigned.

*  Jira project, if needed
    * New projects typically start out using the (TBD) Jira name.
    * Additional Jira projects are named starting with ASA (for "__A__ll__S__een __A__lliance") with a suffix of 4-5 letters or less. Examples: ASACORE, ASALIGHT, ASADT.

*  Mailing list name, if needed
    * Lists have addresses like "allseen-LISTNAME@lists.allseenalliance.org".
    * Refer to the [existing lists](https///lists.allseenalliance.org/) for example names.

It's best to aim for some consistency between them. The core working group has git projects starting with ["core/"](https///git.allseenalliance.org/cgit/core/), a Jira project named [ASACORE](https///jira.allseenalliance.org/browse/ASACORE), and a mailing list called [allseen-core@lists.allseenalliance.org](allseen-core@lists.allseenalliance.org).
If you are not sure which names will work well for your project, the [infrastructure team](allseen-infrastructure@lists.allseenalliance.org) will help you work out names that fit the conventions.
## Conference Call Setup

To set up a WebEx dial-in, enabling weekly/bi-weekly calls, please email [bpreston@linuxfoundation.org](bpreston@linuxfoundation.org)

## Project Overview

Submit project overview, with information provided specific to the open source elements, for inclusion on [Working Group overview page](https///allseenalliance.org/about/working-groups) to [bpreston@linuxfoundation.org](bpreston@linuxfoundation.org)


*  {{:tsc:allseenalliance_name_of_service_date.pptx|Overview Template}}

## Project Release

The expectation is that once a project is approved the team will be working towards a release.  When a software release is ready the TSC must approve it (this is particularly true for projects that are part of the [Base Implementation](https///allseenalliance.org/compliance)). To seek approval a project member must get on the agenda of a TSC meeting using the template below to present all the relevant information.


*  {{:tsc:release_approval_template.pptx|Release Approval template}}
## Compliance and Certification Requirements

####  Document Process for WGs creating Service Frameworks 

The TSC formally approved (April 8, 2014) the following document process for all working groups. This process puts certain requirements on all WGs to provide support for compliance and certification. The Committer or Contributor of Core (About...) and each Service Framework (Config, Control Panel, Notifications, Onboarding, Lighting, etc...) MUST Provide to C&CWG:


*  The source code of the new (or updates) of Core and Service Frameworks 

*  Interface Definitions associated with the Core Interfaces or Service Framework Interfaces

*  Test Case Specs which are written against the Interface Definition of the Service Framework

*  Provide Test Code implementing the Test Case Specs 

*  Please send documents to the [Compliance and Certification (Technical) mail list](allseen-cc@lists.allseenalliance.org).

*  Allow 2 weeks lead time for C&CWG to approve documents 

*  Documents MUST be approved by C&CWG BEFORE a product can be certified with that service framework
 
## Templates


*  {{:compliance:alljoyn_xxxx_service_framework_interface_specification_template_oct2014.docx|Service FrameWork Interface Definition Template}}

*  {{:compliance:alljoyn_service_framework_test_case_specificaton_template_march2015.docx|Service Framework Test Case Specification Template}}

*  {{:compliance:ccwg_reviewtemplate.xls|Review Docs Template}}

*  {{:compliance:how_to_write_allseen_alliance_self_cert_test_cases.pdf|How to Write AllSeen Alliance Self-Certification Test Cases}}

## Contributing Code

One your project is set up, refer to the [Contributing Source Code](develop/contributing_source_code) documentation that covers basic gerrit usage and has pointers to other git and gerrit guides.

