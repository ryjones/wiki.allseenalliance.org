# Outdated Security 2.0 Interfaces

This page lists the outdated interfaces used in Security 2.0

## Permission Module

The Permission Module is the major component of the Security 2.0 system.  This module manages the permission policies and enforces the security rules. This module is exposed via the secure interface PermissionMgmt.

### Interface PermissionMgmt

 | Interface Name             | org.allseen.Security.PermissionMgmt                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       ||||
 | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 | Object path                | /org/allseen/Security/PermissionMgmt                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      ||||
 | Method Name                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Input                                                                                                        | Output                                                                         | Description                                                                                                                      | Access\\ Restriction                                                                                                                                                                                                             |    
 | Claim                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | public key – a KeyInfo object representing the public key of the claimer                                   | public key – a KeyInfo object representing the public key of the device/app. | Claim the app.  This will make the claimer the admin and certificate authority.   The KeyInfo object description is shown below. | None if the app is not yet claimed.   An error will be raised if the app already has an admin and it is not the caller.                                                                                                          | :::
 | :::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Identity Cert – an identity certificate for the claimed app                                                | :::                                                                            | :::                                                                                                                              | :::                                                                                                                                                                                                                              |    
 | InstallPolicy                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | authorization – variant for the authorization data                                                         | None                                                                           | Install the static policy to the app.  It replaces any existing policy on the app.                                               | Only an admin of the app is allowed.                                                                                                                                                                                             |    
 | InstallEncryptedPolicy                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | encryptedAuthData – byte array for the encrypted authorization data                                        | None                                                                           | Decrypt and install the static policy to the app.  It replaces any existing policy on the app.                                   |                                                                                                                                                                                                                                  |    
 | RemovePolicy                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | None                                                                                                         | None                                                                           | Remove the currently installed policy from the app.                                                                              | Only an admin of the app is allowed.                                                                                                                                                                                             |    
 | GetPolicy                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | None                                                                                                         | authorization – variant for the authorization data                           | Retrieve the currently installed policy from the app.                                                                            | Only an admin of the app is allowed.                                                                                                                                                                                             |    
 | InstallMembership                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | certChain – the certificate chain for the guild membership.  Only X.509 DER format is currently supported. | None                                                                           | Install a membership cert to the app. The Certificate object description is shown below.                                         | Only an admin of the app is allowed.                                                                                                                                                                                             |    
 | InstallMembershipAuthData                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | serialNum – a string representing the serial number of the membership certificate                          | None                                                                           | Install a membership authorization data to the app                                                                               | Only an admin of the app is allowed. Only membership authorization with a matching membership certificate is accepted. The hash digest of the authorization is verified against the digest listed in the membership certificate. |    
 | :::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | issuer-- a byte array representing the issuer GUID                                                           | :::                                                                            | :::                                                                                                                              | :::                                                                                                                                                                                                                              |    
 | :::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | authorization – variant for the authorization data                                                         | :::                                                                            | :::                                                                                                                              | :::                                                                                                                                                                                                                              |    
 | RemoveMembership                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | serialNum – a string representing the serial number of the membership certificate                          | None                                                                           | Remove a membership certificate from the app.  Any corresponding membership authorization data will be also be removed.          | Only an admin of the app is allowed.                                                                                                                                                                                             |    
 | :::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | issuer-- a byte array representing the issuer GUID                                                           | :::                                                                            | :::                                                                                                                              | :::                                                                                                                                                                                                                              |    
 | InstallIdentity                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | cert – The certificate of the identity.  Only X.509 DER format is currently supported.                     | None                                                                           | Install an identity cert to the app. The Certificate object description is shown below.                                          | Only an admin of the app is allowed.                                                                                                                                                                                             |    
 | GetIdentity                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | None                                                                                                         | identity cert – Only X.509 DER format is currently supported.                | Retrieve the identity cert from the app                                                                                          | None.                                                                                                                                                                                                                            |    
 | InstallGuildEquivalence                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | cert – the certificate of the guild equivalence cert.  Only X.509 DER format is currently supported.       | None                                                                           | Install a guild equivalence to the app. The Certificate object description is shown below.                                       | Only an admin of the app is allowed.                                                                                                                                                                                             |    
 | RemoveGuildEquivalence                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | serialNum – a hex string representing the serial number of the certificate                                 | None                                                                           | Remove a guild equivalence from the app                                                                                          | Only an admin of the app is allowed.                                                                                                                                                                                             |    
 | :::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | issuer-- a byte array representing the issuer GUID                                                           | :::                                                                            | :::                                                                                                                              | :::                                                                                                                                                                                                                              |    
 | GetManifest                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | None                                                                                                         | manifest – variant for the manifest data                                     | Retrieve the manifest data installed by the application developer.                                                               |                                                                                                                                                                                                                                 
 | GetPublicKey                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | None                                                                                                         | public key – the public key of the application.                              | Retrieve the public key                                                                                                          |                                                                                                                                                                                                                                 
 | Reset                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | None                                                                                                         | None                                                                           | Reset to its original state by deleting all the trust anchors, DSA keys, installed policy and certificates.                      | Only an admin of the app is allowed.                                                                                                                                                                                             |    
 | InstallCredential                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | type – the type of credential                                                                              | None                                                                           | Install additional credential to the app.  It can be an additional trust anchor.                                                 | Only an admin of the app is allowed.                                                                                                                                                                                             |    
 | :::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | credential - the credential. The credential object description is shown below.                               | :::                                                                            | :::                                                                                                                              | :::                                                                                                                                                                                                                              |    
 | RemoveCredential                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | type – the type of credential                                                                              | None                                                                           | Remove a credential from the app.                                                                                                | Only an admin of the app is allowed.                                                                                                                                                                                             |    
 | :::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | credentialID - the credential Identifier. The credential ID description is shown below.                      | :::                                                                            | :::                                                                                                                              | :::                                                                                                                                                                                                                              |    


