# Security 2.0

The Security 2.0 feature is an enhancement to the existing AllJoyn Security.

The goal of the Security 2.0 feature is to allow an application to validate access to  secure interfaces or secure objects based on policies installed by the owner.  This feature is part of the AllJoyn Core library.  It is not an option for the application to enforce permission.  It is up to the user to dictate how the application performs based on the access control lists (ACLs) defined for the application.  The AllJoyn Core Permission Management component does all the enforcement including the concept of mutual authorization before any message action can be taken. 

The Security Manager is an optional service that helps the user with key management and permission rules building.  Using policy templates defined by application developer, the Security Manager builds the application manifest to let the user authorize which interactions the application can do.

Phil Nguyen `<philn@qce.qualcomm.com>` is the primary design document maintainer.

## Security Manager Release Planning

*  v15.09
    * [15.09 Release Plan](core/security_manager_15.09_release_plan)
    * [Release Review 15.09](core/security_manager_15.09_release_review)

# Weekly Meetings

The Security 2 project of the AllSeen Alliance Core Working Group held weekly calls to discuss status, technical details and triage during the development phase of the feature.  The weekly meetings were suspended in Nov 2015 as the team felt a meeting dedicated to the topic is no longer needed.  

To request a topic be added to the agenda for an upcoming call, send an e-mail to the core working group mail list. 

Ad hoc technical discussions will be scheduled as needed if the topic cannot be covered in a regularly scheduled core working group call.  Monitor the core working group mail list for announcements.



## Documents

### Schedule Documents

   * {{:core:core_security_feature_status_1-27-15.pdf| Core Security 2.0 Interface Status for 1-27-15}}
   * {{:core:security2.0combinedschedule-02-4-15.pdf| Combined Milestone Schedule as of 2-04-15}}
### Feature Matrix

   * {{:core:core_security_feature_status_v19.pdf| Feature Matrix as of 2-03-15}}
   * {{:core:core_security_feature_status_v23.pdf| First release feature Matrix as of 3-3-15}}
