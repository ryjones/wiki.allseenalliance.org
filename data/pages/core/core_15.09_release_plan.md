# Core 15.09 Release Plan

## Introduction

Development leads are

*  Microsoft: Arvind Padole

*  QCE: Marcello Lioy

*  Qeo: Kristof Martens 
The QA lead is David McBride.

## Themes and Priorities

**New Features**:
Full list in [ JIRA](https///jira.allseenalliance.org/issues/?jql=project%20%3D%20ASACORE%20AND%20issuetype%20%3D%20%22New%20Feature%22%20AND%20fixVersion%20%3D%20%2215.09%22%20ORDER%20BY%20status%20ASC)
 | JIRA Key                                                             | Feature                                                    | Contributor    | 
 | --------                                                             | -------                                                    | -----------    | 
 | [ASACORE-1686](https///jira.allseenalliance.org/browse/ASACORE-1686) | Make UDP Transport for TC `<->` RN connections product ready | QCE            | 
 | [ASACORE-1393](https///jira.allseenalliance.org/browse/ASACORE-1393) | Security 2.0                                               | MSFT, QCE, QEO | 


## Deliverables

Source:

*  AllJoyn Standard Library (C++, C, Java)

*  AllJoyn Thin Library

AllJoyn Standard Library SDK:

*  Android


## Milestones

 | Milestone        | Date       | Details    | 
 | ---------        | ----       | -------    | 
 | Dev Complete     | 2015/08/03 | ✔        | 
 | Code Freeze      | 2015/09/21 | 2015/09/24 | 
 | QA Complete      | 2015/09/25 | 2015/09/29 | 
 | Alliance Release | 2015/09/30 | ✔        | 


## Expected Work Group Dependencies

None.
## Compatibility with Previous Releases

*  Claimed 15.09 apps/devices (A/D using Security 2.0) cannot interact securely with pre-15.09 A/D using ECDHE_ECDSA key exchange; further, if the A/D only exposes interfaces/objects requiring security it will not be possible to interact with the A/D. This is because once an A/D is claimed, it expects to receive a manifest from the ECDHE_ECDSA peer, and pre-15.09 A/D do not support sending manifests (which were introduced as part Security 2.0 in the 15.09 release).

*  Language tag matching uses prefix matching and also will return the default language if there is no match where previously it would return an error. (ASACORE-2209)

*  Moving the PropertiesChanged signal from the org.freedesktop.DBus interface to the org.freedesktop.DBus.Properties interface (ASACORE-2185) stops applications based on AllJoyn 15.04 and older from receiving this signal from those based on 15.09 and newer, and vice versa. The impact should not be significant since the PropertiesChanged functionality prior to the 15.09 release did not work.  Note that the change in the alljoyn.git project was done in 14.12, so this makes TC applications compatible with SC applications.

*  The APIs for About in the core/about_tcl repo are (still) DEPRECATED

*  AJTCL Source Compatibility
    * Crypto API changes to enhance target portability
      * Removed internal APIs that were unused or could be statically scoped
        * AJ_Crypto_PRF()
        * HMAC functions
      * Updated APIs and data types to hide implementation details
        * ECC functions
        * SHA256
          * AJ_SHA256_Init() now returns an opaque context pointer rather than having the caller manage the context
          * AJ_SHA256_Init() must now be matched with a call to AJ_SHA256_Final() to free resources
          * AJ_SHA256_GetDigest() lost the keepAlive parameter, and always keeps the hash alive. Use AJ_256_Final() if keepAlive is not needed.
      * Moved some APIs to new header files
        * DRBG declarations have moved to aj_crypto_drbg.h (only needed on targets without a CPRNG)
        * Software AES declarations have moved to aj_crypto_aes_priv.h
