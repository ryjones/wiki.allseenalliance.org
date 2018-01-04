# Deprecated

The document you are viewing is the draft 1.0 version of the Interface Design Guidelines. It is no longer maintained, and slowly getting out of date. It is preserved on the wiki for historical purposes, the discussion at the bottom of the individual subpages may still be of some relevance.

The officially approved current version of the Interface Design Guidelines is at all times linked from the [IRB home page](/interfacereviewboard).

# Interface Design Guidelines

The list of rules and recommendations comes first, for your easy reference. The remainder of the document elaborates on the rules and recommendations, providing the reader some context and further insights.

## Rules and Recommendations

List of all the rules comes here.FIXME((TODO: add a summary (preferably done automatically) of all the rules stipulated below.))

## Specification Format

All Interfaces must be specified in a document following the [Service Framework Interface Definition Template](https///git.allseenalliance.org/cgit/interfaces.git/tree/extra/interface-definition-template.md).
## Cosmetic Guidelines

This section provides pointers for the more superficial aspects of Interface design, like naming, spelling and capitalization.

### Language-related Guidelines

[guidelines here](Language-related Guidelines)

### Naming Conventions

[guidelines here](Naming Conventions)
### Interface Definition XML Language

[guidelines here](Interface Definition XML Language)

~~DISCUSSION~~
## Modeling Style

This section discusses a number of high-level stylistic guidelines.

### Make Interface Definitions Explicit

[guidelines here](Make Interface Definitions Explicit)

### Do Not Reinvent the Wheel

> **Do not repeat information or functionality that is already available in some other Interface. Rather, reuse that Interface.**

Similarly, add information or functionality into the Interface where it makes the most sense.
### Interface and Object Granularity

[guidelines here](Interface-Object Granularity)


### Use of Methods and Properties

[guidelines here](Use of Methods-Properties)


### Use of Signals

[guidelines here](Use of Signals)

### Avoid Dependencies on Session Ports

Interfaces should use ephemeral session ports that can be dynamically discovered.
As such, an interface specification does not need to mention them.

## Common Patterns

This section covers commonly occurring patterns in Interface definitions. It offers standardized suggestions for these common patterns.

### Units

[guidelines here](Physical Units)


## Designing for Evolution

Inevitably, standardized Interfaces will evolve over time. This section provides some insights in the do's and don'ts of Interface evolution.
At this moment, there is no clear architectural vision around Interface Evolution, so this section is, by necessity, rather bare.

[discussion and guidelines](Designing for Evolution)

## Designing for Security

*This section will provide detailed guidelines about designing Interfaces with security (in particular, Security 2.0) in mind. The recommendations here should come from the Security Committee rather than the Interface Review Board. We're just adding them here because it makes sense to keep all Interface-related guidelines in one place, and because the Interface Review Board reviews will take these guidelines into account as well.*

Make sure that any information that is privacy sensitive is secured, not sent in the clear.
## Appendix: Purpose and Scope

### Purpose

This document provides guidelines to designers of AllJoyn Interfaces. These guidelines serve as the basis for the Interface reviews organized by the AllSeen Alliance's Interface Review Board in the context of Interface standardization efforts.

Designers of Interfaces that are not intended to be standardized are still encouraged to adhere to the guidelines specified in this document. This ensures a minimum quality and stylistic homogeneity over all defined Interfaces.

### Scope

This document is intended for software and system engineers that are involved in the definition of AllJoyn Interfaces. It assumes familiarity with the AllJoyn concepts of Interface, Method, Signal and Property.

### References


*  [DBUS] [D-Bus Introspection Format Specification](http://dbus.freedesktop.org/doc/dbus-specification.html#introspection-format)

*  [EIX] [Extended Introspection XML Language](https///wiki.allseenalliance.org/irb/extended_introspection_xml)

*  [EIXS] [Extended Introspection XML Schema](https///wiki.allseenalliance.org/irb/extended_introspection_xml#schema_definition)

*  [GLOS] [AllJoyn Glossary](https///allseenalliance.org/developers/learn/glossary)

*  [IDT] [Interface Definition template](https///git.allseenalliance.org/cgit/interfaces.git/tree/extra/interface-definition-template.md)

*  [RFC] [RFC Editor Abbreviation List](http://www.rfc-editor.org/rfc-style-guide/abbrev.expansion.txt)

*  [SI] [SI system of measurement units](http://www.bipm.org/en/measurement-units/)
### Acronyms and terms

 | **Term**                   | **Definition**                                                                                                                                                                                                                                                                                 | 
 | --------                   | --------------                                                                                                                                                                                                                                                                                 | 
 | AllJoyn service frameworks | A collection of full-feature implementations using the AllJoyn framework that provides specific functionality.  These are building blocks can be combined together to build interoperable devices and applications.                                                                            | 
 | UpperCamelCase             | A naming convention in which a name is formed of multiple words that are joined together as a single word with the first letter of each of the multiple words capitalized so that each word that makes up the name can easily be read. This convention is also sometimes known as Pascal case. | 
 | lowerCamelCase             | A naming convention like UpperCamelCase except that the first letter of the first word is lower case.                                                                                                                                                                                          | 



~~DISCUSSION~~
