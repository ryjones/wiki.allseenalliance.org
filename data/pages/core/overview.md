# Core Working Group


The Core Working Group develops the AllJoyn client and routing node software that other services build upon.

Marcello Lioy is the Core Working Group chair.

Check the [Core Project Committers](tsc/committers#core) list for other project participants.
## Projects


*  **alljoyn**: Standard Core and router
    * Repository
      * Clone: `<nowiki>`git clone https://git.allseenalliance.org/gerrit/core/alljoyn`</nowiki>`
      * [ Browse](https///git.allseenalliance.org/cgit/core/alljoyn.git/)
    * Maintainer: Marcello Lioy

*  ** ajtcl **: Thin Core
    * Repository
      * Clone: `<nowiki>`git clone https://git.allseenalliance.org/gerrit/core/ajtcl`</nowiki>`
      * [Browse](https///git.allseenalliance.org/cgit/core/ajtcl.git/)
    * Maintainer: Marcello Lioy

*  ** [alljoyn-js](alljoyn-js/overview) **: Thin client Javascript
    * Repository
      * Clone: `<nowiki>`git clone https://git.allseenalliance.org/gerrit/core/alljoyn-js`</nowiki>`
      * [Browse](https///git.allseenalliance.org/cgit/core/alljoyn-js.git/)
    * Maintainer: Josh Spain

*  ** openwrt_feed **: OpenWRT feed repository for AllSeen code
    * Repository
      * Clone: `<nowiki>`git clone https://git.allseenalliance.org/gerrit/core/openwrt_feed`</nowiki>`
      * [Browse](https///git.allseenalliance.org/cgit/core/openwrt_feed.git/)
    * Maintainer: Josh Spain
    * Feed includes both core and base service packages

[Archived projects](Archived projects)
## Resources


*  Mailing List: `<allseen-core@lists.allseenalliance.org>` ([Subscribe](https///lists.allseenalliance.org/mailman/listinfo/allseen-core))

*  Issue Tracker: [ASACORE Jira project](https///jira.allseenalliance.org/browse/ASACORE)

*  [Build Automation](Build Automation)

*  [NPAPI JavaScript Binding Development Guide (Binding for browsers or WebKit)](JavaScript Binding Development Guide)

## Process

*  [Core WG process](core/overview/wg_process)

*  [Core WG JIRA process](core/overview/jira_process)

*  [Core WG Platform Support process](core/overview/platform_process)

## Release Planning

Part of the release planning is the [weekly triage meetings](overview#Weekly Core Triage Meetings). Release details are below. Release details [are here](release/overview).


*  **v16.10**
    * [16.10 Release Plan](core/core_16.10_release_plan)
    * [Release Review 16.10](core/core_16.10_release_review)

*  **v16.04**
    * [16.04 Release Plan](core/core_16.04_release_plan)
    * [Release Review 16.04](core/core_16.04_release_review)
 
 [Archived release information](core/releases_archive)
## Features


*  [About Feature Rework](About Feature Rework)

*  [Bluetooth Transport](Bluetooth Transport)

*  [Security Enhancements](Security Enhancements) ([ASACORE-1393](https///jira.allseenalliance.org/browse/ASACORE-1393))

*  [Reduction of name traffic in the system](https///jira.allseenalliance.org/browse/ASACORE-1392) (ASACORE-1392)

*  [Move essential DDAPI functionality to Alljoyn core](https///jira.allseenalliance.org/browse/ASACORE-1383) (ASACORE-1383)

*  [Router Selection Algorithm Definition and Mechanism](https///jira.allseenalliance.org/browse/ASACORE-803) (ASACORE-803)

## Technical Proposals


*  [Support creation of dynamic interfaces in AllJoyn Java Binding](/core//overview#technical_meeting_minutes) ([ASACORE-3109](https///jira.allseenalliance.org/browse/))

*  {{:core::asacore-2946_specs_v3.pdf|Design change proposal for resolving}} [ASACORE-2946](https///jira.allseenalliance.org/browse/ASACORE-2946)

*  {{:core:ota_firmware_update_hld.pdf|OTA Firmware Update HLD}}
*  {{:core:alljoyn-ec-speke-draft-1.pdf|EC-SPEKE Authentication Mechanism (draft-1)}} {{:core:alljoyn-ec-speke-draft-2.pdf|(draft-2)}} 

*  {{:core:alljoyn_router_selection_for_tcl_design-3-4-15.pdf|Router Selection Proposal For TCL}}

*  ARDP (UDP transport) {{:core:udp_transport_and_router_requirements.pdf|reqiurements}} and {{:core:udp_transport_and_router_architecture.pdf|design document}}

*  [Name Transfer Changes Proposal](https///jira.allseenalliance.org/secure/attachment/11200/Name%20Transfer%20Changes%20Proposal%201-19-15.pdf)

*  [core:OpenWRT Feed Proposal](core/OpenWRT Feed Proposal)

*  [AllJoyn.js](alljoyn-js/getting-started)

*  [core:OpenWrt Package Development and Maintenance Process Proposal](core/OpenWrt Package Development and Maintenance Process Proposal)

*  [core:Extensions to the Type System Proposal](core/Extensions to the Type System Proposal)

*  [Simplified API](tsc/technical_steering_committee/proposals/simplifiedapi)
 

## Weekly Working Group Meetings

The AllSeen Alliance Core Working Group holds weekly, half hour status meetings. The purpose is primarily to facilitate coordination among the contributors in the group. It also serves the purpose of increasing common awareness of the ongoing status of the project.

### When

Thursdays at 10am Pacific Time

### How to Attend

**Phone Dial-in ([USA](http://www.howtocallabroad.com/usa/)):** +1-415-655-0002 US TOLL\\
**Meeting ID:** 927 530 390\\
**Meeting Password:** 1234\\
**Meeting [Link](https///openconnectivity.webex.com/openconnectivity/j.php?MTID=m31435362a23889e3e37298804a882cbc):** https://openconnectivity.webex.com/openconnectivity/j.php?MTID=m31435362a23889e3e37298804a882cbc\\

**For callers outside the US:** It is recommended that you use the WebEx Java Plug-In to join the meeting.

For more information about joining a WebEx meeting please visit the [ WebEx FAQ](https///meetings.webex.com/collabs/support/nfaqs?_iframe=/webex/v1.3/support/en_US/faq/faq_meetings_signed_out.htm)

### Meeting Agendas

The agenda for each meeting is decided and published prior to the meeting. Any additions to the agenda must be requested prior to the meeting by emailing the [Core Working Group Mailing List](allseen-core@lists.alljoyn.org).

### How Meetings are Run

To properly hold efficient meetings it is necessary to keep them on topic and moving forward. Each meeting will be in the following format:

 1.  Introductions
    - Who is attending the meeting?
 2.  Status Updates
    - Team Member 1 - gives a quick status update (**< 1 minute**)
      - "I have been working on..."
      - "I plan to complete this work when..."
      - "I need to communicate/work with someone about..."
    - Team Member 2 - gives a quick status update
    - ...
 3.  Agenda Item 1
    - Requested agenda item is discussed for a maximum of **10 minutes**.
    - At 10 minutes the discussion is halted
      - A halted discussion may be discussed further at the end of the meeting if there is time available.
      - If there is not time at the end of the meeting then the discussion will be taken offline (i.e. the persons who are involved in the discussion will communicate by other means, such as via email or a separate phone call). Alternatively, the discussion can be tabled until the next weekly meeting.
 4.  Agenda Item 2
 5.  ...
 6.  Other Business
    - Additional items may be added to the meeting agenda after all official agenda items have been discussed.
    - Each requested item will be discussed for a maximum of **5 minutes** before taking the discussion offline.
 7.  Adjourn

### Meeting Minutes

#### December 2016

*  December 15, 2016 {{:core:ajosp-corewg-12-15-16.pdf|Meeting Slides}}[WebEx Recording](https///oregonstate.webex.com/oregonstate/ldr.php?RCID=8eaf6285ea0628b131881fdd94e74123)★
    * Bulk of the meeting was a [Post Mortem for 16.10](/core/core_16.10_release_review#post-mortem) with the action items captured there
    * ★Special thanks to Carrie for offering her WebEx given issues with the AJOSP instance 

*  December 8, 2016 {{:core:ajosp-corewg-12-08-16.pdf|Meeting Slides}}[WebEx Recording](https///openconnectivity.webex.com/openconnectivity/ldr.php?RCID=1922338b3467759bb6d45f4125cf4a2e)  

*  December 1, 2016 {{:core:ajosp-corewg-12-01-16.pdf|Meeting Slides}}[WebEx Recording](https///openconnectivity.webex.com/openconnectivity/ldr.php?RCID=a8281c6a8b20a52c18ebc5e54a3451d2)

#### November 2016


*  November 17, 2016 {{:core:ajosp-corewg-11-17-16.pdf|Meeting Slides}}[WebEx Recording](https///openconnectivity.webex.com/openconnectivity/ldr.php?RCID=1e51184eaef5cd8e28ac86e54872684b)

*  November 10, 2016 {{:core:ajosp-corewg-11-10-16.pdf|Meeting Slides}}[WebEx Recording](https///openconnectivity.webex.com/openconnectivity/ldr.php?RCID=5cce43b7dc1b9ab76271fa0ec726be33)

*  November 3, 2016 {{:core:ajosp-corewg-11-03-16.pdf|Meeting Slides}}[WebEx Recording](https///openconnectivity.webex.com/openconnectivity/ldr.php?RCID=a78cfda9f38705ebfe7b80b3c94bcfde)

#### October 2016


*  October 27, 2016 {{:core:allseen-corewg-10-27-16.pdf|Meeting Slides}}[WebEx Recording](https///openconnectivity.webex.com/openconnectivity/ldr.php?RCID=61ba26858d67d5fce4000c18339879c8)

*  October 20, 2016 {{:core:allseen-corewg-10-20-16.pdf|Meeting Slides}}[WebEx Recording](https///openconnectivity.webex.com/openconnectivity/ldr.php?RCID=e1a913570727bb7f69a2a5213c19e180)

*  October 13, 2016 {{:core:allseen-corewg-10-13-16.pdf|Meeting Slides}}[WebEx Recording](https///meetings.webex.com/collabs/#/files/detail?fileID=OEPN604DI5I4Q0J8PZEQHVSSMX-HIZ3&containerID=UCJD4O38TYYWNXMWVUZXYISO88-HIZ3&containerType=us)
*  October 6, 2016 {{:core:allseen-corewg-10-06-16.pdf|Meeting Slides}}[WebEx Recording](https///meetings.webex.com/collabs/#/files/detail?fileID=OEPN604DI5I4Q0J8PZEQHVSSMX-HIZ3&containerID=UCJD4O38TYYWNXMWVUZXYISO88-HIZ3&containerType=us)

#### September 2016


*  September 29, 2016 {{:core:allseen-corewg-09-29-16.pdf|Meeting Slides}}[WebEx Recording](https///meetings.webex.com/collabs/#/files/detail?fileID=O6A0I5A5OH2ZCP9VO58GVO921C-HIZ3&containerID=UCJD4O38TYYWNXMWVUZXYISO88-HIZ3&containerType=us)

*  September 22, 2016 {{:core:allseen-corewg-09-22-16.pdf|Meeting Slides}}[WebEx Recording](https///meetings.webex.com/collabs/#/files/detail?fileID=O1QKWIIXI90B6IC1VQA6PH2L15-HIZ3&containerID=UCJD4O38TYYWNXMWVUZXYISO88-HIZ3&containerType=us)

*  September 15, 2016 {{:core:allseen-corewg-09-15-16.pdf|Meeting Slides}}[WebEx Recording](https///meetings.webex.com/collabs/#/files/detail?fileID=O08P1LXGTRYXGMVVTINT9F0LYD-HIZ3&containerID=UCJD4O38TYYWNXMWVUZXYISO88-HIZ3&containerType=us)

*  September 08, 2016 {{:core:allseen-corewg-09-08-16.pdf|Meeting Slides}}[WebEx Recording](https///meetings.webex.com/collabs/#/files/detail?fileID=O08P1LXGTRYXGMVVTINT9F0LYD-HIZ3&containerID=UCJD4O38TYYWNXMWVUZXYISO88-HIZ3&containerType=us)

*  September 01, 2016 {{:core:allseen-corewg-09-01-16.pdf|Meeting Slides}}[WebEx Recording](https///meetings.webex.com/collabs/#/files/detail?fileID=O83VFSMJOWJ94L3DWRNP7OE2H3-HIZ3&containerID=UCJD4O38TYYWNXMWVUZXYISO88-HIZ3&containerType=us)

[Meeting minute archives](core/wg meeting archive)
## Weekly Triage Meetings

The Working Group holds weekly, one hour triage meetings. The purpose of these meetings is to review [JIRA](https///jira.allseenalliance.org/browse/ASACORE) with a focus on the next Core release.  Approximately 2 weeks before code/development complete (which is also when the release branch is cut) the frequency of these meetings will double to ensure we can triage bugs related to the release in a timely manner.

### When

Thursdays at 10:30am Pacific Time.
During a release cycle, the additional triage is held on Monday's at 10am Pacific Time

### How to Attend

**Phone Dial-in ([USA](http://www.howtocallabroad.com/usa/)):** +1-415-655-0001 US TOLL\\
**Meeting ID:** 197 373 328\\
**Meeting [Link](https///meetings.webex.com/collabs/#/meetings/detail?uuid=M5E8GLNFVL5VWV6C59JCF1634I-HIZ3&rnd=514577.49514):** https://meetings.webex.com/collabs/#/meetings/detail?uuid=M5E8GLNFVL5VWV6C59JCF1634I-HIZ3&rnd=514577.49514\\

**For callers outside the US:** It is recommended that you use the WebEx Java Plug-In to join the meeting.

For more information about joining a WebEx meeting please visit the [ WebEx FAQ](https///meetings.webex.com/collabs/support/nfaqs?_iframe=/webex/v1.3/support/en_US/faq/faq_meetings_signed_out.htm)


## Ad-hoc Technical Meetings

Technical meetings will be called when a discussion or proposal is not converging on the Core WG [mailing list](https///lists.allseenalliance.org/mailman/listinfo/allseen-core).  These meetings are ad-hoc and invitations with meeting details are sent to the mailing list.

### Technical Meeting Minutes

*  September 13, 2016: IPv6 Test Planning for 16.10 {{:core:ipv6_testing_meeting_notes_091316.docx|Meeting Notes}} [WebEx  recording](https///oregonstate.webex.com/oregonstate/ldr.php?RCID=f48adfae779ff56fdaf9d33cf5ac9364)

*  August 2, 2015 Technical Meeting: Discuss addition of [Dynamic Interface support in Java](https///jira.allseenalliance.org/browse/ASACORE-3109)  [Webex recording](https///meetings.webex.com/collabs/#/files/detail?fileID=O3SUVI4KHXRA8GZT3SY21C4LZY-HIZ3&containerID=UCJD4O38TYYWNXMWVUZXYISO88-HIZ3&containerType=us)
   * June 9, 2016 Technical Meeting: Discuss/define C&C test cases for Security 2.0 [Webex recording](https///meetings.webex.com/collabs/#/files/detail?fileID=O62QCYXYYV3FRQSJP2KHELJZBX-HIZ3&containerID=UCJD4O38TYYWNXMWVUZXYISO88-HIZ3&containerType=us)
   * February 23, 2016 Technical Meeting: discussion around issues and solutions to the Security 2.0 manifests [WebEx Recording](https///meetings.webex.com/collabs/#/files/detail?fileID=OEKGYLJ261KVL8S7P2CW6H9HTZ-HIZ3&containerID=UCJD4O38TYYWNXMWVUZXYISO88-HIZ3&containerType=us)
   * July 15, 2015 Technical Meeting: Dynamic Runtime Translation Discussion [WebEx Recording](https///meetings.webex.com/collabs/url/0YOCTHuS6dCyFzJnxKxNXPRVBuSIUPX40y3Msy3NVqi00000)

*  January 28, 2015 Core technical discussion regarding observer in Core (ASACORE-1383) [WebEx Recording](https///meetings.webex.com/collabs/url/hQ5nCC1UuD5o8v2OeklDwf55j-io9iIIU1hjm2_juGq00000)

*  January 20, 2015 BTLE Technical Discussion [WebEx Recording](https///meetings.webex.com/collabs/url/5GH-KnQJzjaJPIz9g9-1ZhTBo4Ro8KInUTGvOuQWohC00000)

*  January 12, 2015 Review router ranking proposal for TCL connectivity continued discussion {{:core:router_ranking_discussion_1-12-15.pdf|Meeting Notes}} [WebEx Recording](https///meetings.webex.com/collabs/url/J82oKryufDQZmP38ZMDj6YCWDDK2rtXxPc0YekLKIWW00000)

*  January 12, 2015 Discuss testing at the alliance {{:core:core_wg_testing_discussion_1-12-15.pdf|Meeting Notes}} [WebEx Recording](https///meetings.webex.com/collabs/url/PuiWtQWS_TSYx_sx7RVtlrH5VR7RNRrKfzaqW0TjhPy00000)

*  January 8, 2015 Review router ranking proposal for TCL connectivity continued discussion [WebEx Recording](https///meetings.webex.com/collabs/url/9lbTwwopFyKBmlIfXH0xuoU1sztAPk1eeOGlu1sKTPW00000)

*  December 2, 2014 Review router ranking proposal for TCL connectivity {{:core:core_wg_technical_meeting_-_qce_alljoyn_router_selection_for_tcl_proposal_-_dec_2_2014_updated.pdf|Meeting Slides}} [WebEx Recording](https///meetings.webex.com/collabs/url/gOdDop5mDJBmgQAzGk0FAMmu8ymya78EUZVqwWrulYm00000)

*  November 12, 2014 Allseen Summit Core WG Breakout Session {{:core:core_working_group_breakout-11-12-14.pdf|Meeting Slides}} {{:core:core_working_group_breakout_notes_a_11-12-14.pdf|Meeting Notes}} 

*  November 06, 2014 Interface Versioning II {{:core:allseen-corewg-tech-discussion-11-06-14.pdf|Meeting Slides}} [WebEx Recording](https///meetings.webex.com/collabs/url/Yr9m19MG5S1nlbJerU9brj2i3CosAoxz2eoNvbO-ZFG00000)

*  October 30, 2014 Interface Versioning, Session Ports, Auto-pinger {{:core:allseen-corewg-tech-discussion-10-30-14.pdf|Meeting Slides}} [WebEx Recording](https///meetings.webex.com/collabs/url/11JDm-zFanNSxDFyNkmlK0D92XNhm2oJyS0wLOOss2W00000)


