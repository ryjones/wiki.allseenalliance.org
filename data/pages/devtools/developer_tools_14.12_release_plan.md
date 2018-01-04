# Developer Tools 14.12 Release Plan

## Introduction

//[List the working group developer and QA leads for this release cycle.]//

## Themes and Priorities

//[New features, architecture changes, expected improvements.]//
### Code Generator

Support for two new platforms have been added. These are:


*  Android

*  Data Driven API
#### Android

The -t (and --target-language) flag supports "android".
This will produce complete Eclipse Android projects for both the client and
the server. The user interface on both the client and server devices is a
simple scrolling text box with both sides reporting the values received from
the other device. This closely resembles the user interface of the code
generated for the Thin Core Library.
#### Data Driven API

The -t (and --target-language) flag 'ddcpp' supports the Data Driven C++ API.
This will produce interface code for both the data consumer (client) and the
data provider (server).
#### Thin Core Library

Support for Thin Core Library (--target-language flag 'tl') has been upgraded
to match the current version of Thin Core Library.
#### Named Types

Support has been added for named structures and dictionaries.  In the
interface XML file it is now possible to define a 'struct' or 'dict' with a
predefined name for later use and reuse.  The generated code for named types
will use those names.  An example:

	:::xml
	`<interface name="com.example.MyObject">`
	  `<dict name="NamedDict">`
	    `<key type="s"/>`
	    `<value type="i"/>`
	  `</dict>`
	  `<struct name="NamedStruct">`
	    `<field name="intField" type="i"/>`
	  `</struct>`
	  `<method name="some_method">`
	    `<arg name="first_arg" type="[NamedStruct]" direction="in"/>`
	    `<arg name="second_arg" type="[NamedDict]" direction="out"/>`
	  `</method>`
	`</interface>`

#### Usage

For more information on how to use the code generator see the
[AllJoyn Code Generator Wiki](https///wiki.allseenalliance.org/devtools/code_generator)
### Wireshark

The Wireshark AllJoyn dissector has been upgraded to support the AllJoyn
Reliable Data Protocol (ARDP). This is available directly from Wireshark
in [development release](https///www.wireshark.org/download.html#development_release)1.99.1 or later.

## Deliverables

//[Which of this work group's projects are involved in the release.]//

## Milestones

 | Milestone              | Date       | Details                              | 
 | ---------              | ----       | -------                              | 
 | API Freeze             | 2014/12/19 | General freeze or specific API names | 
 | Feature Freeze         | 2014/12/19 |                                      | 
 | Documentation Complete | 2015/01/16 | complete                             | 
 | QA Complete            | 2015/01/16 | complete                             | 


## Expected Work Group Dependencies

//[List projects from other work groups that may be impacted by expected changes during this release cycle.]//

There are no known impacts on other work groups from the expected changes in the tools.

## Compatibility with Previous Releases

//[Explain changes to protocols or APIs that will impact interoperation or applications.]//

### Code Generator

Thin Core Library code produced by the version 14.12 code generator will not work with Thin Core Library version 14.06. Some minor changes in the generated code will be required to get it to compile.