### Interface PermissionMgmt.Notification

 | Interface Name      | org.allseen.Security.PermissionMgmt.Notification |                                                                                                                                    |              |                                                                                                                          |    
 | ---------------------------------------------------------------------- |                                                                                                                                    |              |                                                                                                                          |    
 | Object path | /org/allseen/Security/PermissionMgmt||||                
 | Signal Name                                                            | Params                                                                                                                             | Session-less | Description                                                                                                              |     | 
 | NofityConfig                                                           | version -- the PermissionMgmt version number                                                                                       | yes          | Notification of permission configuration.  This signal is emitted at startup time and when the configuration is changed. |     | 
 | :::                                                                    | publicKey -- public key of the application                                                                                         | :::          | :::                                                                                                                      | ::: | 
 | :::                                                                    | claimableState – an enum value for the claimable state.\\ Valid values are:\\ 0 -- not claimable\\ 1 -- claimable\\ 2 -- claimed | :::          | :::                                                                                                                      | ::: | 
 | :::                                                                    | trust anchors -- array of `<trust anchor usage type, keyInfo>` pairs                                                                 | :::          | :::                                                                                                                      | ::: | 
 | :::                                                                    | policySerialNum -- the policy serial number                                                                                        | :::          | :::                                                                                                                      | ::: | 
 | :::                                                                    | memberships-- array of `<guildID, cert serialNumber>` pairs                                                                          | :::          | :::                                                                                                                      | ::: | 

