# The Extended Introspection XML Format

The Extended Introspection XML format is an evolution of the classic Introspection XML format that aims to do away with a number of ambiguities in the classic format. This format is better suited as input for code generators, and strives to provide a clearer definition of the Interface semantics that relies less on external documentation. The format is accepted as input by the Allseen Alliance code generator (the ''devtools/codegen'' project). A subset of this format is used as output of the ''org.allseen.Introspectable.Introspect'' method.

## Overview

The Extended Introspection XML format is a superset of the DBus Introspection XML format as defined by the [D-Bus Specification](http://dbus.freedesktop.org/doc/dbus-specification.html#introspection-format).

This document will focus on the extensions, rather than repeating the information that is already captured in the DBus specification.

The following extensions are defined:

*  human-readable descriptions with the `<description>` element

*  signal type specification with the ''sessionless'' attribute

*  named types (structures and dictionaries)

## The `<description>` element

All XML elements (`<node>`, `<interface>`, `<method>`, ...) support a sub-element `<description>`.
The description element allows for a human-readable description to be added to the Introspection XML. The description element has a single (optional) attribute ''language'' that specifies the language of the description as an IETF language tag (e.g. "en" for English, "es" for Spanish).

A single element may have multiple `<description>` children, for different languages.

For example:

	:::xml
	`<xml>`
	   `<node name="org/alljoyn/Bus/sample">`
	      `<description language="en">`This is a sample object`</description>`
	      `<interface name="org.alljoyn.bus.sample">`
	         `<description language="en">`This is a sample interface`</description>`
	 
	          `<method name="Concatenate">`
	            `<description>`This concatenates strings`</description>`
	            `<arg name="str1" type="s" direction="in"/>`
	            `<arg name="str2" type="s" direction="in"/>`
	            `<arg name="outStr" type="s" direction="out">`
	               `<description>`The concatenated string`</description>`
	            `</arg>`
	         `</method>`
	      `</interface>`
	   `</node>`
	`</xml>`


## Signal Type Specification

The optional ''sessionless'' attribute of the `<signal>` tag lets you specify whether a signal is expected to be emitted as a sessionless signal or as a regular signal. If the attribute is not specified, it defaults to ''false''.

For example:

	:::xml
	      `<signal name="LightOn" sessionless="true">`
	         `<description>`The light has been turned on`</description>`
	      `</signal>`


> **Note**: there are actually more signal types than just "sessionless" and "non-sessionless". In addition to *sessionless*, the following signal types exist: *unicast*, *sessioncast*, *local broadcast* and *global broadcast*. The Extended Introspection XML format today does not yet allow for the exact specification of these other signal types, but such an extension is planned for the future.

## Named Types

The Extended Introspection XML format allows for a better description of the types of complex properties and arguments. In the standard DBus introspection format, these complex types are represented simply by their signatures. These define the shape of the data type, but offer no additional information about type names and relations or field names.

### Example

The About Interface DBus Introspection XML description includes the following fragment:

	:::xml
	`<method name="GetObjectDescription">`
	  `<arg name="objectDescription" type="a(oas)" direction="out"/>`
	`</method>`
	`<signal name="Announce">`
	  `<!-- ... some args not relevant to this discussion -->`
	  `<arg name="objectDescription" type="a(oas)"/>`
	`</signal>`


In the Extended Introspection XML format, the same interface can be described as follows:

	:::xml
	`<struct name="ObjectDescription">`
	  `<field name="path" type="o"/>`
	  `<field name="interfaces" type="as"/>`
	`</struct>`
	`<method name="GetObjectDescription">`
	  `<arg name="objectDescription" type="a[ObjectDescription]" direction="out"/>`
	`</method>`
	`<signal name="Announce">`
	  `<!-- ... some args not relevant to this discussion -->`
	  `<arg name="objectDescription" type="a[ObjectDescription]"/>`
	`</signal>`


This extended format has several advantages.

Firstly, it allows the code generator to construct properly named language structures for each of the complex types defined in the interface. For example, in C the code generator would produce something like the following:

	:::c
	typedef struct {
	  char *path;
	  char **interfaces;
	} org_alljoyn_About_ObjectDescription_t;
	typedef struct {
	  org_alljoyn_About_ObjectDescription_t *objectDescription;
	} org_alljoyn_About_GetObjectDescription_outargs_t;


Secondly, the interface description becomes more descriptive:

*  It is now clear what each of the fields in the ''(oas)'' struct represent

*  It is officially stated (as opposed to just suggested) that ''GetObjectDescription'' and the ''Announce'' signal return the same kind of data structure representing the same kind of data, and not just two structures that are superficially similar but may contain entirely different kinds of information.

### Type Name References in Signatures

To refer to a named type in a property or argument signature, simply include the declared type name surrounded by square brackets.

For example,

	:::xml
	`<arg name="objectDescription" type="a[ObjectDescription]" direction="out"/>`

declares the type of the objectDescription argument to be "array of ObjectDescription", where ObjectDescription is a named struct defined in the same interface.

> **Note**: you cannot mix "flat" and "extended" signatures: a signature like ''([Foo][Bar]s)'' (a struct with a field of type Foo, one of type Bar and one of type string) is illegal.

### Named Structs

A named struct is the replacement for the flat structure signatures. It consists of a `<struct>` element with a mandatory ''name'' attribute. The `<struct>` element must have at least one child element of type `<field>`. Fields have two mandatory attributes: ''name'' defines the name of the field, and ''type'' defines the signature of the struct field. It is not possible to nest struct definitions.

For example, the struct ''(ios(ii))'' might be expanded to:

	:::xml
	`<struct name="Inner">`
	  `<field name="first" type="i"/>`
	  `<field namd="second" type="i"/>`
	`</struct>`
	`<struct name="Outer">`
	  `<field name="number" type="i"/>`
	  `<field name="path" type="o"/>`
	  `<field name="description" type="s"/>`
	  `<field name="nested" type="[Inner]"/>`
	`</struct>`


### Named Dictionaries

Named dictionaries are similar to named structs. They replace the ''a{..}'' signatures from the DBus Introspection XML. The syntax is simple: there is a `<dict>` element with a mandatory ''name'' attribute, and two mandatory child elements: `<key>` and `<value>`. The key and value elements each have a mandatory ''type'' attribute, but no ''name'' attribute. The signature of the dictionary key must be a simple (e.g. ''i'', ''u'', ''s'', ...) type.

For example, an ''a{s(ii)}'' dictionary might be represented as follows:

	:::xml
	`<struct name="Inner">`
	  `<field name="first" type="i"/>`
	  `<field name="second" type="i"/>`
	`</struct>`
	`<dict name="StringToInts">`
	  `<key type="s"/>`
	  `<value type="[Inner]"/>`
	`</dict>`


## Schema Definition

`<file xml extended-introspection.xsd>`
`<?xml version="1.0" encoding="UTF-8" standalone="no"?>`
`<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">`

    <!-- 

	     *******************************************************
	     *                                                     *
	     *               Attribute Definitions                 *
	     *                                                     *
	     *******************************************************
	-->
	
	<xs:attribute name="name" type="xs:string"/>

	<xs:attribute name="access">
		<xs:simpleType>
			<xs:restriction base="xs:string">
				<xs:enumeration value="read"/>
				<xs:enumeration value="write"/>
				<xs:enumeration value="readwrite"/>
			</xs:restriction>
		</xs:simpleType>
	</xs:attribute>

    `<xs:attribute name="sessionless">`
        `<xs:simpleType>`
            `<xs:restriction base="xs:string">`
                `<xs:enumeration value="true"/>`
                `<xs:enumeration value="false"/>`
            `</xs:restriction>`
        `</xs:simpleType>`
    `</xs:attribute>`
    
    <!-- 

	     *******************************************************
	     *                                                     *
	     *               Type Definitions                      *
	     *                                                     *
	     *******************************************************
	-->

	<xs:simpleType name="arg_direction">
		<xs:restriction base="xs:string">
			<xs:enumeration value="in"/>
			<xs:enumeration value="out"/>
			<!--  unset is used by the app as metadata. -->
			<xs:enumeration value="unset"/>
		</xs:restriction>
	</xs:simpleType>
	
        `<xs:simpleType name="dictionary_key_type">`
                `<!-- dictionary key types are always simple types -->`
                `<xs:restriction base="xs:string">`
                        `<xs:pattern value="[ybnqiuxtdso]"/>`
                `</xs:restriction>`
        `</xs:simpleType>`

        `<xs:simpleType name="field_type">`
                <!-- field types can only be non-flattened.
                     Conceptually, the pattern looks like this:
                     a*(`<basic type>`|`<[NamedTypeReference]>`)
                  -->
                `<xs:restriction base="xs:string">`
                        `<xs:pattern value="a*([ybnqiuxtdsogv]|\[\w+\])"/>`
                        `<xs:minLength value="1"/>`
                `</xs:restriction>`
        `</xs:simpleType>`

        `<xs:simpleType name="arg_and_property_type">`
                <!-- arg and property types can be flattened or non-flattened.
                     Non-flattened looks like this (see field_type):
                     a*(`<basic type>`|`<[NamedTypeReference]>`)
                     Flattened looks like this:
                     [ybnqiuxtdsogav\{\}\(\)]*
                     Note that the a`<basic type>` branch of non-flattened is trivially
                     covered by the flattened pattern, so we don't have to specify it separately.
                  -->
                `<xs:restriction base="xs:string">`
                        `<xs:pattern value="([ybnqiuxtdsogav\{\}\(\)]*)|(a*\[\w+\])"/>`
                        `<xs:minLength value="1"/>`
                `</xs:restriction>`
        `</xs:simpleType>`

	<xs:complexType name="arg_type">
		<xs:sequence>
			<xs:element maxOccurs="unbounded" minOccurs="0" ref="annotation"/>
			<xs:element maxOccurs="unbounded" minOccurs="0" ref="description"/>
		</xs:sequence>
		<xs:attribute ref="name"/>
		<xs:attribute name="type" type="arg_and_property_type" use="required"/>
		<xs:attribute default="unset" name="direction" type="arg_direction"/>
	</xs:complexType>

	<xs:complexType name="nested_node">
		<xs:choice maxOccurs="unbounded" minOccurs="1">
			<xs:element maxOccurs="unbounded" ref="interface"/>
			<xs:element maxOccurs="unbounded" name="node" type="nested_node"/>
		</xs:choice>
		<xs:attribute ref="name" use="required"/>
	</xs:complexType>

	<!-- 

	     *******************************************************
	     *                                                     *
	     *               Element Definitions                   *
	     *                                                     *
	     *******************************************************
	-->

	<xs:element name="description">
		<xs:complexType mixed="true">
			<xs:sequence>
				<xs:any maxOccurs="unbounded" minOccurs="0" namespace="##any" processContents="skip"/>
			</xs:sequence>
                        `<xs:attribute name="language" type="xs:string" use="optional"/>`
		</xs:complexType>
	</xs:element>

	
	<xs:element name="annotation">
		<xs:complexType>
			<xs:attribute name="name" type="xs:string" use="required"/>
			<xs:attribute name="value" type="xs:string" use="required"/>
		</xs:complexType>
	</xs:element>
	
	<xs:element name="signal">
		<xs:complexType>
			<xs:choice maxOccurs="unbounded" minOccurs="0">
				<xs:element maxOccurs="unbounded" minOccurs="0" ref="description"/>
				<xs:element maxOccurs="unbounded" minOccurs="0" name="arg" type="arg_type"/>
				<xs:element maxOccurs="unbounded" minOccurs="0" ref="annotation"/>
			</xs:choice>
			<xs:attribute ref="name" use="required"/>
            `<xs:attribute ref="sessionless" use="optional"/>`
		</xs:complexType>
	</xs:element>
	
	<xs:element name="method">
		<xs:complexType>
			<xs:choice maxOccurs="unbounded" minOccurs="0">
				<xs:element maxOccurs="unbounded" minOccurs="0" ref="description"/>
				<xs:element maxOccurs="unbounded" minOccurs="0" ref="annotation"/>
				<xs:element maxOccurs="unbounded" minOccurs="0" name="arg" type="arg_type"/>
			</xs:choice>
			<xs:attribute ref="name" use="required"/>
		</xs:complexType>
	</xs:element>

	<xs:element name="property">
		<xs:complexType>
			<xs:sequence>
				<xs:element maxOccurs="unbounded" minOccurs="0" ref="annotation"/>
				<xs:element maxOccurs="unbounded" minOccurs="0" ref="description"/>
			</xs:sequence>
			<xs:attribute ref="name" use="required"/>
			<xs:attribute name="type" type="arg_and_property_type" use="required"/>
			<xs:attribute ref="access" use="required"/>
		</xs:complexType>
	</xs:element>


	<xs:element name="struct">
		<xs:complexType>
			<xs:sequence>
                                `<xs:element maxOccurs="unbounded" minOccurs="0" ref="annotation"/>`
                                `<xs:element name="field" minOccurs="1" maxOccurs="unbounded">`
                                        `<xs:complexType>`
                                                `<xs:sequence>`
                                                        `<xs:element maxOccurs="unbounded" minOccurs="0" ref="annotation"/>`
                                                `</xs:sequence>`
                                                `<xs:attribute ref="name" use="required"/>`
                                                `<xs:attribute name="type" type="field_type" use="required"/>`
                                        `</xs:complexType>`
                                `</xs:element>`
			</xs:sequence>
			<xs:attribute ref="name" use="required"/>
		</xs:complexType>
	</xs:element>

	<xs:element name="dict">
		<xs:complexType>
			<xs:sequence>
				<xs:element maxOccurs="unbounded" minOccurs="0" ref="annotation"/>
                                `<xs:element name="key" minOccurs="1" maxOccurs="1">`
                                        `<xs:complexType>`
                                                `<xs:sequence>`
                                                        `<xs:element maxOccurs="unbounded" minOccurs="0" ref="annotation"/>`
                                                `</xs:sequence>`
                                                `<xs:attribute name="type" type="dictionary_key_type" use="required"/>`
                                        `</xs:complexType>`
                                `</xs:element>`
                                `<xs:element name="value" minOccurs="1" maxOccurs="1">`
                                        `<xs:complexType>`
                                                `<xs:sequence>`
                                                        `<xs:element maxOccurs="unbounded" minOccurs="0" ref="annotation"/>`
                                                `</xs:sequence>`
                                                `<xs:attribute name="type" type="field_type" use="required"/>`
                                        `</xs:complexType>`
                                `</xs:element>`
			</xs:sequence>
			<xs:attribute ref="name" use="required"/>
		</xs:complexType>
	</xs:element>


	<xs:element name="interface">
		<xs:complexType>
			<xs:sequence>
				<xs:element maxOccurs="unbounded" minOccurs="0" ref="annotation"/>
				<xs:element maxOccurs="unbounded" minOccurs="0" ref="description"/>
				<xs:choice>
					<xs:element ref="method"/>
					<xs:element ref="signal"/>
					<xs:element ref="property"/>
					<xs:element ref="struct"/>
					<xs:element ref="dict"/>
				</xs:choice>
				<xs:choice maxOccurs="unbounded" minOccurs="0">
					<xs:element ref="annotation"/>
					<xs:element ref="method"/>
					<xs:element ref="signal"/>
					<xs:element ref="property"/>
					<xs:element ref="struct"/>
					<xs:element ref="dict"/>
				</xs:choice>
			</xs:sequence>
			<xs:attribute ref="name" use="required"/>
		</xs:complexType>
	</xs:element>

	<xs:element name="node">
		<xs:complexType>
			<xs:sequence>
				<xs:element maxOccurs="unbounded" minOccurs="0" ref="description"/>
				<xs:choice maxOccurs="unbounded" minOccurs="1">
					<xs:element maxOccurs="unbounded" ref="interface"/>
					<xs:element maxOccurs="unbounded" name="node" type="nested_node"/>
				</xs:choice>
			</xs:sequence>
			<xs:attribute ref="name"/>
		</xs:complexType>
	</xs:element>

`</xs:schema>`
`</file>`

