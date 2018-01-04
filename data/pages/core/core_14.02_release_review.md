# Core 14.02 Release Review

## Features

About feature support added for iOS.

## Non-Code Aspects

Link to user documents, examples, tutorials

## Architectural Issues

Renamed libajdaemon.a and BundledDaemon.o to libajrouter.a and BundledRouter.o to match the AllJoyn terminology of leaf and router nodes.

## Security Issues

Several crash and deadlock issues identified and fixed.

## Quality Assurance


*  AllJoyn Standard Library was tested successfully on the following:
      * Ubuntu 12.04
      * Android JellyBean
      * iOS 7
      * OS X Mavericks
      * Windows 7/8 (x86)
      * OpenWRT

*  AllJoyn Thin Library was tested successfully on the following:
      * Ubuntu 12.04
      * Windows 7
      * ARM-based embedded platform

We have a layered approach to testing that starts with verifying core functionality, such as messaging and security.  Then, we execute platform-specific tests for each of the platforms listed above.  This includes testing of transports, bindings, sample applications, as well as stress testing.  We also conduct interoperability testing to ensure that, for example, AllJoyn applications running on a Windows laptop can interact with applications running on an Android phone.  Finally, we do backward compatibility testing to ensure, for example, that a new routing node will communicate with an older routing node.
    
Issues identified during testing are documented in our bug tracking system.  A triage process assigns the bugs a priority and a release target.  Naturally, the highest priority bugs are targeted for the next release.  Once a bug has been resolved-fixed, then the bug fix is verified, and the bug is closed.
## Known Issues

ALLJOYN-1967: AllJoyn router cannot (quickly) detect disconnection of non-local
client connection such as thin-client connection

ALLJOYN-2192: AllJoyn thin client does not support header compression

ALLJOYN-2374: AllJoyn thin client binding cannot send/receive messages larger
than 55KB

ALLJOYN-2504: Calling GetPeerGUID from RequestCredentialsAsync callback may
cause deadlock when AllJoyn is built with OpenSSL without multi-thread support

AJCORE-271: Infrequent crash when running thread stress test on OpenWRT.

## End-of-life

Removed support for Windows RT.

## Standards Compliance

N/A

## Schedule Post-Mortem

Compare actual project milestones to the published release plan estimates