### Introspection XML

	
	<node
	      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	      xsi:noNamespaceSchemaLocation="https://allseenalliance.org/schemas/introspect.xsd">
	    `<interface name="org.allseen.Security.PermissionMgmt">`
	        `<method name="Claim">`
	            `<arg name="publicKey" type="(yv)" direction="in"/>`
	            `<arg name="identityCert" type="(yay)" direction="in"/>`
	            `<arg type="(yv)" direction="out"/>`
	        `</method>`
	        `<method name="InstallPolicy">`
	            `<arg name="authorization" type="(yv)" direction="in"/>`
	        `</method>`
	        `<method name="InstallEncryptedPolicy">`
	            `<arg name="encryptedAuthorization" type="ay" direction="in"/>`
	        `</method>`
	        `<method name="GetPolicy">`
	            `<arg type="(yv)" direction="out"/>`
	        `</method>`
	        `<method name="RemovePolicy">`
	        `</method>`
	        `<method name="InstallMembership">`
	            `<arg name="certChain" type="a(yay)" direction="in"/>`
	        `</method>`
	        `<method name="InstallMembershipAuthData">`
	            `<arg name="serialNum" type="s" direction="in"/>`
	            `<arg name="issuer" type="ay" direction="in"/>`
	            `<arg name="authorization" type="(yv)" direction="in"/>`
	        `</method>`
	
	        `<method name="RemoveMembership">`
	            `<arg name="serialNum" type="s" direction="in"/>`
	            `<arg name="issuer" type="ay" direction="in"/>`
	        `</method>`
	        `<method name="InstallIdentity">`
	            `<arg name="cert" type="(yay)" direction="in"/>`
	        `</method>`
	        `<method name="GetIdentity">`
		    <arg name="cert" type="(yay)" direction="out"/>
	        `</method>`
	        `<method name="InstallGuildEquivalence">`
	            `<arg name="cert" type="(yay)" direction="in"/>`
	        `</method>`
	        `<method name="RemoveGuildEquivalence">`
	            `<arg name="serialNum" type="ay" direction="in"/>`
	            `<arg name="issuer" type="ay" direction="in"/>`
	        `</method>`
	        `<method name="GetManifest">`
	            `<arg type="(yv)" direction="out"/>`
	        `</method>`
	        `<method name="Reset">`
	        `</method>`
	        `<method name="GetPublicKey">`
	            `<arg type="(yv)" direction="out"/>`
	        `</method>`
	        `<method name="InstallCredential">`
	            `<arg name="type" type="y" direction="in"/>`
	            `<arg name="credential" type="v" direction="in"/>`
	        `</method>`
	         `<method name="RemoveCredential">`
	            `<arg name="type" type="y" direction="in"/>`
	            `<arg name="credentialID" type="v" direction="in"/>`
	        `</method>`
	     `</interface>`
	     `<interface name="org.allseen.Security.PermissionMgmt.Notification">`
	        `<signal name="NotifyConfig">`
	            `<arg name="version" type="q"/>`
	            `<arg name="publicKeyInfo" type="a(yv)"/>`
	            `<arg name="claimableState" type="y"/>`
	            `<arg name="trustAnchors" type="a(yv)"/>`
	            `<arg name="serialNumber" type="u"/>`
	            `<arg name="memberships" type="a(ayay)"/>`
	        `</signal>`
	    `</interface>`
	`</node>`
	



### Key Info Object Signature

