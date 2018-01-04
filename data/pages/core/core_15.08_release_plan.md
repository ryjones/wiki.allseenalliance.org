# **DRAFT** Core 15.08 Release Plan

## Introduction

Development leads are

## Themes and Priorities

**New Features**:
Full list in [ JIRA](Need jira filter)
 | JIRA Key | Feature | Contributor | 
 | -------- | ------- | ----------- | 


## Deliverables

Source:

*  AllJoyn Standard Library 

*  AllJoyn Thin Library

AllJoyn Standard Library SDK:

AllJoyn Thin Library SDK:

*  Linux

*  Windows

## Milestones

 | Milestone        | Date | Details | 
 | ---------        | ---- | ------- | 
 | Dev Complete     |      |         | 
 | Code Freeze      |      |         | 
 | QA Complete      |      |         | 
 | Alliance Release |      |         | 

## Expected Work Group Dependencies


## Compatibility with Previous Releases

*  ''EncodePublicKeyPEM()'', ''DecodePublicKeyPEM()'', ''EncodePrivateKeyPEM()'', and ''DecodePrivateKeyPEM()'' in ''qcc::CertificateX509'' which take ''uint8_t'' arrays are being deprecated in favor of versions that operate on ''qcc::ECCPublicKey'' and ''qcc::ECCPrivateKey'' classes instead. Applications currently using this functionality should move to the versions that use the proper abstractions. ''ECCPublicKey'' and ''ECCPrivateKey'' provide the import and export functionality when working with raw key bytes directly is required.

