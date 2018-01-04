# Interface Design Guidelines v1.0

This version of the Guidelines document was approved by the TSC on 2015-02-24.

This document provides guidelines to designers of AllJoyn Interfaces. These guidelines serve as the basis for the Interface reviews organized by the AllSeen Alliance's Interface Review Board in the context of Interface standardization efforts.

Designers of Interfaces that are not intended to be standardized are still encouraged to adhere to the guidelines specified in this document. This ensures a minimum quality and stylistic homogeneity over all defined Interfaces.
## Specification Format

All Interfaces must be specified in a document following the [Service Framework Interface Definition Template](https///git.allseenalliance.org/cgit/interfaces.git/tree/extra/interface-definition-template.md).

## Cosmetic Guidelines

This section provides pointers for the more superficial aspects of Interface design, like naming, spelling and capitalization.


### Language-related Guidelines

> **Use English words for identifiers**

Always use U.S. English spelling when there are different ways to spell a word.

For example:

*  Use *caliber* instead of *calibre*
*  Use *license* instead of *licence*


> **Only use abbreviations and acronyms in type or member names if they are widely understood and commonly used**

It's perfectly fine to use HTML or id (short for "identity"), but don't use "temp" instead of "temperature".  One source for determining whether an abbreviation or acronym is "widely understood" is if it is listed in the [RFC Editor Abbreviations List](http://www.rfc-editor.org/rfc-style-guide/abbrev.expansion.txt) with an asterisk.


> **In UpperCamelCase and lowerCamelCase identifiers, capitalize acronyms and initializers as if they were regular words**

Often, type or member names will include some kind of acronym or initialism (HTML file, DB connection, IP address, ...). The convention is to treat these as "regular" words, and hence capitalize only the first letter of the word.
Hence,

*  *HtmlFile* instead of *HTMLFile*
*  *DbConnection* instead of *DBConnection*
*  *IpAddress* instead of *IPAddress*


> **Use Consistent Terminology**

Don't use multiple terms for the same concept.  If a term is defined in the [AllJoyn glossary](https///allseenalliance.org/developers/learn/glossary)[GLOS], use it rather than a different synonym.  (For example, use "producer" not "provider".)


> **Use names that describe actors and not acts**

Consider the following statements:

*  A road construction object implements a *paver*, not a *pavement*.

*  A list object implements a *container*, not a *containment*.

*  An object that manages a resource implements a *manager*, not a *management*.

### Naming Conventions

As AllJoyn Interfaces are closely related to DBus Interfaces, we adopt the DBus naming conventions.
For all names, restrict yourself to alphanumeric characters (A-Z, a-z, 0-9). In some cases, which will be explicitly indicated, underscores ('_') and dots ('.') will also be allowed.

#### Interface Names

Interface names consist of multiple components separated by the dot ('.') character. Individual components may only consist of alphanumeric characters (A-Z, a-z, 0-9) and underscores ('_'). Components must not start with a numeric character.

> **Interface names start with a reversed DNS domain name**
The reversed DNS part of the name shall be in lower case, with any characters (such as hyphens) not valid in interface names converted to underscores. The subsequent parts of an interface name use UpperCamelCase.

Examples:

*  example.com -> ''com.example.Foo.Bar''

*  example-2.com -> ''com.example_2.Foo.Bar''


> **Official AllSeen Alliance names must start with ''org.alljoyn''**
Despite the fact that the official Internet address for the AllSeen Alliance is ''allseenalliance.org'', the AllSeen Alliance also owns ''alljoyn.org'' and this shorter form will be used for interface names.


> **Proprietary (i.e., non-standardized) Interfaces must not use the ''org.alljoyn'' prefix**
The are expected to use the reversed DNS name of the organization that defined the non-standardized interface.

Example Interfaces for sample applications and test code may be located in the ''org.alljoyn.example'' namespace.


> **Newly proposed Interface names must respect the existing Interface hierarchy**

For example, if the namespace ''org.alljoyn.Sensors'' exists, a proposed humidity sensor Interface definition must use ''org.alljoyn.Sensors.Humidity'' and not something like ''org.aljoyn.Humidity.Sensor''.


#### Member Names

> **Member (property, signal and method) names must use UpperCamelCase notation without punctuation**

They must start with a letter, and consist solely of alphanumeric characters.


> **Property names should be nouns or predicates**

For example: ''Location'', ''IsOpen''

> **Method names should start with a verb**

For example: ''Open'' or ''SetColor''

> **Signal names should describe the event they represent**

Typically, the name of a signal should be phrased in terms of past tense (past participle form), as an event normally describes something that just happened.  For example: ''ItemsChanged''


#### Argument Names

> **Method and signal argument names must use lowerCamelCase notation without punctuation**

This helps distinguish methods and signals from their parameters.


> **All method and signal arguments, both input arguments and output arguments, must have a descriptive name**

This helps users of the interface understand what the parameter is for.

#### Object Paths

The features of a valid object path are described in the [D-Bus specification](http://dbus.freedesktop.org/doc/dbus-specification.html). In a nutshell, a path is a sequence of components (consisting of only alphanumerics and underscores) separated by the slash ('/') character. Paths always begin with a slash character.

It is common to let object paths start with a reversed domain name. Obviously, that reversed domain name should be the same as the one used in at least one of the Interfaces implemented by that object.

In rare cases, it may make sense to standardize the path of the object that implements the interface at hand. This is really only appropriate if the object in question is by definition a singleton, and even then its actual path can easily be discovered via the About feature.

> **The reversed domain name part of an object path should use lowercase notation, the rest of the object path should use UpperCamelCase notation**

For example: ''/org/allseen/Singletons/Foo''


#### Error Names

Error names follow by and large the same rules as Interface names. It is customary for the next-to-last component of the error name to be ''Error''.

> **Error names start with a reversed DNS domain name, in lower case. The subsequent parts of an error name use UpperCamelCase. The next-to-last part of the error name should be ''Error''**

For example: ''org.alljoyn.Lighting.Error.BulbIsBroken''

#### Type and Field Names

When using the [Extended Introspection XML format](irb/extended_introspection_xml)[EIX] for the [Interface definition](#interface_definition_xml_language), the Interface designer has the option to describe structs and dictionaries used in member signatures in more detail by defining a named type.

> **Type names (for named types) must use UpperCamelCase notation without punctuation**

Like interface members, they must start with a letter, and consist solely of alphanumeric characters.

> **Field names in named structs must use lowerCamelCase notation without punctuation**

Again, this is to distinguish between struct's named type from the elements of the struct.

### Interface Definition XML Language


The formal definition of an AllJoyn Interface is expressed in a well-defined XML format, called the Introspection XML language. The name is due to the fact that the definition format was originally designed for run-time introspection of DBus (and later AllJoyn) bus objects and their Interfaces.

#### Two Flavors

There are two flavors of the Interface Definition XML:

*  The "classic" flavor, which is inherited directly from D-Bus. This format is defined in the [D-Bus specification](http://dbus.freedesktop.org/doc/dbus-specification.html)[DBUS], and is used as output of the ''org.freedesktop.DBus.Introspectable.Introspect'' method.
*  The Extended Introspection XML format is an evolution of the classic Introspection XML format that aims to do away with a number of ambiguities in the classic format. This format is better suited as input for code generators, and strives to provide a clearer definition of the Interface semantics that relies less on external documentation. The format is defined in the [Extended Introspection XML Schema](irb/extended_introspection_xml)[EIXS], and is accepted as input by the Allseen Alliance code generator (the ''devtools/codegen'' project). A subset of this format is used as output of the ''org.allseen.Introspectable.Introspect'' method.

#### Valid XML

> **Interfaces offered up for standardization must be described in the Extended Introspection XML format.**

All Interface definitions offered up for standardization must validate against the official [Extended Introspection XML Schema Definition](irb/extended_introspection_xml#schema_definition)[EIXS].

#### Use of External Documentation

> **Interface designers should strive to describe the semantics of their Interface as accurately as possible in the formal XML language. **

It is allowed to rely on external documentation (in the form of an Interface Definition document[IDT] that accompanies the formal XML description) to provide extra information where necessary, but this must never be done gratuitously. Whenever it is possible to capture the semantics in the Extended Introspection XML format directly, this must be done.


## Modeling Style

This section discusses a number of high-level stylistic guidelines.

### Make Interface Definitions Explicit

Strive to make an Interface definition as explicit as possible. All structure and semantics that can be captured in the XML description should be captured there.

> **Prefer Descriptive Names**

Avoid generic names like ''Do'' or ''Execute'' in an Interface. Make sure that the name of a type, Interface or member clearly describes its meaning.

> **Avoid the Variant Type**

A good indication that your Interface definition is overly generic is its use of the variant type (i.e., signatures like ''v'' or ''a{sv}'').

If a property or argument has a variant type, that implies its meaning is not fixed, but dependent on run-time conditions. This in turn has several undesirable consequences:

*  the Interface definition is incomplete without an auxiliary document that describes exhaustively which actual types are to be expected in which run-time context for the variant type. Auxiliary documentation can get lost, out of date, or simply misinterpreted, leading to interoperability issues.
*  the framework can no longer guarantee the correctness of types in the messages sent over the bus. This burden now rests on the application developer, who needs to deal with a host of error conditions related to variant types not containing the expected actual type at run time.

> **Specify All Well-Known Dictionary Keys**

If your Interface definition includes a Dictionary (e.g., a signature like ''a{su}'') that uses keys with specific values, the Interface must clearly specify the value of each such key and its meaning.

> **Avoid Alternative Marshaling Schemes**

AllJoyn offers a rich type system that allows for the creation of complex data structures. For some language bindings, there is even a code generator that generates the required marshaling and unmarshaling code to translate between the programming language equivalent of these data structures and the AllJoyn wire messages.
Make use of these facilities. Do not define properties or arguments as binary blobs or strings, where the actual structured data is then hidden inside some alternative marshaling schema like JSON, XML or some binary encoding of your own design. All arguments that caution against the use of the Variant type in Interfaces apply here, and doubly so.

> **Choose and Document Only One Signal Emission Behavior**

A signal as defined in an AllJoyn Interface can be emitted in many different ways (sessionless, unicast, local or global broadcast, multicast). Depending on the way the signal is emitted, the intended receivers need to take different actions to make sure they actually receive the signal.
When you define signals in an Interface, choose a single intended emission behavior, and document it clearly in the Interface definition.

> **Use Annotations to Declare Your Intentions**

Several predefined annotations exist that allow you to clarify the semantics of your Interface. Make use of these where applicable.

*  ''org.freedesktop.DBus.Method.NoReply'' indicates that a method call will not result in a return message being sent.
*  ''org.freedesktop.DBus.Property.EmitsChangedSignal'' indicates that a property will send a standard signal when its value changes.

### Do Not Reinvent the Wheel

> **Do not repeat information or functionality that is already available in some other Interface. Rather, reuse that Interface.**

Similarly, add information or functionality into the Interface where it makes the most sense.

### Interface Granularity

> **An Interface must encapsulate a single, coherent block of information and functionality.**

Do not create everything-and-the-kitchen-sink Interfaces. Split the functionality and data provided by the 
Interface into logical, coherent blocks. This will facilitate reuse of your Interface by others with similar, but not identical, use cases.

Don't overdo it either: it does not make sense to split every property, signal and method off into its own separate Interface.

> **When parts of the functionality envisioned for an Interface are optional, split them off into a separate Interface.**

An Interface definition is an all-or-nothing promise: if a bus object implements this Interface, it must implement all functionality defined in the Interface. By splitting optional features off in separate Interfaces, it becomes trivial to check whether a given object supports the optional functionality: it does if it implements the associated Interface.

> **When parts of the functionality envisioned for an Interface are permitted only to a specific role,
split them off into a separate Interface.**

This is important to provide ease of use by a consumer app, so that behavior is predictable.
An Interface definition should normally be treatable as an all-or-nothing promise: if a consumer app
can access this Interface, it can access all functionality defined in the Interface.

### Object Granularity

Consider how your data model can be split up over various (hierarchically organized) bus objects. Separate entities in the problem domain should be represented by separate objects on the bus.

In many cases, there is an inherent one-to-many relationship in the data model: one firewall has many rules, one address book has many entries, etc. This kind of relationship can be modeled elegantly as a single parent object (the firewall, the address book, ...) that has many similar child objects (the rules, the contact entries, ...).

There are limits to the scalability of the object hierarchy mechanism, though. As a rule of thumb, the parent/children hierarchy is suitable for up to a hundred children. If you expect more child objects, it is better to revert to an approach where child objects are not instantiated explicitly, but are modeled as elements of a single collection object. Assign some identifier to each element, and provide query methods in the collection object that allow the client to search for specific elements and retrieve their properties.

For example, it would be unwise to represent a media collection as thousands of individual bus objects, each representing a single media file. It is better to assign a unique identifier to each media file, and provide a single MediaCollection object with Search(), Browse() and GetFile() query methods.

>> **Tip**: consider using the well-known relational database modeling tools (Entity-Relationship diagrams, Normal Form decomposition, ...) to reason about your problem domain. While those tools are not to be applied blindly, they will provide useful insights and inspiration for your own Interface decomposition efforts.

### Use of Methods

This section covers some best practices for the use of methods in Interfaces.

#### Error Returns

Be sure to specify error conditions and what error should be returned in each case.

In many programming languages (C in particular), it is common practice to define functions as having an integer return value that indicates whether the function concluded successfully (zero return value) or what went wrong (various non-zero return values). 

Do not use this practice for the definition of AllJoyn Interfaces. Instead, use AllJoyn's dedicated method error return mechanism. 

> **Methods should only conclude with a regular method return message (containing the declared output 
arguments) when the method has concluded successfully. If a method failed for some reason, the method should 
conclude by sending a method error return message, containing a well-defined error code.**

#### Do Not Use Methods to Emulate Properties

> **Use properties to represent externally observable state. Do not use methods to emulate properties.**

It is possible to emulate properties by creating dedicated "getter" methods. For example, instead of having a Color property, an Interface might define the GetColor method. Refrain from doing this.

The first argument against dedicated getter methods is simply consistency. The property mechanism exists, so use it.

The second argument may be more material: the property mechanism allows for the annotation of cacheable properties, which is not possible with dedicated getter methods.

If an object's observable state is so large that it really cannot be represented in a set of properties, a getter method that retrieves subsets of the state may be warranted. However, objects with such a large state should raise a warning flag: perhaps it is better to further decompose this object into smaller objects?

### Use of Properties

This section covers some best practices for the use of Properties in Interfaces.

#### Properties Represent Externally Observable State

As discussed in the [Object Granularity](#object_granularity) section, different bus objects represent different entities in the problem domain. The various Interfaces represent various aspects of those entities. The properties defined in an Interface represent the observable state of an aspect of an entity.

In theory, an observer of the bus object (i.e., a client application) should be able to infer everything it needs to know about the state of that bus object from the object's properties.

#### Types of Properties

Properties come in three flavors, based on their associated [org.freedesktop.DBus.Property.EmitsChangedSignal](http://dbus.freedesktop.org/doc/dbus-specification.html#introspection-format) annotation value:

*  "true" defines an *updating* property. Whenever the value of such a property changes, the bus object will emit the org.freedesktop.DBus.Properties.PropertiesChanged signal with the new property value.
*  "invalidates" defines an *invalidating* property. Whenever the value of such a property changes, the bus object will emit the org.freedesktop.DBus.Properties.PropertiesChanged signal, but the new property value will not be specified.
*  "false" (the default value if the annotation is not present) defines a *non-cacheable* property that never causes the org.freedesktop.DBus.Properties.PropertiesChanged signal to be emitted.

>> **Note**: AllJoyn deviates from the DBus specification here: the default value for this annotation is "true" for DBus, but "false" for AllJoyn. It is best to always explicitly specify the annotation for each property, to avoid confusion.

Updating and invalidating properties are cacheable. Clients can rest assured that the values they acquired for those properties remain valid until a counter-notice (in the form of the PropertiesChanged signal) is received. Non-cacheable properties must be retrieved from the remote bus object every time they are needed, which may incur significant network traffic and latency.

The Data-driven API for AllSeen, for example, will automatically cache all cacheable properties for discovered objects on behalf of the application.

As a rule of thumb:

*  Non-cacheable properties are only really useful for properties that change very rapidly, making the emission of the PropertiesChanged signal impractical. For example, the received byte counter on an Interface representing a network interface changes very rapidly.
*  Invalidating properties are useful for those properties that are expected to be updated more frequently than they are actually used, or that have a very large representation (large arrays or structures). In these cases, it may save network bandwidth to not send the new property value along with the invalidation message.
*  Updating properties are useful for those properties that are expected to be used more frequently than they are updated. Constant properties (for example, the Version property that is defined for each Interface) should also be marked as updating properties, to indicate that they are indeed cacheable.

When in doubt, use an updating property.

#### Writable Properties

As a rule of thumb, strive to define properties as read-only. Properties represent the state of an object, methods allow you to manipulate that state. Typically, the outcome of a method call will be reflected by a change in the object's observable state, and hence by a change in value for the object's properties.

If it is conceptually possible to manipulate a property in isolation, then declaring the property read-write is warranted as a convenience. As an example, an audio playback device may have a Volume property. It is perfectly acceptable to make this property read-write.

> **Do not ever, in any case, define write-only properties.**

A write-only property is just a badly disguised method.

#### Avoid Redundant Properties

To keep the requirements for producers as lightweight as possible, avoid exposing the same information multiple ways.  In general, if a piece of information can be derived from another value exposed, let the consumer derive it rather than making producers expose the derived value.

### Use of Signals

This section covers some best practices for the use of signals in Interfaces.

#### Types of Signals

Signals come in several flavors. The recipients of the signal vary based on the signal's flavor:

*  *unicast* signals have an explicit destination (a bus name). Only the intended recipient will receive the signal.
*  *sessioncast* signals do not specify a destination but a session id. All participants in the session (apart from the emitter) will receive the signal.
*  *local broadcast* signals are delivered to all participants that share the sender's routing node, provided that those participants installed an appropriate match rule.
*  *global broadcast* signals are delivered to all participants that are connected to a routing node that is somehow in session with the sender's routing node. Again, the recipients must have the appropriate match rule installed.
*  *sessionless* signals are delivered to all participants on the network, if they have the appropriate match rule. Note that sessionless signals have delivery semantics that are very different from the other signal types.

> **Every signal in the Interface must be of a well-defined flavor. Document which flavor is intended for which signal.**

>> **Note**: the current version of the Extended Introspection XML language is not yet sufficiently expressive to capture the distinction between the different signal flavors. It can only capture whether a signal is sessionless or not. For all other signal types, add an XML comment that clearly states the intended signal emission behavior.

> **Use sessioncast signals, or explain why a sessioncast signal is insufficient.**

As a rule of thumb, use sessioncast signals. In rare cases, a unicast signal is warranted. Sessionless signals have very specific semantics, use them only in those cases where you need these semantics. Avoid broadcast signals: the local broadcast signal is only relevant for interprocess communication on a single device (which is not exactly the scope of AllSeen), and the global broadcast signal is unpredictable: you can never know which participants will receive the signal and which ones won't. In addition, indiscriminate use of global broadcast signals will cause a lot of spurious network traffic.

#### Signals are for Events, Properties are for State

Signals are most useful for representing ephemeral occurrences related to the entities in the problem domain. Ephemeral occurrences are facts that are true at a single point in time. A colloquial term for these occurrences is *events*. One can contrast this with the observable *state* of the domain entities, which remains true over a longer period of time. That state is, as argued before, best modeled as a set of properties.

For example, in a home security system, one of the domain entities is a door. A door has observable state: a location, whether it's locked, whether the door is open or closed. These aspects of the door are represented as properties in the Door Interface.  The fact that someone is walking through the open door, on the other hand, is definitely an event: this is true at this point in time, but in two seconds, that same person is no longer walking through the door. Hence, the PersonPassedThrough event would be modeled as a signal in the Door Interface.

#### Prefer intrinsic state and events over derived state and events

Intrinsic state refers to the natural state of being for the system being modeled.

Intrinsic event refers to natural events from the system being modeled.  There are actually 2 kinds of intrinsic events: those that result in state change and those that do not alter state.  In AllJoyn, intrinsic events that change state are conveyed with the PropertiesChanged signal since state is conveyed via properties.  Intrinsic events that do not alter state will need to be send as their own signals.

As an example of intrinsic state, consider a door.  A door has 2 intrinsic states: open or closed.  An example of derived state would be that the door was opened for X time.  Such state is derived by observing the state transition from closed to open and starting a timer.  The value of that timer is the derived state.

Systems with more than one intrinsic state inherently have at least one intrinsic event to convey the transition from one state to the other.  In the case of the door, there are 2 such state transition events: door opened and door closed.  An example of a derived event could be that the door was left open for 5 minutes (derived from a 5 minute timer that started as a result of the door opened event and that the door closed event was never received before the timer expired).

For intrinsic events that do not alter state, consider a turn-style.  The intrinsic event with a turn-style is that a person passed though.  While most mechanical turn-styles include a counter, that count of the number of people who passed through is derived state.  A turn-style could ring a bell instead of increment a counter.  Regardless of what other functionality a turn-style has it will always process the event of a person passing through which is what makes that the intrinsic event.

#### Don't Reinvent Updating Properties with Signals

> **For state that is represented as properties, do not define dedicated signals to inform observers that the properties have changed. **

The D-Bus Properties Interface that is part of the AllJoyn framework already incorporates that functionality. Define your property as an updating property (see [above](#types_of_properties)) and rely on the existing framework functionality to convey the state update information to interested observers.

### Avoid Dependencies on Session Ports

Interfaces should use ephemeral session ports that can be dynamically discovered.
As such, an interface specification does not need to mention them.

## Common Patterns

This section covers commonly occurring patterns in Interface definitions. It offers standardized suggestions for these common patterns.

### Units

This section explains how to deal with units in AllJoyn Interfaces.

#### Units are Non-negotiable

> **For every type of quantity (temperature, humidity, length, mass, ...) that is represented in your data model, you must define the intended unit up front. All implementations of the Interface must present values in the unit you defined.**

#### Preferred Units

> **As a rule of thumb, use [SI units](http://www.bipm.org/en/measurement-units/)[SI] where possible.**

> **Whenever this makes sense, reuse the units chosen for the same quantity in existing standardized Interfaces.**

This guideline aims to promote consistency across different Interfaces. Deviate from this guideline only where it really makes sense for the problem domain at hand.

The table below summarizes the most common units:

 | Quantity                    | Unit                                                    | 
 | --------                    | ----                                                    | 
 | Absolute time (date & time) | Seconds since UNIX Epoch (00:00:00 on January 1, 1970). | 
 | Time of day                 | Seconds since midnight                                  | 
 | Time interval               | Seconds                                                 | 
 | Bandwidth                   | Bits per second                                         | 
 | Data size                   | Bytes                                                   | 
 |                             |                                                         | 


#### Precision

> **Prefer fixed-point representation over floating point representations. **

In other words: use 32-bit or 64-bit integers to represent the measurements. Microcontroller-based sensors often do not include floating-point hardware, which makes it inconvenient for such devices to produce or process floating point values.

> **The precision of the measurements in the Interface must be clearly defined. If the precision is fixed for all implementations, it must be clearly stated in the Interface definition. If the precision is variable, it must be stated in an auxiliary property/argument (called fooExponent for a measurement argument called foo) as a power of 10 versus the base unit.**

For example:

	
	interface: org.alljoyn.HotTub
	  RO-property: temperature
	  description: Water temperature in °C
	  RO-property: temperatureExponent
	  description: Power of 10 multiplier to temperature


When ''temperature = 303'' and ''temperatureExponent = -1'', the actual temperature of the hot tub water is 303*10e-1 = 30.3°C.


## Designing for Evolution

Inevitably, standardized Interfaces will evolve over time. This section provides some insights in the do's and don'ts of Interface evolution.
At this moment, there is no clear architectural vision around Interface Evolution, so this section is, by necessity, rather bare.

### What is Interface Evolution?

Interface Evolution is the process in which newer versions of an existing Interface are defined, in such a way that the various versions of the Interface remain compatible with one another. The compatibility must go both ways: clients expecting newer versions of an Interface must be able to deal with services offering older versions of that Interface, and clients expecting older versions of an Interface must be able to deal with services offering a newer version of that Interface.

In practice, every new version of an Interface must be a strict superset of the previous version of the same Interface. See [below](#concrete_guidelines) for what that means precisely. Interfaces always evolve in a straight line: there are no branches, there is never any deprecation of existing features (members) of an Interface.

Any deviation from the straight-line, strict superset evolution described above implies the creation of a totally new Interface, which starts at version 1. This new Interface *must* have a new name.
### Don't Evolve If You Can Augment

In many cases it is better to define an auxiliary interface than to truly evolve an existing interface. There are no hard and fast rules for this, this is the kind of judgment call that requires a lot of [Fingerspitzengefühl](http://en.wikipedia.org/wiki/Fingerspitzengef%C3%BChl).
### Vendor Extensions

> **Do not add proprietary extensions to a standardized Interface. Define an auxiliary interface instead.**

Obviously, the reversed domain name prefix of the auxiliary Interface must not be ''org.alljoyn''. Do make sure there is a clear link between the name of the auxiliary Interface and the name of the standardized Interface it extends.

### Concrete Guidelines

> **Every standardized Interface must include a uint16 (signature ''q'') property ''Version'' that indicates the implemented version of the Interface.**

This property is used at run time to determine the capabilities of the object offering the Interface.

> **Every new version of an Interface must be a strict superset of the previous version of that Interface.**

That means that every new version of an Interface may:

*  add new members (properties, signals, methods).

The following things are expressly forbidden:

*  remove existing members

*  change member signatures

## Designing for Security

*This section will provide detailed guidelines about designing Interfaces with security (in particular, Security 2.0) in mind. The recommendations here should come from the Security Committee rather than the Interface Review Board. We're just adding them here because it makes sense to keep all Interface-related guidelines in one place, and because the Interface Review Board reviews will take these guidelines into account as well.*

Make sure that any information that is privacy sensitive is secured, not sent in the clear.

## Acronyms and terms

 | **Term**                   | **Definition**                                                                                                                                                                                                                                                                                 | 
 | --------                   | --------------                                                                                                                                                                                                                                                                                 | 
 | AllJoyn service frameworks | A collection of full-feature implementations using the AllJoyn framework that provides specific functionality.  These are building blocks can be combined together to build interoperable devices and applications.                                                                            | 
 | UpperCamelCase             | A naming convention in which a name is formed of multiple words that are joined together as a single word with the first letter of each of the multiple words capitalized so that each word that makes up the name can easily be read. This convention is also sometimes known as Pascal case. | 
 | lowerCamelCase             | A naming convention like UpperCamelCase except that the first letter of the first word is lower case.                                                                                                                                                                                          | 


## References


*  [DBUS] [D-Bus Introspection Format Specification](http://dbus.freedesktop.org/doc/dbus-specification.html#introspection-format)

*  [EIX] [Extended Introspection XML Language](https///wiki.allseenalliance.org/irb/extended_introspection_xml)

*  [EIXS] [Extended Introspection XML Schema](https///wiki.allseenalliance.org/irb/extended_introspection_xml#schema_definition)

*  [GLOS] [AllJoyn Glossary](https///allseenalliance.org/developers/learn/glossary)

*  [IDT] [Interface Definition template](https///git.allseenalliance.org/cgit/interfaces.git/tree/extra/interface-definition-template.md)

*  [RFC] [RFC Editor Abbreviation List](http://www.rfc-editor.org/rfc-style-guide/abbrev.expansion.txt)

*  [SI] [SI system of measurement units](http://www.bipm.org/en/measurement-units/)