### High Level Design Documents

   * [Click here to view the HLD](https///allseenalliance.org/framework/documentation/learn/core/security2_0/hld )
     * Note: Revision 1 update 6 is locked for the Security 2.0 release as part of the Core 15.08 release tracked in [JIRA linked here.](https///jira.allseenalliance.org/browse/ASACORE-1393)
   * Use the following process to add comments and/or making changes to the HLD 
     * Submit comments/questions to the Core WG mail list with the subject prefix [Security 2.0]
     * Once there is resolution make the proposed changes to the HLD following the alliance webdocs process
     * Additional comments are captured through the gerrit approval process
     * Note: Once a proposed change is approved, a request must be sent to the documentation mail list (allseen-tech-documentation-website@lists.allseenalliance.org) to have the web site updated.
   * To make updates, follow the alliance documentation process detailed [here](https///wiki.allseenalliance.org/tsc/technical_documentation/webdocs)
     * View the source documentation using [this link](https///git.allseenalliance.org/cgit/extras/webdocs.git/tree/docs/learn/core/security2_0?h=refs/heads/feature/security2.0) 
     * Use git to access the documentation [via gerrit](https///git.allseenalliance.org/gerrit/#/admin/projects/extras/webdocs) (one time action)
     * To view and edit the documentation use the following commands.
       * Sign in using your AllSeen Aliance credentials
       * Select `clone with commit-msg hook`
       * Select `HTTP`
       * Use the provided git clone command to download the webdocs project
#### Archived versions

*  [HLD Open Questions/Action Items](core/security_enhancements/hldreview)

*  Draft Version
    * {{:core:alljoyn_security_2.0_hld_rev1.6-draft17.docx|Draft 17 Security 2.0 HLD version 1.6}}
    * [Application Manifest Proposal](core/security_manifest)

* Latest versions
    * {{:core:alljoyn_security_2.0_hld_rev1.5.docx| Security 2.0 HLD version 1.5}}
    * {{:core:alljoyn_security_2.0_hld_rev1.5.pdf| Security 2.0 HLD version 1.5}}

* Older versions
    * {{:core:alljoyn_security_2.0_hld_rev1.4.docx| Security 2.0 HLD version 1.4}}
    * {{:core:alljoyn_security_2.0_hld_rev1.4.pdf| Security 2.0 HLD version 1.4 }}
    * {{:core:alljoyn_security_2.0_hld_rev1.3.docx| Security 2.0 HLD version 1.3}}
    * {{:core:alljoyn_security_2.0_hld_rev1.3.pdf| Security 2.0 HLD version 1.3}}
    * {{:core:alljoyn_security_2.0_hld_rev1.2.docx| Security 2.0 HLD version 1.2}}
    * {{:core:alljoyn_security_2.0_hld_rev1.2.pdf| Security 2.0 HLD version 1.2}}
    * {{:core:alljoyn_security_2.0_hld_rev1.1.docx| Security 2.0 HLD version 1.1}}
    * {{:core:alljoyn_security_2.0_hld_rev1.1.pdf| Security 2.0 HLD version 1.1}}
    * {{:core:alljoyn_security_2.0_hld_rev1.0.docx| Security 2.0 HLD version 1.0}}
    * {{:core:alljoyn_security_2.0_hld_rev1.0.pdf| Security 2.0 HLD version 1.0}}
### Newly Proposed Interface Descriptions For IRB Review

*  [Security 2.0 IRB Review](https///git.allseenalliance.org/gerrit/#/c/4283/)
#### Outdated Interface Descriptions


*  [Security Interface Descriptions](Security Interface Descriptions) 
### Security Manager Documentation

   * [Security Manager Description](Security Manager Description)
   * {{:core:security_manager_sample_application_in_windows_design_document.pdf| Windows Security Manager Sample Application Design DRAFT}}
### Test Documents

   * {{:core:aj_core_security2_test_plan-v4.xlsx| Core Security 2.0 Test Plan APPROVED Updated 7/07/15}}
   * {{:core:aj_core_security2_test_plan_-_v1.xlsx| Core Security 2.0 Test Plan DRAFT Updated 6/22/15}}
     * [Test case review meeting recording 1/2](https///meetings.webex.com/collabs/url/mcRbo9KtIkZX_4_vyq-gt-ddAR1fZjZqpRGhvlFyY8i00000)
     * [Test case review meeting recording 2/2](https///meetings.webex.com/collabs/url/vNRE9ur20JMe6QrEqIv64MukTGMHIu_8BITiWTUxs5O00000)
   * {{:core:alljoyn_sec2_0_test_plan_v3.pdf| Core Security 2.0 Test Plan DRAFT Updated 2/13/15}}
###  Technical Meeting Minutes

*  Technical Discussion Notes for Nov 9, 2015 regarding concerns of fine grained interfaces potential to cause large manifests
    * [WebEx Recording](https///meetings.webex.com/collabs/url/GFcmSDcIIl0ZQKAiDVXfetB2xPeSA5rxSlhTeQoAkFO00000)
    * {{:core:AllSeen-CoreWG-Security2-11-09-15.pdf|Meeting Notes}} 

*  Technical Discussion Notes for June 18, 2015 regarding [ASACORE-2067](https///jira.allseenalliance.org/browse/ASACORE-2067) and Delegation
    * [WebEx Recording](https///meetings.webex.com/collabs/url/l1u31865C8MsS_mYrFknxMYitdi0lF_jmiWAGcqRNG400000)

*  Technical Discussion Notes for May 05, 2015 
    * [WebEx Recording](https///meetings.webex.com/collabs/url/OmAU9yVN-vIX1uG-z-F9yNLH-9jDq2aEVU8Eul5sCoa00000)
    * {{:core:security_2_meeting_notes_5-5-15.pdf|Meeting Notes}} 

*  Technical Discussion Notes for April 21, 2015 
    * [WebEx Recording](https///meetings.webex.com/collabs/url/-PSiPWbITFID4xx_sg7-nGokXY26sqN7kw5zfy7OSwG00000)

*  Technical Discussion Notes for April 7, 2015 HLD Review #2 discussion
    * [WebEx Recording](https///meetings.webex.com/collabs/url/irxspreLxBm-avOJPoxAPQq3ikRGFW5fBxdMBfxlQYa00000)

*  Technical Discussion Notes for March 19, 2015 HLD Review #2 discussion
    * {{:core:meeting_notes_for_hld_review_held_on_3-3_3-6_and_3-19.pdf|Meeting Notes}} 
    * [WebEx Recording](https///meetings.webex.com/collabs/url/cI-D8y9nx-krKAUG3UMrknNrb83Rbuhcqu9dKd9w3nm00000)

*  Technical Discussion Notes for March 13, 2015 Follow up from mail thread discussions
    * {{:core:security2technicaldiscussion3-13-15.pdf|Meeting Notes}} 
    * [WebEx Recording](https///meetings.webex.com/collabs/url/6_OC7AE_X6fIO-aiG4OKM6SbwdyuXC-JVgUE6ApDXnq00000)

*  Technical Discussion Notes for March 10, 2015
    * [WebEx Recording](https///meetings.webex.com/collabs/url/1-kjToKHAWkaeTh9sWY9t8a448KUp4tVUzs_Ch-ULTC00000)

*  Technical Discussion Notes for March 06, 2015 HLD Review part 2
    * {{:core:meeting_notes_for_hld_review_held_on_3-3_and_3-6.pdf|Meeting Notes}} 
    * [WebEx Recording](https///meetings.webex.com/collabs/url/FHeABKYj57sE27ifFF8XDTrrANUzFNEwvcYtPg0JR9e00000)

*  Technical Discussion Notes for February 24, 2015
    * {{:core:core_security_2_pending_features_for_2-26-15.pdf|Meeting Notes}} 
    * {{:core:core_security_2_pending_features_-_2-26-15.pdf|Pending Features}} 
    * [WebEx Recording](https///meetings.webex.com/collabs/url/BxlRHf-E3KZ2td4hOXU112geJiaYfRJiq5wgCsSNXji00000)

*  Technical Discussion Notes for February 10, 2015
    * [WebEx Recording](https///meetings.webex.com/collabs/url/HEhjmqY0Ue06kRQeZISphntoIlUdGr9nEVbKt4RB6ve00000)

*  Technical Discussion Notes for January 27, 2015
    * {{:core:core_security_feature_status_1-27-15.pdf|Meeting Notes}} [WebEx Recording](https///meetings.webex.com/collabs/url/8PDGxlBs70oWYWMfxSraccBpxBkcA7G-r00MLyyGlVu00000)

*  January 13, 2015 Security 2.0 Root Of Trust - Technical Discussion [WebEx Recording](https///meetings.webex.com/collabs/url/90lSwhz7kiRemr_TeXaB31eWk8DPPKZnJxWywQvkwyG00000)

*  Technical Discussion Notes for October 2, 2014
    * {{:core:technicolor_security_review_meeting_10-2-14.pdf|Meeting Minutes}}{{:core:technicolor_analysis_-_alljoynsecurityanalysisforallseen.pdf |Tecnicolor Analysis Report}}       

*  Technical Discussion Notes for September 23, 2014
    * {{:core:certificatelayoutallseen.pdf|Meeting Minutes}}       

*  Technical Discussion Notes for September 3, 2014
    * {{:core:core_security_technical_meeting_notes_9-3-14.pdf|Meeting Minutes}} [WebEx Recording](https///meetings.webex.com/collabs/url/z08kP8iCXImxEcKFkheJbvKVkSIUdq019pObhJ2jzu800000)

* Collaboration Meeting Notes for August 12-14, 2014 
    * {{:core:security_collaboration_meeting_aug12-13-14-2014.pdf| Meeting Minutes}}   {{:core:security_collaboration_meeting_aug12-13-14-2014.docx| Meeting Minutes MS Word}}
### Status Meeting Minutes

*  November 02, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/mMHzsJnjNAENa0g5Rwweq9al0WdkYYkVC3iCj8emseS00000)  {{:core:allseen-corewg-security2-11-02-15.pdf|Meeting Slides}}

*  October 12, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/WSo0xlqD0Yy7zsWfIzWPy1etc6PpivFhoa-mXL1AqFu00000)  {{:core:allseen-corewg-security2-10-12-15.pdf|Meeting Slides}}

*  October 05, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/U6avLd0jOCSEzCUhBSM3ntuoT1DahMfjrk1XxWGnGXS00000)  

*  September 28, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/oCswcZbVlpcltfOizTIgXjgylSzkVO8K3MwY9Fn3BYm00000)  {{:core:allseen-corewg-security2-9-28-15.pdf|Meeting Slides}}

*  September 21, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/fXsM5DYgiNGg4dTF2WM1bf3VdApZB2cVO5RkwvfrCJa00000)  {{:core:allseen-corewg-security2-9-21-15.pdf|Meeting Slides}}

*  September 15, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/4NwGu4DGxG4a--dpV7lG7sTxp767-dls8NNUulGhhVG00000)  {{:core:allseen-corewg-security2-9-15-15.pptx|Meeting Slides}}

*  September 08, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/QiHXZO9f4FPc8VWAUnW_ACG9heONqSLNJLxbQEMgxnS00000)  {{:core:allseen-corewg-security2-9-8-15.pdf|Meeting Slides}}
   * August 31, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/K7b6l0XdAv-K5_rBNM0ijatAFHwgkXeRrYMDDW_CHFq00000)  {{:core:allseen-corewg-security2-aug-31-15.pdf|Meeting Slides}} 

*  August 24, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/HELohpmIyQx1YuitH_EQCCkN33ZtzYEZlh_5Ah4W9Nm00000) 

*  August 17, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/rElKYgFTXiMFAiqOOkUD7dEeKrRLe8uSUmR-wFIpCfq00000)  {{:core:allseen-corewg-security2-aug-17-15.pdf|Meeting Slides}} 

*  August 10, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/fZ5iIuLbmg0E_5RWltuSeoGcoum7GE1KeUTv1CPgFDO00000)  {{:core:allseen-corewg-security2-aug-10-15.pdf|Meeting Slides}} 

*  August 03, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/iP7tU1VBdPayIExsbyGGICc8ojWYCE1KlSfUlurmxYS00000)  {{:core:allseen-corewg-security2-aug-03-15.pdf|Meeting Slides}} 

*  July 27, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/kx3zznlb7NxEkyBS_wMsoupCR4HG6KbRFUsJdMc6xDG00000)  {{:core:allseen-corewg-security2-july-27-15.pdf|Meeting Slides}} 

*  July 20, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/7qdmlXxF6d9bbAmyBdJ6rJ_4m1VrjXS0m2XZyNX3swK00000)  {{:core:allseen-corewg-security2-july-20-15.pdf|Meeting Slides}} 

*  July 13, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/fhFf4a-S2jGCyzLVuuG8F3CBjWIL6pbtGCmoiSLet4C00000)  {{:core:allseen-corewg-security2-july-13-15.pdf|Meeting Slides}} 

*  July 07, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/Jg-ksrkS7a3N6tgHXkzn7-UXXv696JFCv_yMFmgrPvG00000)  {{:core:allseen-corewg-security2-july-07-15.pdf|Meeting Slides}} 

*  June 29, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/_AB9B3XLZ-WpvOBsm9psMoeBaYKwhIuw-fozO4p6OJS00000)  {{:core:allseen-corewg-security2-june-29-15.pdf|Meeting Slides}} 

*  June 22, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/yso5x-4O09m9ypDpGRC4WxrQx2HySBEaTpFqwA8y_v000000)  {{:core:allseen-corewg-security2-june-22-15.pdf|Meeting Slides}} 

*  June 15, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/3FWzi5uucEkGdXcwiAbLwMQfjQUy0fatOpx-I_AFyiG00000)  {{:core:allseen-corewg-security2-june-15-15.pdf|Meeting Slides}} 

*  June 08, 2015  [WebEx Recording](https///meetings.webex.com/collabs/url/yx4L_knqCqeZZM_7fKkbV3CkD6896fgvGGsnbJ2672S00000)

*  June 01, 2015  [WebEx Recording](https///meetings.webex.com/collabs/url/2IjM1Ipgqs_iV2cm3vD_xEyK1uAxsB8bS6cQdzes5ja00000)

*  May 11, 2015  [WebEx Recording](https///meetings.webex.com/collabs/url/Edfp9HhNPQa57Sm-1yK27ODa11Tf6rUShnZ3BzFFgmq00000){{:core:alljoyn_sec2_meetingnotes_20150511.pdf|Meeting Notes}}

*  April 28, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/9a_X-XR4KPptDjHxV_mkNGTmEH4_5nHp0X5kqpa7iKq00000)  {{:core:hld_and_irb_security_review_4-28-15-2.pdf|Meeting Notes}} 

*  April 14, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/A0QpitcTj_blFUqsrzuwmkCDM8QaFVWPdAJcPwu32Be00000)

*  March 31, 2015 {{:core:core_security_feature_status_v25.pdf|Meeting Notes}} [WebEx Recording](https///meetings.webex.com/collabs/url/Q_rAg6wwgviGs7xZ61vvLjoAK7PHRIHCdozvPbETD0e00000)

*  March 17, 2015 [[https://meetings.webex.com/collabs/url/1T1A1bbrR3jxlQ7qkmXPPcvx-pNtNrDNG_Or-3pr66000000
 | WebEx Recording]]
 | -----------------

*  March 03, 2015 -Includes HLD review part 1- [WebEx Recording](https///meetings.webex.com/collabs/url/EFt-NCcDNzn5E0OFE_4CUXcuQmjeNFSk4f5SasPmd_u00000)

*  February 17, 2015 {{:core:security_2_0_qeo_llc_planning_inputs_with_meeting_notes_for_2-17-15.pptx|Meeting Notes}} [WebEx Recording](https///meetings.webex.com/collabs/url/nhyFP3LNDmu6_XKZS_Q-IJTK7KYqMq5KcPVdt4jSsE000000)

*  February 03, 2015 {{:core:core_security_feature_status_v19.pdf|Meeting Notes}} [WebEx Recording](https///meetings.webex.com/collabs/url/XMc0-ru79ycyHXxZaWP5u2k56A13VDSgAYs1c6lJkCi00000)

*  January 20, 2015 {{:core:core_security_feature_status_date_1-20-15_v4.pdf|Meeting Notes}} [WebEx Recording](https///meetings.webex.com/collabs/url/WwbMXvF1cRl7M3x3-YJyxEXXUJ4DJPIotdHezCwDNYi00000)

*  January 06, 2015 [WebEx Recording](https///meetings.webex.com/collabs/url/-a4sl28csmEeQTJ1NzB5Mt3o2XEwwJ7zmE0MZWWykPS00000)

*  December 09, 2014 [WebEx Recording](https///meetings.webex.com/collabs/url/fUNu9P9EhIuJWz1U-ZTcVnMgAevvPJHcIXUW0gC8lz400000)

*  November 25, 2014 [WebEx Recording](https///meetings.webex.com/collabs/url/kN2ooMn30ymJM0CZ11mLWFTS6zXWWVi8k_dmbAucWIm00000)

*  October 28, 2014 [WebEx Recording](https///meetings.webex.com/collabs/url/rsV8zMWNZ4nLjEQ0houJwTsA4t2-dJDaVuolBwMZSgC00000)

*  October 14, 2014 {{:core:allseen-security-10-14-14.pdf|Meeting Slides/Notes}} [WebEx Recording](https///meetings.webex.com/collabs/url/v8oJZTe_PT_rtY3zd704LEx_On_vEvu-T5XaSZ64TBe00000)

*  September 30, 2014 {{:core:core_security_technical_meeting_notes_9-30-14.pdf|Meeting Minutes}} [WebEx Recording](https///meetings.webex.com/collabs/url/3g7MpHgLXgVp7rqybzofgHg7mMIA5bVn6hOQWLtQaOS00000)

*  September 16, 2014 {{:core:core_security_technical_meeting_notes_9-16-14.pdf|Meeting Minutes}} [WebEx Recording](https///meetings.webex.com/collabs/url/-0gSpDB8SFJ07vf-49EUWRDjivJlc0qLx10S4JD2d9e00000)

*  September 09, 2014 {{:core:core_security_technical_meeting_notes_9-9-14.pdf|Meeting Minutes}} [WebEx Recording](https///meetings.webex.com/collabs/url/BWTAAj2SrDj25Ds8CW2qL2731yvqa2pXpwSmlCa-FUu00000)

*  September 02, 2014 {{:core:core_security_weekly_status_meeting_notes_9-2-14.pdf|Meeting Minutes}} [WebEx Recording](https///meetings.webex.com/collabs/url/5H3Umjg9Z5SUVu_qtP_3Ey8krDad04lJZwW8RJyzW3K00000)

*  August 26, 2014 {{:core:core_security_weekly_status_meeting_notes_8-26-14.pdf|Meeting Minutes}} [WebEx Recording](https///meetings.webex.com/collabs/url/EVrXvna1xEnxg7lW2Je72jojfG78OIV5GaiODLhWrdq00000)







 
