# About Feature Rework

The AboutService was originally developed as a separate service from the core functionality of AllJoyn.  Now the AboutService is a core requirement for AllJoyn.  This branch will be used to move the functionality found in the AboutService into the alljoyn_core code base.

See the [Project and Working Group Lifecycle](https///allseenalliance.org/about-allseen/governance/project-and-working-group-lifecycle) for more details.

----

#### Project Description:

**//What is the purpose and intent of the project//**\\ 
The intention of this is to move the functionality found in the AboutService in with the core code.  To prevent breaking backwards compatibility the current implementation of the AboutService framework will continue to exist.
 

**//Include any architecture diagrams or specifications//**\\ 
[About Feature 1.0 Feature specification](https///allseenalliance.org/docs-and-downloads/documentation/alljoyn-about-feature-10-interface-specification)

**//How will it benefit the community//**\\ 
Moving the functionality of the About Feature in with the core code will help with several improvements.

*  API method names will match more closely with the names used in the rest of the core code

*  By being fully integrated the about feature will have full access to the internals of the BusAttachment

*  Users no longer need a separate library to use the About Feature

#### Scope:

**//What features and functionality will be developed//**\\ 
All new code will be in the ''ajn'' namespace not the ''ajn::services'' namespace.

''AnnounceHandler'' will become ''AboutListener''

In the core code all callbacks are handled by listeners not by handlers.  By calling it a listener we hold consistent with the naming scheme used in ''alljoyn_core''.

Functionality of the ''AnnouncementRegistrar'' will be moved into ''BusAttachment''.

''AnnouncementRegistrar::RegisterAnnounceHandler'' -> ''BusAttachment.RegisterAboutListener''\\ 
''AnnouncementRegistrar::UnRegisterAnnounceHandler'' -> ''BusAttachment.UnregisterAboutListener''\\ 
''AnnouncemenetRegistrar::UnRegisterAllAnnounceHandlers'' -> ''BusAttachment.UnregisterAllAboutListeners''\\ 

Functionality of the ''AboutService'' will be moved into ''AboutObj''. AllJoyn already has a terminology for code that implements an interface.  It is a ''BusObject'' not a Service. 

''AboutService::Announce'' -> ''AboutObj::Announce''

Functionality of the ''AboutClient'' will be moved into ''AboutProxy''. Once again AllJoyn already has terminology for the remote object that calls a ''BusObject'' it is a ''ProxyBusObject''.

''AboutClient.GetObjectDescripitons'' -> ''AboutProxy.GetObjectDescriptions''\\ 
''AboutClient.GetAboutData'' -> ''AboutProxy.GetAboutData''\\ 
''AboutClient.GetVersion` -> `AboutProxy.GetVersion''\\ 

The ObjectDescription information will no longer be a Public member variable of the ''AnnounceHandler'' as ''std::map`<qcc::String, std::vector<qcc::String>` >'' but will be maintained as a separate class ''AboutObjectDescription''. This does a few things it allows us to hide the internals of the ObjectDesctipion making it simpler to write language bindings.  It also lets us write member functions to help interact with the Object description.

Replace ''AboutPropertyStore'' and ''AboutPropertyStoreImpl'' with a classes ''AboutDataListener'' and ''AboutData'' that handles the same functionality without exposing access to information that is specified in the About Feature specification.  

''AboutPropertyStore'' -> ''AboutDataListener''\\
''AboutPropertyStoreImpl'' -> ''AboutData''

AllJoyn already has a precedent of a virtual class that represents a interface that needs an implementation. The ''KeyStoreListener'' is an example of a class that only has virtual functions.  The naming for this was reused to give the name of the ''AboutDataListener'' class.  Then a default implementation of the ''AboutDataListener'' is provided as the ''AboutData'' class. Unlike the ''AboutPropertyStore'' the ''AboutDataListener'' class only exposes two virtual methods. ''GetMsgArg(arg, language)'' and ''GetMsgArgAnnounce''.  If the developer need more functionality than these two methods there are free to implement it.  This is the minimum functionality required by the About Feature. 

Move the About interfaces definitions into the ''AllJoynObj''. The interfaces in question are ''org.alljoyn.About'' and ''org.alljoyn.Icon''. The ''org.alljoyn.About'' interface will no longer be part of the Announce signal.  The ''org.alljoyn.Icon'' will be part of the Announce signal as long as the user has an instance of the AboutIconObj in their code.

AllJoyn header files will avoid exposing the ''stl'' (Standard template library) because this makes developing language bindings more difficult.

When the ''BusObject'' is registered it should contain a Boolean variable that indicates if the object should be announced and when announce is called that object is automatically announced without the user having to add it to the ''AboutObjectDescription'' explicitly as a separate programming step.
    

**//What AllJoyn interfaces will be developed//**\\ 
 1.  ''org.alljoyn.About''
 2.  ''org.alljoyn.Icon''

**//What is the completion criteria//**\\ 

*  The About Feature rework should be compatible with current implementation of the AboutService

*  It should implement the [About Feature 1.0 Feature specification](https///allseenalliance.org/docs-and-downloads/documentation/alljoyn-about-feature-10-interface-specification)

*  Reached an acceptable level of quality `<sub>`(this is still to be determined)`</sub>`

#### Project Name:

**//Name for the project//**\\ 
About Feature Rework

**//Name for the git repository//**\\ 
''[feature/about_rework](https///git.allseenalliance.org/cgit/core/alljoyn.git/log/?h=refs/heads/feature/about_rework)''

**//Jira Tickets associated with this feature//**\\ 
[ASACORE-775](https///jira.allseenalliance.org/browse/ASACORE-775) - AboutService feature moved into alljoyn_core code base

#### Proposed Working Group:

This work will be done as part of the Core working group.
#### Committers and Contributors:

George Nash `<georgen@qce.qualcomm.com>` is the primary developer and contributor at this time. He will be responsible for initial testing till QA resources are available.

#### Proposed Release Schedule:

This is currently planed for the 14.10 release. It will follow the release cadence of the core working group.

----

#### Reference Links

All of the following links point directly to the the the AllSeen Alliance git repository. The are provided to help aid discussion.  This represents the state of the code at the time the links were posted and does not imply final code.

Gerrit and Git links:
 | Gerrit link                                              | Git tag                                                                                                                                               | current state | details                                                                                                                                                                                           | 
 | -----------                                              | -------                                                                                                                                               | ------------- | -------                                                                                                                                                                                           | 
 | [1992](https///git.allseenalliance.org/gerrit/#/c/1992)  | [a87040a7c2cc040f8cad0ccf84ba3d187b203abb](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=a87040a7c2cc040f8cad0ccf84ba3d187b203abb) | Merged        | Initial public commit contains work on most listed features                                                                                                                                       | 
 | [2035](https///git.allseenalliance.org/gerrit/#/c/2035)  | [0c53b69bdb199a1f9dce4673db47c62d22d9db07](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=0c53b69bdb199a1f9dce4673db47c62d22d9db07) | Merged        | Unit tests added interface matching bug fixed                                                                                                                                                     | 
 | [2036](https///git.allseenalliance.org/gerrit/#/c/2036/) | [5dea1aa94fbc11497837299898ae950b7bc0a1bf](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=5dea1aa94fbc11497837299898ae950b7bc0a1bf) | Merged        | Removed AboutObj init member function.                                                                                                                                                            | 
 | [2038](https///git.allseenalliance.org/gerrit/#/c/2038/) | [b7a2e57942ac46779a3b58b125e23dfd756c40cb](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=b7a2e57942ac46779a3b58b125e23dfd756c40cb) | Merged        | Ability to specify is an interface is announced when adding it to a BusObject                                                                                                                     | 
 | [2039](https///git.allseenalliance.org/gerrit/#/c/2039/) | [45a544524bcff7f8cf462ea2654f480c1a31786d](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=45a544524bcff7f8cf462ea2654f480c1a31786d) | Merged        | Add member function to the AboutObjectDescription class to make working with that class simpler                                                                                                   | 
 | [2040](https///git.allseenalliance.org/gerrit/#/c/2040/) | [f4323c0a09e51a360b86ddb92936ce77a83546cb](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=f4323c0a09e51a360b86ddb92936ce77a83546cb) | Merged        | AboutObj can automatically obtain a list of interfaces that were marked as announced when that interface was added to the BusObject and that BusObject is added to the BusAttachment.             | 
 | [2041](https///git.allseenalliance.org/gerrit/#/c/2041/) | [cbf8a63b0aad354c78a33853d8ec9d9d431b09b9](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=cbf8a63b0aad354c78a33853d8ec9d9d431b09b9) | Merged        | GetInterfacePaths member function added to the AboutObjectDescription.  Makes it possible to get a list of object paths for a given interface.                                                    | 
 | [2042](https///git.allseenalliance.org/gerrit/#/c/2042/) | [ba7e3871a46823ed08b558f156a113ee596e92c2](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=ba7e3871a46823ed08b558f156a113ee596e92c2) | Merged        | Changed names of member functions in the About Data to Get/Set functions not Add/Get.                                                                                                             | 
 | [2080](https///git.allseenalliance.org/gerrit/#/c/2080/) | [512572083999a946c895bd31dd738dcf48c046a3](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=512572083999a946c895bd31dd738dcf48c046a3) | Merged        | Sample programs and unit tests                                                                                                                                                                    | 
 | [2081](https///git.allseenalliance.org/gerrit/2081)      | [4ff1b109552af73dad8cb5c6ed10b2873e6ed5fb](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=4ff1b109552af73dad8cb5c6ed10b2873e6ed5fb) | Merged        | Initial implementation of the org.alljoyn.Icon interface. This implementation is quite similar to the original implementation of org.alljoyn.Icon implementation before the About Feature rework. | 
 | [2082](https///git.allseenalliance.org/gerrit/2082)      | [4c82665cc78c0c9f768db0a09ff000b6df8757b2](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=4c82665cc78c0c9f768db0a09ff000b6df8757b2) | Merged        | Fixed issues identified in code review. Thank you to user dmessing.                                                                                                                               | 
 | [2178](https///git.allseenalliance.org/gerrit/#/c/2178)  | [a4c86ecdbe0f2fd6fdc0fcd7f76159325df5b114](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=a4c86ecdbe0f2fd6fdc0fcd7f76159325df5b114) | Merged        | Merged origin/master into feature/about_rework                                                                                                                                                    | 
 | [2180](https///git.allseenalliance.org/gerrit/#/c/2180)  | [eb85e6cad308041752a7fdd16d30c88de6587136](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=eb85e6cad308041752a7fdd16d30c88de6587136) | Merged        | Fixed multiple issues identified in code review.                                                                                                                                                  | 
 | [2181](https///git.allseenalliance.org/gerrit/#/c/2181)  | [b8b608a4c6f84a30a460ca895352325cee4a5fed](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=b8b608a4c6f84a30a460ca895352325cee4a5fed) | Merged        | Replaced boolean value to specify if an interface was announced with an enum value UNANNOUNCED or ANNOUNCED making code more readable.                                                            | 
 | [2193](https///git.allseenalliance.org/gerrit/#/c/2193)  | [9c1c0ac07e001704c6081a29e12fed1509b44ab8](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=9c1c0ac07e001704c6081a29e12fed1509b44ab8) | Merged        | Add the virtual AboutDataListener class. This has the same function as the original PropertyStore class.                                                                                          | 
 | [2194](https///git.allseenalliance.org/gerrit/#/c/2194/) | [653bc30ef6580d7f3ea8b9ce951ca0f0a72ee31a](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=653bc30ef6580d7f3ea8b9ce951ca0f0a72ee31a) | Merged        | Removed the BusAttachment.GetAboutObjectDescription from the public API                                                                                                                           | 
 | [2196](https///git.allseenalliance.org/gerrit/#/c/2196/) | [853c3691b7d44da8a97e26207f10a8c43c59ae82](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=853c3691b7d44da8a97e26207f10a8c43c59ae82) | Merged        | GetAboutObjectDescription changed to GetAnnouncedObjectDescription also methods now return MsgArg not some other class this is more future proof design                                           | 
 | [2209](https///git.allseenalliance.org/gerrit/#/c/2209/) | [cd3c565bc694971229879ff3a507e72a5cdd42cd](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=cd3c565bc694971229879ff3a507e72a5cdd42cd) | Merged        | You must have a registered BusObject to make an announcement you no longer can pass in an interface name that you don't actually own                                                              | 
 | [2210](https///git.allseenalliance.org/gerrit/#/c/2210/) | [431669d63b0cec9d0f697f6199739d74be7e53fa](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=431669d63b0cec9d0f697f6199739d74be7e53fa) | Merged        | Add option to announce the org.alljoyn.About interface this option is off by default                                                                                                              | 
 | [2211](https///git.allseenalliance.org/gerrit/#/c/2211/) | [1f8e60d34c1def2993ad77f9025a5ed02c8908ee](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=1f8e60d34c1def2993ad77f9025a5ed02c8908ee) | Merged        | Removed functions that are no longer needed from the AboutObjectDescription class                                                                                                                 | 
 | [2213](https///git.allseenalliance.org/gerrit/#/c/2213/) | [6c47b66c36c109531c3523c25498614482c4b58b](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=6c47b66c36c109531c3523c25498614482c4b58b) | Merged        | Merged origin/master into feature/about_rework                                                                                                                                                    | 
 | [2240](https///git.allseenalliance.org/gerrit/#/c/2240/) | [be378f205b8f3d0e64a986dcb00cbd55e4b4757f](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=be378f205b8f3d0e64a986dcb00cbd55e4b4757f) | Merged        | When a localized value is added to the AboutData the language is automatically added to the supported languages tag                                                                               | 
 | [2242](https///git.allseenalliance.org/gerrit/#/c/2242/) | [c4f18832831a43f3e9d6054f9fbc5a600dcf8fe0](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=c4f18832831a43f3e9d6054f9fbc5a600dcf8fe0) | Merged        | AboutObj::CancelAnnouncement added method added                                                                                                                                                   | 
 | [2243](https///git.allseenalliance.org/gerrit/#/c/2243/) | [9b58390babd4e5d0e68aba4fc8aa645f86237c7e](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=9b58390babd4e5d0e68aba4fc8aa645f86237c7e) | Merged        | Small improvements to reduce the amount mem copies are done with strings                                                                                                                          | 
 | [2244](https///git.allseenalliance.org/gerrit/#/c/2244/) | [69777c62137c4c82aab34c68bc787d741e8fce63](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=69777c62137c4c82aab34c68bc787d741e8fce63) | Merged        | Modified the headers to use const char* instead or qcc::String in may locations                                                                                                                   | 
 | [2257](https///git.allseenalliance.org/gerrit/#/c/2257/) | [233276d5efee637ca0322522af4fb1691fd77fb8](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=233276d5efee637ca0322522af4fb1691fd77fb8) | Merged        | Split the Register listener into two parts the RegisterListener and WhoImplements member functions                                                                                                | 
 | [2258](https///git.allseenalliance.org/gerrit/#/c/2258/) | [8501ad0baa66574b371c0828594b227b346e3809](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=8501ad0baa66574b371c0828594b227b346e3809) | Merged        | Additional unit test for the AboutData class                                                                                                                                                      | 
 | [2286](https///git.allseenalliance.org/gerrit/#/c/2286/) | [19b3e2d7cfb139b10f7f5e4b0a40350d9e0e0b59](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=19b3e2d7cfb139b10f7f5e4b0a40350d9e0e0b59) | Merged        | Merged origin/master into feature/about_rework                                                                                                                                                    | 
 | [2316](https///git.allseenalliance.org/gerrit/#/c/2316/) | [5f34b179f1b3faa2e491a4549590dbaacb5ce4b1](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=5f34b179f1b3faa2e491a4549590dbaacb5ce4b1) | Merged        | GetObjectDescriptions changed to GetObjectDescription                                                                                                                                             | 
 | [2333](https///git.allseenalliance.org/gerrit/#/c/2333/) | [553ce550c6cf0152af4cf477664bd5d334febb56](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=553ce550c6cf0152af4cf477664bd5d334febb56) | Merged        | Additional unit tests for the AboutData class                                                                                                                                                     | 
 | [2349](https///git.allseenalliance.org/gerrit/#/c/2349/) | [e786aee1cef345d9430af6794945079af7412ae6](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=e786aee1cef345d9430af6794945079af7412ae6) | Merged        | Add more printout information to the Aboutclient sample                                                                                                                                           | 
 | [2350](https///git.allseenalliance.org/gerrit/#/c/2350/) | [457ad01e9f45c51d1df49cefccbc362f4ab100ef](https///git.allseenalliance.org/cgit/core/alljoyn.git/commit/?id=457ad01e9f45c51d1df49cefccbc362f4ab100ef) | Merged        | Update AboutClient test code to handle many announcements                                                                                                                                         | 
----

#### Question Answer Section

''About Service'' == Current implementation of the About Feature.\\
''About Feature'' == The About Feature rework that this Wiki is addressing.

Since many questions have been sent to directly to me (George Nash) not to the allseen-core mailing list `<allseen-core@lists.allseenalliance.org>` I have decided to compile a question/answer section to avoid responding to questions multiple times. Please feel free to ask any question via the allseen-core mailing list.  I will respond to those questions.  If I feel they add any value I they will be added to this list.

**Q:** How long are you planning on keeping the old code in place for backward compatibility?\\
**A:** This has not been decided. This is a decision for the AllSeen Alliance Core working group. I personally think it should be around for at least a year maybe longer.

**Q:** The wiki says you are changing  ''AnnounceHandler'' to ''AnnounceListener'' it looks in the code like you call it AboutListener.\\
**A:** I originally planned on naming it ''AnnounceListener''.  As I did the work I felt naming it ''AboutListener'' made more since.  I did not catch the name change when I made the wiki page. I have updated the wiki page.

**Q:** Is the name of the announce signal going to stay announce or will it be About?\\
**A:** The About Feature rework is using the interface definition as it is specified in the About Feature specification.  There are not modifications to the interface. So yes the announce signal is still ''Announce''.

**Q:** The property store implementation in Java is not part of the about service, how are you planning on implementing the about data?\\
**A:** I have not started the work on the Java language binding for the About Feature.  My plan is to have a very similar implementation as the C++ implementation.  There will be an ''AboutData'' class that has ''Get''/''Set'' methods for all of fields specified in the About Feature Specification. The class will then have a way of providing the data as a ''MsgArg'' for the actual ''Announce'' signal.

**Q:** You write that the About and Icon interfaces will not be announced, since it is always implemented. Is it really?\\
**A:** What this means is the About and Icon interfaces are now integrated as part of the AllJoyn Object that everyone gets automatically when using AllJoyn.  Announcing that we have those interfaces becomes less
meaningful when everyone has the interface. The big question is did a developer provide the data needed for the interface.  I don’t think adding the org.alljoyn.About will add any information to the user.  If they get
an ''Announce'' signal they automatically know that the user has the ''org.alljoyn.About'' interface because they got the ''Announce'' signal. On the other hand adding ''org.alljoyn.Icon'' to the announcement could have added information since it tells the developer that an icon is available. **Update:** If an ''AboutIcon'' bus object is implemented it will announce the ''org.alljoyn.Icon'' interface for the reason given. 

**Q:** Do you have to implement an icon?\\
**A:** no just like today you don’t have to implement an icon.

**Q:** At what point in the code is it checked that the bus implements the about data?\\
**A:** The ''org.alljoyn.About'' interface is added to the bus at startup.  Methods like ''GetObjectDescription'' and ''GetAboutData'' are available but if they are called before the ''AboutData'' or ''AboutObjectDescription'' is provided by the developer to the application the method calls will fail.

**Q:** Will there be any checking if about fields are empty/legal?\\
**A:** Right now the code checks if the the required about fields are provided and that is about it.  There is very little verification of the fields at this time.  I want to add verification of fields that can be verified.  For example we should verify things like the language tag used is at least a valid tag per RFC 5646 (checking that it’s a legal tag is something we can do checking if it’s real language I think may be beyond what resonable).  The DateOfManufacture should be checked to see that it is of the XML Data Time Format (YYYY-MM-DD).  DeviceId and AppId should be UUIDs per the RFC 4122. These are things that should be validated but currently are not validated, in both the ''About Service'' and the ''About Feature'' as it currently is implemented.

**Q:** Did you remove the Icon URL option?\\
**A:** No I just did not get that part implemented yet. That change should go in soon. //Change has gone in and the review can be found [here](https///git.allseenalliance.org/gerrit/2081).//

**Q:** Looks like the App ID is no longer a UUID, was this on purpose? I think we want to keep it as a UUID so it is backwards compatible.\\
**A:** Yes it was done on purpose.  According to the specification the ''AppId'' should be an array of bytes not a String. Although the public specification does not say what those bytes should be the usage guide has stated that it should be a UUID as specified in RFC 4122.  The RFC has information on converting to a string and back.  The ''About Service'' (current implementation) has a function that converts a string to an array of bites.  I don’t think the function does this as is specified in the RFC 4122. I can add a helper function that does the same thing as the ''About Service'' to the ''About Feature'' to make migration simpler.

**Q:** In the client code we see you have and ''AddMatch'' for ''type = ‘error’'', I think this is not needed anymore since 14.06, is it just legacy code?\\
**A:** That was in the client code because legacy code.  I wrote that client sample before the ''AddMatch'' error was fixed and did not remove it after the error was fixed.  It should not be in the code.  `<del>`Thanks for the catch it will be removed in a future commit.`</del>` It has been removed.

**Q:**	''DeviceId'': We would like the device Id to be unique per device (across multiple applications) maybe About can take care of this?\\
**A:** I am aware of this problem. I currently don’t have a good fix for it. This is actually a really hard problem that is platform specific for each platform.   Yes this is a problem that the ''About Feature'' should take care of I don’t know if it will make it in the first draft of the About Feature rework.

**Q:** Do we want to add some flag just like we add an option to say if this interface/object is announcable that is implements ''org.allseen.introspectable'', for easily knowing that an interface has events and actions?\\
**A:** I don’t know enough about the event and actions to say for sure. If you want the event and actions interface to be announced then yes you could add a flag to make that interface announced.

**Q:**: I understand that About will probably become more or less automatically enabled for every AllJoyn application. About is also tied to the BusAttachment. What is the implication of this for applications that have multiple BusAttachments?\\
**A:**: The About Interface will be part of every application.  It is still up to the developer to make sure the ''AboutData'' and ''AboutObjectDescription'' is populated.  Your question points out one of the major problems I have with the current implementation of the ''About Service''.  The only thing that is tied to the application is the ''AboutData''.  The ''AboutObjectDescritpion'' information is about the ''BusObjects'' that a ''BusAttachment'' implements.  Since the current implementation forces you to use a singleton and that singleton only knows about one ''BusAttachment'' you can only ''Announce'' Objects that are on the one  BusAttachment.  

With the proposed design if you have two ''BusAttachments'' in a single application they can share the same ''AboutData''.  Since the ''AboutData'' is maintained as a separate class it can be shared between two BusAttachments.  Most important however is that now both ''BusAttachments'' can make an announcement that contains ''AboutObjectDescriptions'' for ''BusObjects'' they implement.  With the current ''AboutService'' implementation, only one of the ''BusAttachments'' can do that. **note:** ''BusAttachment''s require lots of resources and we strongly encourage usage of only a single ''BusAttachment''

**Q:** will liballjoyn_about.so disappear over time then?\\
**A:** Yes liballjoyn_about.so will disappear when the current implementation is deprecated. 

**Q:** Regarding ''AppId'' and ''DeviceId'', I know this is a platform specific question, but is it planned to have those two parameters persistent?\\
**A:** ''AppId'' should be persistent to the application.  While ''DeviceId'' should be persistent to the Device.  If an announce signal is received from a phone with a given ''DeviceId''.  Then some time later you connect with the same phone it should give the same ''DeviceId''.  The ''AppId'' should be connected to the application. If you get an ''AppId'' from ''App1'' then get an ''AppId'' from ''App2'' those ''AppId''s should differ even if they came from the same device.  Just like the ''DeviceId'' if you connect with same copy of ''App1'' the ''AppId'' should be the same as it was the first time you connected with that application.  I still do not know what the behavior should be if multiple copies of an application is run.  For example if two copies of ''App1'' were run on a PC should both copies use the same ''AppId'' or should they each contain their own ''AppId''.  What about later if the computer restarts and launches ''App1'' again which ''AppId'' does it get assigned?

**Q:** Regarding aboutdata. The old property store had the ability to add customized user fields that would be announced. Will this capability be kept? Why? How?\\
**A:** Yes you can make a customized user field that is announced. **How?** By default you cannot add an announced custom user field to the ''AboutData'' class. If you implement a class that inherits from the ''AboutData'' class you can add a custom field where you can set the field values to be anything you want. Is it required? Is it Announced? Is it localizable? What is the signature (data type) of the field?  I have an example of a class with customized user field that is announced in the unit tests. **why?** To the best of my understanding the ability to add user defined fields to the ''AboutData'' is a requirement for the config service. The ''About Feature'' should not remove any functionality that exists in the ''About Service''.


