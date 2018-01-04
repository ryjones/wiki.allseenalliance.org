# DDAPI Project Termination Review

The DDAPI Project committers are formally proposing to terminate the project after the release of DDAPI r15.04.
 
## Reason for termination

 
The end product of the DDAPI project consists of an alternative API for AllJoyn Core, with the following characteristics:

*  Emphasis on the publish-subscribe interaction model

*  A simplified API, when compared to AllJoyn Core

*  Use of a code generator to remove boilerplate code related to type description and message marshaling
 
After the first release of the DDAPI, the project contributors started work on migrating the essential pub/sub functionality from the DDAPI (the Observer API and the ProxyBusObject property cache) to AllJoyn Core. From Core R15.04 onwards, there is no functionality left in the DDAPI that is not covered by an equivalent (although sometimes more elaborate) API in AllJoyn Core.
 
Furthermore, although we still believe there’s a need for simplification of AllJoyn API’s, we have come to the conclusion that this is something that is likely best tackled in AllJoyn Core directly, to avoid duplication of efforts and to assure broad adoption in the user community.
 
In this light, we see no compelling reason to maintain the separate API, with all the maintenance burden that entails. The DDAPI contributors will spend their future efforts on the refinement of AllJoyn Core.
 
## Impact on other projects, users and communities

 
The only project that is directly impacted by the termination of the DDAPI project is the code generator project, as it contains the templates and code for the DDAPI/C++ code generator. The DDAPI contributors will remove the relevant templates from the ''devtools/codegen'' repository in time for the R15.09 release of the code generator.
 
## Where should the project be archived?

 
We propose to keep the ''data/datadriven_api'' repository in its current form. We will clearly indicate the “archived” state of the project in the README file that is part of this repository. We will also do the same on the main wiki page for the DDAPI project, and in the DDAPI documentation that is published on [the Alliance documentation pages](http://allseenalliance.org/developers/learn/ddapi).