The KeyInfo object is used to represent the public key.


 | KeyInfo (yv) |           |                                                                                                                                                                                                                  | 
 | ------------ |           |                                                                                                                                                                                                                  | 
 | Field        | Signature | Description                                                                                                                                                                                                      | 
 | format       | y         | Key format.  Current values: \\ 0 -- AllJoyn\\ 1 -- JSON Web Key [JWK](https///tools.ietf.org/html/draft-ietf-jose-json-web-key-32#section-3)\\ 2 -- [X.509](http://tools.ietf.org/html/rfc5280#section-4.1.2.7) | 
 | value        | v         | Key Value depending on the key format.\\ The variant signature for different types are shown below.                                                                                                              | 

 | ALLJOYN KeyInfo Record (ayyyv) |                   |                                                           | 
 | ------------------------------ |                   |                                                           | 
 | Field Name                     | Variant Signature | Description                                               | 
 | kid                            | ay                | Key ID.  The identifier of the key.  Usually it is a GUID | 
 | use                            | y                 | Key Usage. Current values \\ 0 -- SIG, 1 -- ENC           | 
 | kty                            | y                 | Key Type. Current values \\ 0 -- ECC                      | 
 | value                          | v                 | Key Type Contents.                                        | 

 | ECC KeyTypeInfo (yyv) |           |                                                             | 
 | --------------------- |           |                                                             | 
 | Field                 | Signature | Description                                                 | 
 | alg                   | y         | ALgorithm to use. Current values: \\ 0 -- ECDSA with SHA256 | 
 | crv                   | y         | The curve ID. Current values: \\ 0 -- NIST P-256            | 
 | value                 | v         | The Curve Contents (parameters and coordinates).            | 

 | NIST P-256 CurveKeyInfo (ayay) |           |                  | 
 | ------------------------------ |           |                  | 
 | Field                          | Signature | Description      | 
 | x-coord                        | ay        | the X coordinate | 
 | y-coord                        | ay        | the Y coordinate | 

### PermissionMgmt::InstallCredential Signature

The InstallCredential is used to install additional credentials like trust anchors to the app.  Future credentials can be supported.

 | InstallCredential yv |           |                                                                                                      | 
 | -------------------- |           |                                                                                                      | 
 | Field                | Signature | Description                                                                                          | 
 | type                 | y         | Credential type.  Current values: \\ 0 -- Trust Anchor                                               | 
 | value                | v         | Credential Value depending on the type.\\ The variant signature for different types are shown below. | 

 | Trust Anchor Record (yv) |                   |                                                                     | 
 | ------------------------ |                   |                                                                     | 
 | Field Name               | Variant Signature | Description                                                         | 
 | use                      | y                 | Usage. Current values \\ 0 -- ANY\\ 1 -- IDENTITY\\ 2 -- MEMBERSHIP | 
 | value                    | v                 | KeyInfo object described above                                      | 

### PermissionMgmt::RemoveCredential Signature

The RemoveCredential is used to remove an existing credential like a trust anchor from the app.  

 | RemoveCredential yv |           |                                                                                                        | 
 | ------------------- |           |                                                                                                        | 
 | Field               | Signature | Description                                                                                            | 
 | type                | y         | Credential type.  Current values: \\ 0 -- Trust Anchor                                                 | 
 | value               | v         | CredentialID value depending on the type.\\ The variant signature for different types are shown below. | 

 | Trust Anchor ID Record (yv) |                   |                                                                     | 
 | --------------------------- |                   |                                                                     | 
 | Field Name                  | Variant Signature | Description                                                         | 
 | use                         | y                 | Usage. Current values \\ 0 -- ANY\\ 1 -- IDENTITY\\ 2 -- MEMBERSHIP | 
 | value                       | v                 | KeyInfo object described above                                      | 
### Certificate Object Signature

The Certificate object is used to represent the certificate.


 | Certificate (yay) |           |                                                                                                                                                                                                | 
 | ----------------- |           |                                                                                                                                                                                                | 
 | Field             | Signature | Description                                                                                                                                                                                    | 
 | encoding          | y         | Data encoding scheme.  Current values: \\ 0 -- ALLJOYN \\ 1 -- JSON Web Key [JWK](https///tools.ietf.org/html/draft-ietf-jose-json-web-key-32#section-3)\\ 2 -- X.509 DER\\ 3 -- X.509 DER PEM | 
 | cert data         | ay        | the certificate data depending on the encoding.                                                                                                                                                | 


### Authorization Data Signature and Field IDs

The functional description on the authorization data is in the HLD in [Security 2.0](core/security_enhancements)

The authorization data begins with a specification version number and the top level data.

The top level of the authorization data is composed the serial number and the list of sections.  Each section is defined by a section ID and a variant representing the section.

 | Authorization Data (yv)               |              |                              |                                                                          | 
 | -----------------------               |              |                              |                                                                          | 
 | Field                                 | Signature    | Description                  |                                                                          | 
 | version                               | y            | specification version number |                                                                          | 
 | Authorization Top Level Data (ua(yv)) |              |                              |                                                                          | 
 | Field                                 | Signature    | Description                  |                                                                          | 
 | serialNumber                          | u            | authorization serial number  |                                                                          | 
 | Section Data a(yv)                    |              |                              |                                                                          | 
 | Section ID                            | Section Name | Variant Signature            | Description                                                              | 
 | 1                                     | admins       | a(yyv)                       | List of admins.  Each admin is represented in a peer record shown below. | 
 | 2                                     | terms        | aa(yv)                       | Permission terms section is composed of a list of terms show below.      | 

 | Peer Record (yyv) |           |                                                                                                                                        | 
 | ----------------- |           |                                                                                                                                        | 
 | Field             | Signature | Description                                                                                                                            | 
 | level             | y         | level of authorization\\ The valid values are:\\ 0 -- NONE\\ 1 -- ENCRYPTED\\ 2 -- AUTHENTICATED\\ 3 -- AUTHORIZED                     | 
 | type              | y         | type of peer.\\ The valid values are:\\ 1 -- ANY\\ 2 -- PEER\\ 3 -- GUILD                                                              | 
 | value             | v         | The GUID.  Depending on the peer type, the value is:\\ ANY -- ay -- empty \\ PEER-- ay -- peer GUID\\ GUILD -- ay -- GUID of the guild | 

 | Term Record a(yv) |            |                   |                                                | 
 | ----------------- |            |                   |                                                | 
 | Field ID          | Field Name | Variant Signature | Description                                    | 
 | 1                 | peers      | a(yyv)            | Peer Information show above.                   | 
 | 2                 | rules      | aa(yv)            | rules.\\ Rule record definition is shown below | 

 | Rule Record a(yv) |            |                   |                                                                            | 
 | ----------------- |            |                   |                                                                            | 
 | Field ID          | Field Name | Variant Signature | Description                                                                | 
 | 1                 | obj        | s                 | object path                                                                | 
 | 2                 | ifn        | s                 | interface name                                                             | 
 | 3                 | mbrs       | a(yv)             | interface members.\\ It's an array of Interface Member records shown below | 

 | Interface Member Record a(yv) |             |                   |                                                                                                                                                                                                                                                                            | 
 | ----------------------------- |             |                   |                                                                                                                                                                                                                                                                            | 
 | Field ID                      | Field Name  | Variant Signature | Description                                                                                                                                                                                                                                                                | 
 | 1                             | mbr         | s                 | member name                                                                                                                                                                                                                                                                | 
 | 2                             | type        | y                 | message type.  Valid values are:\\ M: method call\\ S: signal\\ P: property                                                                                                                                                                                                | 
 | 3                             | action      | y                 | action mask flag.  The list of valid masks:\\ 0x01: Denied\\ 0x02: Provide -- allows to send signal, perform method calls and produce properties\\ 0x04: Observe -- allows to receive signals and get properties\\ 0x08: Modify -- Observe + Set properties + method calls | 
 | 4                             | mutual-auth | b                 | mutual authorization required                                                                                                                                                                                                                                              | 

 | Manifest Record (yv) |            |                   |                                                | 
 | -------------------- |            |                   |                                                | 
 | Field ID             | Field Name | Variant Signature | Description                                    | 
 | 1                    | rules      | aa(yv)            | rules.\\ Rule record definition is shown below | 

### BusAttachment API change

The BusAttchment API will be added with a method call to retrieve the Permission Configurator object.  The PermssionConfigurator object allows the application developer to perform certain configurations for the Permssion Management module.

PermissionConfigurator& BusAttachment::GetPermissionConfigurator();

#### PermissionConfigurator functions

 | Method Name               | Description                                                                                                 | 
 | -----------               | -----------                                                                                                 | 
 | SetPermissionManifest     | Set the permission manifest for the application.                                                            | 
 | GetClaimableState         | Retrieve the claimable state of the application.                                                            | 
 | SetClaimable              | Set the claimable state to be claimable or not.                                                             | 
 | GenerateSigningKeyPair    | Generate the signing key pair and store it in the key store.                                                | 
 | GetSigningPublicKey       | Retrieve the public key info fo the signing key.                                                            | 
 | SignCertificate           | Sign the X509 certificate using the signing key                                                             | 
 | Reset                     | Reset the Permission module by removing all the trust anchors, DSA keys, installed policy and certificates. | 
 | GetConnectedPeerPublicKey | Get the connected peer ECC public key if the connection uses the ECDHE_ECDSA key exchange.                  | 

For more information, please refer the documentation in the PermissionConfigurator.h file.
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
### Newly Proposed Interface Descriptions For IRB Review

*  [For IRB Review Security Interface Descriptions](For IRB Review Security Interface Descriptions) 


