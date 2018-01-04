# Deprecated

The document you are viewing is the draft 1.0 version of the Interface Design Guidelines. It is no longer maintained, and slowly getting out of date. It is preserved on the wiki for historical purposes, the discussion at the bottom of the individual subpages may still be of some relevance.

The officially approved current version of the Interface Design Guidelines is at all times linked from the [IRB home page](/interfacereviewboard).

### Naming Conventions

As AllJoyn Interfaces are closely related to DBus Interfaces, we adopt the DBus naming conventions.
For all names, restrict yourself to alphanumeric characters (A-Z, a-z, 0-9). In some cases, which will be explicitly indicated, underscores ('_') and dots ('.') will also be allowed.

#### Interface Names

Interface names consist of multiple components separated by the dot ('.') character. Individual components may only consist of alphanumeric characters (A-Z, a-z, 0-9) and underscores ('_'). Components must not start with a numeric character.

++++ Interface names start with a reversed DNS domain name |
The reversed DNS part of the name shall be in lower case, with any characters (such as hyphens) not valid in interface names converted to underscores. The subsequent parts of an interface name use UpperCamelCase.

Examples:

*  example.com -> ''com.example.Foo.Bar''

*  example-2.com -> ''com.example_2.Foo.Bar''
++++

++++ Official AllSeen Alliance names must start with ''org.allseen'' |
Despite the fact that the official Internet address for the AllSeen Alliance being ''allseenalliance.org'', the AllSeen Alliance also owns ''allseen.org'' and this shorter form will be used for interface names.
++++

++++ Proprietary (i.e., non-standardized) Interfaces must not use the ''org.allseen'' prefix |
The are expected to use the reversed DNS name of the organization that defined the non-standardized interface.
++++

++++ Newly proposed Interface names must respect the existing Interface hierarchy |

For example, if the namespace ''org.allseen.Sensors'' exists, a proposed humidity sensor Interface definition must use ''org.allseen.Sensors.Humidity'' and not something like ''org.allseen.Humidity.Sensor''.
++++

#### Member Names

++++ Member (property, signal and method) names must use UpperCamelCase notation without punctuation |
They must start with a letter, and consist solely of alphanumeric characters.
++++

++++ Property names should be nouns or predicates |
For example: ''Location'', ''IsOpen''
++++

++++ Method names should start with a verb |
For example: ''Open'' or ''SetColor''
++++

++++ Signal names should describe the event they represent |
Typically, the name of a signal should be phrased in terms of past tense (past participle form), as an event normally describes something that just happened.  For example: ''ItemsChanged''
++++

#### Argument Names

++++ Method and signal argument names must use lowerCamelCase notation without punctuation |
This helps distinguish methods and signals from their parameters.
++++

++++ All method and signal arguments, both input arguments and output arguments, must have a descriptive name |
This helps users of the interface understand what the parameter is for.
++++

#### Object Paths

The features of a valid object path are described in the [D-Bus specification](http://dbus.freedesktop.org/doc/dbus-specification.html). In a nutshell, a path is a sequence of components (consisting of only alphanumerics and underscores) separated by the slash ('/') character. Paths always begin with a slash character.

It is common to let object paths start with a reversed domain name. Obviously, that reversed domain name should be the same as the one used in at least one of the Interfaces implemented by that object.

In rare cases, it may make sense to standardize the path of the object that implements the interface at hand. This is really only appropriate if the object in question is by definition a singleton, and even then its actual path can easily be discovered via the About feature.

++++ The reversed domain name part of an object path should use lowercase notation, the rest of the object path should use UpperCamelCase notation |

For example: ''/org/allseen/Singletons/Foo''
++++

#### Error Names

Error names follow by and large the same rules as Interface names. It is customary for the next-to-last component of the error name to be ''Error''.

++++ Error names start with a reversed DNS domain name, in lower case. The subsequent parts of an error name use UpperCamelCase. The next-to-last part of the error name should be ''Error'' |

For example: ''org.allseen.Lighting.Error.BulbIsBroken''
++++

#### Type and Field Names

When using the [Extended Introspection XML format](irb/extended_introspection_xml)[EIX] for the [Interface definition](irb/interface_definition_xml_language), the Interface designer has the option to describe structs and dictionaries used in member signatures in more detail by defining a named type.

++++ Type names (for named types) must use UpperCamelCase notation without punctuation |
Like interface members, they must start with a letter, and consist solely of alphanumeric characters.**
++++

++++ Field names in named structs must use lowerCamelCase notation without punctuation |
Again, this is to distinguish between struct's named type from the elements of the struct.
++++

~~DISCUSSION~~
