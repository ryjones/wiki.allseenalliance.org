#  (Unified) AllJoyn Introspection XML

## 1 Introduction
In 15.09 and earlier, there are 3 incompatible introspection XML formats:
 1.  D-Bus introspection XML, as returned from Introspect(), and defined in http://dbus.freedesktop.org/doc/dbus-specification.html#introspection-format.
 2.  Extended introspection XML, which isn’t returned by anything, but which is defined in https://wiki.allseenalliance.org/irb/extended_introspection_xml.  This uses named structs in type signatures, and so is incompatible with D-Bus introspection XML since any code expecting D-Bus introspection XML will treat named structs in type signatures as illegal.
 3.  AllJoyn introspection XML, as returned from IntrospectWithDescription().  Its format is not documented anywhere but in short: it uses D-Bus style type signatures as does (1), but uses the `<description>` element and signal behavior attributes from (2).  As such, it is treated as legal by most tools using D-Bus introspection XML, except ones that do strict validation on elements and attributes. 

This document collapses them into one format going forward, which is D-Bus introspection compatible, in order to maximize use of existing tools and expertise across the industry.

## 2 Scenarios and Requirements

There are multiple scenarios that need to be (or already are, at least in part) solved:

 1.  End users need descriptions of interfaces and their members, for creating If-This-Then-That (IFTTT) style rules as discussed in https://wiki.allseenalliance.org/_media/compliance/alljoyn_events_actions_feature_interface_definition.pdf
 2.  Administrators need descriptions of interfaces and sometimes their members, for doing ACLs (see the discussion of descriptions under “Application Manifest” in https://allseenalliance.org/developers/learn/core/security2_0/hld).  It isn’t stated that the description is obtained in introspection XML format, so that may or may not be the case, because it hasn’t been defined yet.  However, the advantage of using introspection XML is that it avoids gratuitously introducing yet a fourth variation of an interface description format.
 3.  The IRB needs to review interface definitions, including the introspection XML.
 4.  A developer wants to get the official XML for a standard interface, from the Alliance website, for code generation purposes.  In one sense, this is dangerous though: in AllJoyn, the code, not the documentation, is authoritative.  Example: The published Onboarding interface spec is currently wrong and anyone who uses it will fail to interoperate with any device.  Specifically, https://allseenalliance.org/developers/learn/base-services/onboarding/interface says a method is called “ConfigWifi” but the introspection XML section of the same document calls it “ConfigureWifi”, and unfortunately both are wrong.  The code has “ConfigureWiFi” (note the capital F) and the protocol is case-sensitive.   That can be partially mitigated by good IRB review, and by getting ASADOC bugs fixed in a timely fashion, which doesn’t happen today.
 5.  A developer wants to get the actual XML from a device (which may or may not be a proprietary interface) for code generation purposes.   You cannot guarantee the XML will be available anywhere else, and even if it were, you cannot guarantee anything else will interoperate with a device (see the Onboarding existence proof above).

The corollary is that the introspection XML returned by a device at runtime must be complete; it cannot be a subset of the formally published XML on www.allseenalliance.org for any standard interface supported by the device. If it deviates from that, it must be as a superset (e.g., because of vendor-specific annotations that were added as discussed in section 3.6).

### 2.1 Scenarios and Requirements

Code generators (of which at least two AllJoyn-specific ones are currently known to exist [here](devtools/code_generator) and [here](https///msdn.microsoft.com/en-us/library/dn913809.aspx), and some discussion at https://developer.gnome.org/gio/stable/gdbus-codegen.html for D-Bus is also relevant) need to support both scenario 4 and scenario 5.  Today code generation is complicated by the fact that the [extended introspection XML format](irb/extended_introspection_xml) is designed to make code generation easy, but it is not available in scenario 5 today, and for scenario 4, no published interfaces yet use the extended format.   When ones do get published, code generators would need to support multiple incompatible formats.  

The limitation of the formats used today is that structures and members cannot be named, complicating code generation significantly, and making generated code hard to read and maintain.

As such, the requirements are:

 1.  Use a single common format, in order to reduce complexity
 2.  Retain D-Bus compatibility, in order to leverage existing tools and expertise
 3.  Make code generation straightforward

## 3 Interface XML Language

### 3.1 Versioning
For versioning and schema evolution, the unified format uses the “org.gtk.GDBus.Since” annotation, which is defined in http://dbus.freedesktop.org/doc/dbus-api-design.html#annotations and further discussed at https://developer.gnome.org/gio/stable/gdbus-codegen.html.

This annotation can be used on any `<interface>` element to specify the version of the interface.  This annotation can be used on any `<method>`, `<signal>` or `<property>` element to specify the interface version the member first appeared in.   For AllJoyn, the value must be an integer, and each member version must be less than or equal to the interface version.  This annotation can be omitted from all elements in the initial version of an interface, and the default value if omitted is “1”.

Example:

	
	`<interface name="org.alljoyn.example.Test">`
	  `<annotation name="org.gtk.GDBus.Since" value="2"/>`
	  
	  `<!-- Since no annotation exists below, Foo was in version 1. -->`
	  `<property name="Foo" type="s" access="read"/>`
	  
	  <!-- Bar was also in version 1.  This illustrates that it's not an
	       error to have version 1 be explicit, but it's unnecessary. -->
	  `<property name="Bar" type="s" access="read">`
	    `<annotation name="org.gtk.GDBus.Since" value="1"/>`
	  `</property>`
	  
	  `<!-- Baz was added in version 2. -->`
	  `<property name="Baz" type="s" access="read">`
	    `<annotation name="org.gtk.GDBus.Since" value="2"/>`
	  `</property>`
	`</interface>`


### 3.2 Type Signatures

Here is an example of the current Extended Introspection XML format using named types:

	
	`<struct name="ObjectDescription">`
	  `<field name="path" type="o"/>`
	  `<field name="implementedInterfaces" type="as"/>`
	`</struct>`
	
	`<method name="GetObjectDescription">`
	  `<arg name="objectDescription" type="a[ObjectDescription]" direction="out"/>`
	`</method>`
	
	`<dict name="ApplicationMetadata">`
	  `<key type="s"/>`
	  `<value type="v"/>`
	`</dict>`
	
	`<signal name="Announce" sessionless="true">`
	  `<arg name="objectDescription" type="a[ObjectDescription]"/>`
	  `<arg name="metadata" type="[ApplicationMetadata]"/>`
	`</signal>`
	
	`<property name="ObjectDescriptions" type="a[ObjectDescription]" access="read"/>`


As noted earlier, the above type signatures are incompatible with the D-Bus introspection XML format.  The new D-Bus compatible equivalent using annotations would be:

	
	`<annotation name="org.alljoyn.Bus.Struct.ObjectDescription.Field.path.Type" value="o"/>`
	`<annotation name="org.alljoyn.Bus.Struct.ObjectDescription.Field.implementedInterfaces.Type" value="as"/>`
	            
	`<method name="GetObjectDescription">`
	  `<arg name="objectDescription" type="a(sas)" direction="out">`
	    `<annotation name="org.alljoyn.Bus.Type.Name" value="a[ObjectDescription]"/>`
	  `</arg>`
	`</method>`
	
	`<annotation name="org.alljoyn.Bus.Dict.ApplicationMetadata.Key.Type" value="s"/>`
	`<annotation name="org.alljoyn.Bus.Dict.ApplicationMetadata.Value.Type" value="v"/>`
	
	`<signal name="Announce">`
	  `<arg name="objectDescription" type="a(sas)">`
	    `<annotation name="org.alljoyn.Bus.Type.Name" value="a[ObjectDescription]"/>`
	  `</arg>`
	  `<arg name="metaData" type="a{sv}">`
	    `<annotation name="org.alljoyn.Bus.Type.Name" value="[ApplicationMetadata]"/>`
	  `</arg>`
	`</signal>`
	
	`<property name="ObjectDescriptions" type="a(sas)" access="read">`
	  `<annotation name="org.alljoyn.Bus.Type.Name" value="a[ObjectDescription]"/>`
	`</property>`


It is also common for interfaces to define a set of enumerated values, which are modeled as integers with names and explanations of the values as part of the interface description document, not as part of the XML. 
For example, SmartSpaces.Environment.WaterLevel, has XML:

	
	`<property name="SupplySource" type="y" access="read">`
	    `<description language="en">`The supply source of water.`</description>`
	    `<annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>`
	`</property>`

with the following additional text in the document:

	

	  * 0 --- Tank --- water supplied via a tank
	  * 1 --- Pipe --- water supplied via a pipe
	  * 255 --- Not Supported --- no supply source information available


Using annotations in introspection XML, the XML becomes:

	
	`<annotation name="org.alljoyn.Bus.Enum.WaterSupplySource.Value.Tank" value="0"/>`
	`<annotation name="org.alljoyn.Bus.Enum.WaterSupplySource.Value.Pipe" value="1"/>`
	`<annotation name="org.alljoyn.Bus.Enum.WaterSupplySource.Value.NotSupported" value="255"/>`
	`<property name="SupplySource" type="y" access="read">`
	    `<annotation name="org.alljoyn.Bus.Type.Name" value="[WaterSupplySource]"/>`
	    `<annotation name="org.alljoyn.Bus.DocString.En" value="The supply source of water."/>`    
	    `<annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>`
	`</property>`


That is, the following annotation conventions are defined:

*  **org.alljoyn.Bus.Struct.//StructureName//.Field.//fieldName//.Type**: This defines a field named *fieldName* in a structure named *StructureName*, with a type signature given in the value.  The value has the same syntax as currently allowed by [Extended Introspection XML](irb/extended_introspection_xml) types.  The order of fields in the structure is defined by the order in which the annotations appear in the XML.

*  **org.alljoyn.Bus.Type.Name**: This defines the type, using the same syntax as currently allowed by [Extended Introspection XML](irb/extended_introspection_xml) types, of a signal or method argument, or of a property.

*  **org.alljoyn.Bus.Dict.//DictionaryName//.Key.Type**: This defines a dictionary named *DictionaryName*, with a type signature of its key given in the value.  The value has the same syntax as currently allowed by [Extended Introspection XML](irb/extended_introspection_xml) types.

*  **org.alljoyn.Bus.Dict.//DictionaryName//.Value.Type**: This defines the type, using the same syntax as currently allowed by [Extended Introspection XML](irb/extended_introspection_xml) types, of the values in the dictionary named *DictionaryName*.  This annotation must appear after the corresponding org.alljoyn.Bus.Dict.//DictionaryName//.Key.Type annotation.

*  **org.alljoyn.Bus.Enum.//EnumName//.Value.//ValueName//**: This defines an enumeration type named *EnumName* with a value named *ValueName*.  The value is an integer expressed as a string.

Note that since D-Bus introspection XML is case-sensitive, the *fieldName* appears in lowerCamelCase in the interface name so that it will match the actual field name which uses the lowerCamelCase convention.


### 3.3 Descriptions and Comments

All five scenarios need to obtain some descriptions of interfaces and members, whether to display to an end-user or admin, or simply to generate comments in generated code.  However, there are two different audiences, with different requirements:

 1.  End users/administrators (scenarios 1-2) where having descriptions localized into different languages is important, but explanations of low-level implementation details would be confusing.
 2.  Developers (scenarios 3-5) where localized descriptions are less important since Alliance specs for example are available only in English, but explanations of low-level implementation details may be required.

The unified format is as follows:
 1.  End-user accessible descriptions use XML annotations that replace the `<description>` element currently defined by AllJoyn’s [Extended Introspection XML](irb/extended_introspection_xml).   Alliance interfaces require English description elements, and descriptions in other languages are optional.  For security, descriptions (regardless of language) must be verified to come from the organization defining the interface. 
 2.  Additional developer-only details are not localized, and XML `<!-- comment -->` blocks containing gtk-doc formatted text are used as discussed at http://dbus.freedesktop.org/doc/dbus-api-design.html#documentation.   End-user accessible descriptions should not be duplicated in such comments.  That is, developers get both types and comment blocks should only be used for additional details not obvious from the end-user description.
 3.  IntrospectWithDescription() currently returns XML that is not strictly D-Bus compliant.  It should continue to do so for backwards compatibility, but should be deprecated.
 4.  Introspect() should be updated to include all end-user-accessible descriptions as well as developer-only comments.  

For developer-only descriptions, the org.gtk.GDBus.DocString XML annotation is also defined at http://dbus.freedesktop.org/doc/dbus-api-design.html#documentation which explains that `<!—comment -->` blocks are preferred.  As such, AllJoyn need not support org.gtk.GDBus.DocString XML annotations.   Furthermore, that annotation does not support language tags, and hence is not suitable for end-user accessible descriptions either.

For end-user descriptions, the annotation org.alljoyn.Bus.DocString.//LanguageTag// is hereby defined, where *LanguageTag*, is a language tag with any hyphens converted to underscores (as is done with the DNS name prefix).   Example:

	
	`<signal name="LightOn">`
	  `<annotation name="org.alljoyn.Bus.DocString.En" value="Light has been turned on"/>`
	  `<annotation name="org.alljoyn.Bus.DocString.Nl" value="Licht is aangestoken"/>`
	`</signal>`


The security 2.0 subgroup had a long discussion about interface descriptions for scenario 2 (application manifests), and whether those descriptions could come from a device or whether they could only come from a server in the cloud, keeping in mind that sometimes one may not have connectivity to the Internet.  They tentatively concluded that they could only safely come from the cloud, such as from a site maintained by the org identified in the interface prefix.   These same arguments might also apply to scenario 1 (events & actions) descriptions.

### 3.4 Signal Emission Behaviors

The introspection XML format used by IntrospectWithDescription() currently allows specifying the signal emission behavior via XML attributes on the `<signal>` element.   These are not strictly compliant with the D-Bus introspection XML format.  As such, the following annotations are defined for D-Bus compliance, for use in `<signal>` elements.

 | Name                                   | Values (separated by ,) | Description                                                                                                     | 
 | ----                                   | ----------------------- | -----------                                                                                                     | 
 | org.alljoyn.Bus.Signal.Sessionless     | true,false              | Whether or not the signal may be sessionless.  Equivalent to the existing “sessionless” attribute.          | 
 | org.alljoyn.Bus.Signal.Sessioncast     | true,false              | Whether or not the signal may be sessioncast.  Equivalent to the existing “sessioncast” attribute.          | 
 | org.alljoyn.Bus.Signal.Unicast         | true,false              | Whether or not the signal may be unicast.  Equivalent to the existing “unicast” attribute.                  | 
 | org.alljoyn.Bus.Signal.GlobalBroadcast | true,false              | Whether or not the signal may be global broadcast.  Equivalent to the existing “globalbroadcast” attribute. | 

All signal emission behavior annotations have a default value of false.   If all signal emission behaviors have a value of false, the effect is the same as if all had the value of true, which is that any behavior is allowed.

### 3.5 Use of Annotations vs. Const Properties

Constants such as the units, minimum value, and maximum value of a given property are important to be able to communicate to a developer and consume in code (e.g., for a UI) or use at code generation time.

The following AllJoyn-specific optional annotations are defined:

*  org.alljoyn.Bus.Type.Min: Value is a number expressed as a string

*  org.alljoyn.Bus.Type.Max: Value is a number expressed as a string

*  org.alljoyn.Bus.Type.Units: Value is a string suitable for display

*  org.alljoyn.Bus.Type.Default: Value is a string containing the default value expressed as a string. The default value is defined as the value of the object when created or reset, and not explicitly set to a value by any other means.   This annotation should only be used on readwrite properties, and has the same meaning as the DEFVAL clause defined in [RFC 2578 section 7.9](http://tools.ietf.org/html/rfc2578#section-7.9).

*  org.alljoyn.Bus.Type.Reference: Value is a string suitable for display, containing a cross-reference to some other document, usually one that defines the meaning or values of a property or argument.  This annotation has the same meaning as the REFERENCE clause defined in [RFC 2579 section 3.4](http://tools.ietf.org/html/rfc2579#section-3.4). In the past, references have instead appeared embedded in descriptions or comments (see section 3.3), and this annotation allows them to be explicit.

*  org.alljoyn.Bus.Type.DisplayHint: Value is a string giving a hint as to how a value should be displayed.  This annotation has the same meaning and syntax as the DISPLAY-HINT clause defined in  [RFC 2579 section 3.1](http://tools.ietf.org/html/rfc2579#section-3.1).  The annotation is only a hint, and implementations that do not understand this annotation can ignore it.

If the constant is defined by the interface and it must be the same for every device and implementation of that interface, then use an annotation.   This is because annotations are not per-device and can be cached and applied to any device.  Example:

	
	`<property name="WaterTemperature" type="u" access="readwrite">`
	  `<annotation name="org.alljoyn.Bus.Type.Min" value="0"/>`
	  `<annotation name="org.alljoyn.Bus.Type.Max" value="100"/>`
	  `<annotation name="org.alljoyn.Bus.Type.Units" value="degrees Celsius"/>`
	  ...
	`</property>`


If the constant can vary by implementation or by device, then use a const property, since these are cached on a per-device basis.  (Note that "const" is not supported until release 16.04 so use "true" in the meantime and chaneg to "const" when it is ready.)  Example:

	
	`<property name="Temperature" type="u" access="readwrite">`
	  ...
	`</property>`
	`<property name="MaxTemperature" type="u" access="read">`
	  `<annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="const"/>`
	  ...
	`</property>`


### 3.6 Custom Annotations

Only D-Bus and AllJoyn standard annotations may appear in “official” XMLs that are published by the AllSeen Alliance.  Vendors free to add their own annotations in introspection XML (including XML for AllJoyn standard interfaces) returned at runtime by devices, or in XMLs posted on their own servers.

Any tool that parses XML must be able to cope with unknown annotations anyway, for reasons of forward compatibility.

Custom annotation names must follow the same guidelines as for interface names and error names.

### 3.7 Schema Namespace

The `<node>` element in the introspection XML should point to the XSD as in the example below.

	
	`<node name="/SomePath" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.allseenalliance.org/schemas/introspect" xsi:schemaLocation="http://www.allseenalliance.org/schemas/introspect.xsd">`

## Appendix A: Migration Process

The following items are needed to phase in the use of the unified format.
 1.  DONE: Update the [draft v1.1 IRB guidelines](irb/interface_design_guidelines_draft_1.1) to use the new XML format.
 2.  Write a tool to convert XML in one of the old formats into the new format.  This will assist in migration and isn’t blocked on anything else.
 3.  SCL/TCL code: Update (for 16.04) the SCL/TCL code to use the new format in what Introspect() returns and what APIs like BusAttachment.CreateInterfacesFromXml accept.
 4.  Update other tools like ajxmlcop and codegen utilities to accept the new format.   This includes updating http://www.allseenalliance.org/schemas/introspect.xsd
 5.  XML submitted for IRB review: Start requiring that new XML submitted to the IRB use the new format. Any submissions already in progress can either be kept as is, or politely asked to use the new format.
 6.  The TSC should ideally direct that existing published specs on the Alliance site that use a deprecated format (e.g., the Events & Actions interface spec) should be updated.

