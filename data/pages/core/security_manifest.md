# Application Manifest

When considering where AllSeen enabled applications will run, smartphones are an obvious target. A lot of applications are available in various the app stores. Unfortunately not all of these applications are trustworthy. Example the flashlight app which asked for access to phonebook, network, ... Same as the application is sandboxed on the smartphone, we would like to sandbox applications within the AllSeen security 2.0 context. If I install an AllSeen TV remote control app, then I would like it only to have rights to do TV operations. Nothing more. Since we can't trust the application, we can't assume it will behave properly. So these restrictions must be enforced by the peers. For the RC example, the TV must check the app has permissions.  When remote crontol app tries to open the door, then the door must reject the call.

The main goal of an application manifest is to inform an admin which interfaces an application will produce and consume. Once the admin accepts the manifest, the manifest is signed and installed on the application. The signed manifest will be used to enforce the application can not produce or consume any unwarranted interfaces.

A signed application manifest limits the potential interfaces a malicious application can access within a set of well-behaving applications.

The goal of an application manifest is similar application manifests on Android, in which an end-user has to accept a list of permissions when installing a new application on his phone which are enforced by Android. The implementation is however different, as explained in the sections below.

## Requirements

### Manifest Format

The manifest MUST be expressed at the interface level. It MAY be expressed at the member level, but this is not recommended as this increases the complexity that needs to be handled by the admin.

### Manifest Acceptance

The manifest MUST be presented to the admin in a user-friendly way. As the interface names might not be very informative, they MUST be mapped to a user-friendly description.

The descriptions of the interfaces MUST be trustworthy. As a malicious application can by definition not be trusted, the descriptions MUST be provided by a trusted third party.

The descriptions of the interfaces SHOULD be localized to the admin.

The AllSeen Alliance MUST provide descriptions for any standard AllSeen interface, as reviewed and accepted by the Interface Review Board (IRB).

The application developer MUST provide the descriptions of any application specific interfaces.

If a manifest is defined at the member level, a description for each listed member MUST be available.

### Manifest Enforcement

When an application tries to produce or consume without a signed manifest granting him to do so, the AllSeen framework MUST return an authorization failure error.

The accepted manifest MUST be enforced by the peer application, as a malicious application may not be trusted to enforce it locally.

### Manifest Updates

Whenever an application is updated and does not require additional rights, it MAY still use the previously signed manifest. Only when the update requires additional rights, the admin MUST accept a new manifest for that application.

## Implementation

When an administrator wants to add an application to one of his security groups, he needs to accept a manifest of the application. When he accepts the manifest, its contents will be encoded in a membership certificate.

 1.  The security manager discovers the remote application through the NotifyConfig signal.
 2.  The admin adds the application to one of his security groups.
 3.  The security manager retrieves the manifest of the application.
 4.  The security manager contacts a server to retrieve the human readable description of the interfaces and presents them to the admin.
 5.  The admin accepts (or rejects) the description of the manifest. When the admin rejects the manifest, the application will not receive a membership certificate.
 6.  The security manager encodes the requested (& accepted) permissions in a membership certificate.
 7.  The security manager installs the generated certificate on the application.

{{:core:security_manifest.png?direct&200|}}

### Application

The application developer needs to embed the manifest in his application. There should be a platform specific callback function to retrieve the manifest that belongs to an application. For Android, it could be based on convention, providing the manifest as a file inside the application package. For small embedded devices, the manifest could be part of the application.

To ease the generation of membership certificates by the security manager, the manifest format should line up with the format that is used to express access rules in the membership certificates.

### Interface Description Server

The server serving the descriptions of the interfaces can either be:

 1.  Hosted by the application developer for application specific interfaces. To prevent spoofing attacks, the URL of this server MUST be based on the reverse domain name of the interface name.
 2.  Hosted by the AllSeen Alliance for common AllSeen interfaces. This server MUST be hosted on a predefined URL. This server MUST be contacted over HTTPS.

### Manifest Enforcement 

As the manifests are encoded in the membership certificates, no additional enforcement mechanisms need to be implemented. 

When applying security group specific policy rules, the remote peer will enforce the rules in the membership certificate, effectively enforcing the manifest of the application within that security group.

As no membership certificates can be applied for ANY-USER policy rules, manifests can not be enforced for such policies.

## Discussion

 1.  Introspection XMLs can not be re-used for the purpose of manifests, as they only contains data that is being used by an application at a certain moment in time. An application might use different interfaces depending on its internal state.
 2.  Although granting a subset of the rights requested in the manifest provides some additional flexibility, it would also increase the development cost for every application developer to handle every combination of rights his application might have been granted.
 3.  Instead of encoding the manifest in a membership certificate, it can be encoded in an identity certificate during claiming. This has the advantage that the manifest should only be encoded once for each application instead of once for each security group, and that the manifest can also be applied for ANY-USER policy rules.
 4.  The interface descriptions for non-standard interfaces might be provided by the applications themselves. Such descriptions will need to be signed by one of the trusted AllSeen Certificate Authorities. If their signature can not be verified, they should be clearly marked as being untrustworthy to the admin when accepting the manifest. 
