# Interface Design Guidelines v1.1

This version of the Guidelines document was approved by the TSC on 2015-11-16.

The rules in this document are guidelines.  Should the interface developer encounter a need to deviate from these rules, he/she should provide detailed justification for doing so during the review and work with the IRB((IRB: Interface Review Board - A group that reports to the AllSeen Alliance Technical Steering Committee with recommendations on proposed interfaces that will be owned by the AllSeen Alliance.)) on possible alternatives.
## Naming Conventions

### Interface Names

++++ Interface names may only use the characters A-Z, a-z, 0-9, "_" (underscore), and "." (dot). |
This originates from using the D-Bus spec as the starting point for developing AllJoyn.  This is what the current code expects and is required to maintain interoperability with older versions.
++++

++++ The "." (dot) character is used to separate interface name components. |
This allows for creating an organized taxonomy of interface names.
++++

++++ Interface names must start with the reversed DNS name of the organization that owns the interface. |
The reversed DNS part of the name shall be in lower case, with any characters (such as hyphens) not valid in interface names converted to underscores.

Examples:

*  example.com -> ''com.example.Foo.Bar''

*  example-2.com -> ''com.example_2.Foo.Bar''
++++

++++ All components of the interface name, apart from the reversed DNS name, must use UpperCamelCase. |
Good:

*  ''org.alljoyn.Foo.Bar''
Bad:

*  ''org.AllJoyn.Foo.Bar'' (reversed DNS name should not be capitalized)

*  ''org.alljoyn.foo.bar'' (components following DNS name must use UpperCamelCase)
++++

++++ Official AllSeen Alliance names must start with ''org.alljoyn''. |
Despite the fact that the official Internet address for the AllSeen Alliance being ''allseenalliance.org'', the AllSeen Alliance also owns ''alljoyn.org'' and this shorter form will be used for interface names.
++++

++++ Proprietary (i.e., non-standardized) Interfaces must not use the ''org.alljoyn'' prefix. |
They are expected to use the reversed DNS name of the organization that defined the non-standardized interface.

Example Interfaces for sample applications and test code may be located in the ''org.alljoyn.example'' namespace.
++++

++++ Newly proposed Interface names must respect the existing Interface hierarchy. |
This is to promote an organized name taxonomy.

Good Examples:

*  org.alljoyn.Sensors

*  org.alljoyn.Sensors.Humidity

*  org.alljoyn.Sensors.Temperature

Bad Examples (do not do):

*  org.alljoyn.Humidity.Sensor

*  org.alljoyn.Temperature.Sensor

*  org.alljoyn.Sensor
++++

++++ Interface names should avoid the word "Error" in their name. |
This is to avoid confusion with Error names.
++++

### Member Names

++++ Member (property, signal and method) names must use UpperCamelCase notation without punctuation. |
They must start with an uppercase letter and consist solely of alphanumeric characters (A-Z, a-z, and 0-9 only).
++++

++++ Property names should be nouns or predicates. |
For example: ''Location'', ''IsOpen''
++++

++++ Method names should start with a verb. |
For example: ''Open'' or ''SetColor''
++++

++++ Signal names should describe the event they represent. |
Typically, the name of a signal should be phrased in terms of past tense (past participle form), as an event normally describes something that just happened.  For example: ''ItemsChanged''
++++

### Argument Names

++++ Method and signal argument names must use lowerCamelCase notation without punctuation. |
They must start with a lowercase letter and consist solely of alphanumeric characters (A-Z, a-z, and 0-9 only).

This helps distinguish methods and signals from their parameters.
++++

++++ Both input and output arguments for methods and signals must have a descriptive name. |
This helps users of the interface understand what the parameter is for.
++++

### Error Names

++++ Error names must start with the reversed DNS name of the organization that defines the error. |
This helps to provide a namespace for the set of errors being defined.
++++

++++ The next-to-last part of the error name should be ''Error''. |
This identifies the string as an error name and is easy to distinguish from interface names.

For example: ''org.alljoyn.Lighting.Error.BulbIsBroken''
++++

++++ Errors specific to an interface must use the interface's namespace as a prefix. |
This provides a namespace for the set of errors being defined.

For example, the ''DuplicateCertificate'' error for the ''org.alljoyn.Bus.Security.ManagedApplication'' interface should have as full name ''org.alljoyn.Bus.Security.Error.DuplicateCertificate''.
++++

++++ Do not use (the name of) QStatus error codes as error names. |
''QStatus'' error codes (e.g. ''ER_OK'', ''ER_FAIL'', etc.) are intended for use as local error codes within a single process. The are not intended to be sent over the wire.

The following are **not** valid error names:

*  ''ER_INVALID_VALUE''

*  ''org.alljoyn.Bus.ER_INVALID_VALUE''

++++
### Type and Field Names

++++ Use type names for each level of nested structures. |
This encourages reuse of the same set of structure elements in the same order throughout an interface.  The [AllJoyn Introspection XML format](irb/xmlv2) has express support for named types.
++++

++++ Type names (for named types) must use UpperCamelCase notation without punctuation. |
Like interface members, they must start with a letter, and consist solely of alphanumeric characters.
++++

++++ Field names in named structs must use lowerCamelCase notation without punctuation. |
Again, this is to distinguish between struct's named type from the elements of the struct.
++++


### Language Related Considerations

++++ Use English words for identifiers. |
Always use U.S. English spelling when there are different ways to spell a word.

For example:

*  Use *caliber* instead of *calibre*
*  Use *license* instead of *licence*
++++

++++ Only use abbreviations and acronyms in names if they are widely understood and commonly used. |
It's perfectly fine to use HTML or id (short for "identity"), but don't use "temp" instead of "temperature".  One source for determining whether an abbreviation or acronym is "widely understood" is if it is listed in the [RFC Editor Abbreviations List](http://www.rfc-editor.org/rfc-style-guide/abbrev.expansion.txt)((RFC Editor Abbreviations List - [http://www.rfc-editor.org/rfc-style-guide/abbrev.expansion.txt](http://www.rfc-editor.org/rfc-style-guide/abbrev.expansion.txt))) with an asterisk.
++++

++++ In UpperCamelCase and lowerCamelCase identifiers, capitalize acronyms and initialisms as if they were regular words. |
Often, type or member names will include some kind of acronym or initialism (HTML file, DB connection, IP address, ...).  The convention is to treat these as "regular" words and to capitalize only the first letter of the word.

Hence,

*  *HtmlFile* instead of *HTMLFile*
*  *DbConnection* instead of *DBConnection*
*  *IpAddress* instead of *IPAddress*
++++

++++ Use consistent terminology. |
Don't use multiple terms for the same concept.  If a term is defined in the [AllJoyn glossary](https///allseenalliance.org/developers/learn/glossary)((AllJoyn Glossary - [https://allseenalliance.org/developers/learn/glossary](https///allseenalliance.org/developers/learn/glossary))), use it rather than a different synonym.  (For example, use "producer" not "provider".)

Likewise, don't use a term differently from how it is already used in the system.
++++

++++ Use names that describe actors and not acts. |
Consider the following statements:

*  A road construction object implements a *paver*, not a *pavement*.

*  A list object implements a *container*, not a *containment*.

*  An object that manages a resource implements a *manager*, not a *management*.
++++

++++ Use descriptive names. |
Avoid generic names like ''Do'' or ''Execute''.  Make sure that the name of a type, interface, or member clearly describes its meaning.
++++

++++ Use the shortest unambiguous name. |
For example,

*  *OperationalMode* instead of *OperationalModeId*

*  *ResetAlert(alertCode)* instead of *ResetSpecificAlert(alertCode)*

In addition, don't repeat yourself: don't prefix every member of an interface with the same string, especially not when that string is part of the interface name itself.

For example, in an interface called *com.example.Door*,

*  *IsOpen* instead of *DoorIsOpen*

*  *Location* instead of *DoorLocation*.

++++

## Modeling Style

++++ Do not reinvent the wheel. |
Do not repeat information or functionality that is already available in some other Interface.  Rather, reuse that Interface.

If additional functionality is required, then define an auxiliary interface that is related to the base interface.

Design to ease bridging to standard or widely deployed non-AllJoyn schemas if they exist (Bluetooth profile, ZigBee profile, IPSO, MIB, MOF, etc.).  That is, where such schemas are known to exist, try to be as consistent as possible in order to aid in bridging, and reference relevant ones in your specification.
++++

++++ Design interfaces around ideal abstract operations and avoid device specific idiosyncrasies.  |
Try to formulate interfaces in such a way that they are widely applicable and reusable. Do not cater to a specific implementation of a functionality on a device you know, but aim for abstraction.
++++

++++ Avoid the variant type. |
A good indication that your interface definition is overly generic is its use of the variant type (i.e., signatures like ''v'' or ''a{sv}'').

If a property or argument has a variant type, that implies its meaning is not fixed, but dependent on run-time conditions. This in turn has several undesirable consequences:

*  The interface definition is incomplete without an auxiliary document that describes exhaustively which actual types are to be expected in which run-time context for the variant type.  Auxiliary documentation can get lost, out of date, or simply misinterpreted, leading to interoperability issues.
*  The framework can no longer guarantee the correctness of types in the messages sent over the bus.  This burden now rests on the application developer, who needs to deal with a host of error conditions related to variant types not containing the expected actual type at run time.
++++

++++ Specify constraints on arrays of structures. |
If your Interface definition includes an array of structures (e.g., a signature like a[Widget]), the Interface must clearly specify whether order is significant, and whether duplicates (or elements with duplicate keys) are allowed.
++++

++++ Specify all well-known dictionary keys. |
If your Interface definition includes a Dictionary (e.g., a signature like ''a{su}'') that uses keys from a predefined set, the Interface must clearly specify each key and its meaning.

This is absolutely required if the dictionary uses the variant type for the value (e.g., ''a{sv}'').

It is also expected that duplicate keys in the same dictionary are not allowed.
++++

++++ Avoid alternative marshaling schemes. |

AllJoyn offers a rich type system that allows for the creation of complex data structures.  For some language bindings, there is even a code generator that generates the required marshaling and unmarshaling code to translate between the programming language equivalent of these data structures and the AllJoyn wire messages.

Make use of these facilities.  Do not define properties or arguments as binary blobs or strings where the actual structured data is then hidden inside some alternative marshaling schema like JSON, XML, CBOR, or some binary encoding of your own design.  All arguments that caution against the use of the Variant type in Interfaces apply here, and doubly so.
++++

++++ Choose and document only one signal emission behavior. |
A signal as defined in an AllJoyn Interface can be emitted in many different ways (sessionless, unicast, local or global broadcast, or sessioncast).  Depending on the way the signal is emitted, the intended receivers need to take different actions to make sure they actually receive the signal.

When you define signals in an Interface, choose a single intended emission behavior, and document it clearly in the Interface definition.
++++

++++ Minimize use of localizable strings. |
Normally, the UI used by a human should translate low level details into human readable information, rather than having the human readable string come from the producer itself.  Where localizable strings are required, there should be a way to enumerate what languages a producer supports, and there should be a way for the consumer to request strings using a given language tag and such a method should support language tag matching ([RFC 4647 section 3.4](http://tools.ietf.org/html/rfc4647#section-3.4)) for which core library support exists for interfaces to use. 
++++

++++ Use annotations to declare your intentions. |
Several predefined annotations exist that allow you to clarify the semantics of your Interface.  Make use of these where applicable.

*  ''org.gtk.GDBus.Since'' on an interface indicates the current version, and on a member indicates the first interface version in which the member appeared.  Defaults to 1.  See the [AllJoyn Introspection XML](irb/xmlv2) spec for more info.

*  ''org.alljoyn.Bus.Secure'' indicates whether an interface requires security.  Default is ''inherit''.

*  ''org.alljoyn.Bus.DocString.//LanguageTag//'', where *LanguageTag* is a language tag with any hyphens converted to underscores, provides an end-user text description in a given language of an interface, method, property, or signal.  See the [AllJoyn Introspection XML](irb/xmlv2) spec for more info.

*  ''org.freedesktop.DBus.Deprecated'' indicates that the interface, method, property, or signal is deprecated.  See the D-Bus spec for more info.

*  ''org.freedesktop.DBus.Method.NoReply'' indicates that a method call will not result in a return message being sent.  See the D-Bus spec for more info.

*  ''org.freedesktop.DBus.Property.EmitsChangedSignal'' indicates whether a property will send a standard signal when its value changes.  If set on an interface, provides the default for all properties in that interface.  See the D-Bus spec for more info.

*  ''org.alljoyn.Bus.Signal.//Behavior//'' indicates the signal emission behavior of a signal.  See the [AllJoyn Introspection XML](irb/xmlv2) spec for more info.

*  ''org.alljoyn.Bus.Struct.//StructureName//.Field.//fieldName//.Type'' defines a field named *fieldName* in a structure named *StructureName*.  See the [AllJoyn Introspection XML](irb/xmlv2) spec for more info.

*  ''org.alljoyn.Bus.Type.Name'' defines the type, using named types, of a signal or method argument, or of a property.  See the [AllJoyn Introspection XML](irb/xmlv2) spec for more info.

*  ''org.alljoyn.Bus.Dict.//DictionaryName//.Key.Type'' defines a dictionary named *DictionaryName*.  See the [AllJoyn Introspection XML](irb/xmlv2) spec for more info.

*  ''org.alljoyn.Bus.Dict.//DictionaryName//.Value.Type'' defines the type, using named types, of the values in the dictionary named *DictionaryName*.  See the [AllJoyn Introspection XML](irb/xmlv2) spec for more info.

*  ''org.alljoyn.Bus.Enum.//EnumName//.Value.//ValueName//'' defines an enumeration type named *EnumName* with a value named *ValueName*.  See the [AllJoyn Introspection XML](irb/xmlv2) spec for more info.

*  ''org.alljoyn.Bus.Type.Min'' indicates the minimum value of a signal or method argument, or of a property.

*  ''org.alljoyn.Bus.Type.Max'' indicates the maximum value of a signal or method argument, or of a property.

*  ''org.alljoyn.Bus.Type.Units'' indicates the units of a signal or method argument, or of a property.

*  ''org.alljoyn.Bus.Type.Default'' indicates the default value of a readwrite property when created or reset.a value by any other means.  See the [AllJoyn Introspection XML](irb/xmlv2) spec for more info.

*  ''org.alljoyn.Bus.Type.Reference'' provides a cross-reference to some other document, usually one that defines the meaning or values of a property or argument.

*  ''org.alljoyn.Bus.Type.DisplayHint'' provides a hint as to how a value should be displayed (e.g., as decimal or hex).  See the [AllJoyn Introspection XML](irb/xmlv2) spec for more info.
++++

### Interface Granularity

++++ An interface must encapsulate a single, coherent block of information and functionality. |
Do not create everything-and-the-kitchen-sink interfaces. Split the functionality and data provided by the 
Interface into logical, coherent blocks. This will facilitate reuse of your interface by others with similar, but not identical, use cases.

Don't overdo it either: it does not make sense to split every property, signal and method off into its own separate interface.
++++

++++ When parts of the functionality envisioned for an interface are optional, split them off into a separate interface. |
An interface definition is an all-or-nothing promise: if a bus object implements this interface, it must implement all functionality defined in the interface.  By splitting optional features off in separate interfaces, it becomes trivial to check whether a given object supports the optional functionality: it does if it implements the associated interface.
++++

++++ When parts of the functionality envisioned for an interface are permitted only to a specific role,
split them off into a separate interface. |
This is important to provide ease of use by a consumer app, so that behavior is predictable.

An interface definition should normally be treatable as an all-or-nothing promise: if a consumer app
can access this interface, it can access all functionality defined in the interface.
++++

### Object Granularity

++++ Consider how your data model can be split up over various (hierarchically organized) bus objects. |

Separate entities in the problem domain should be represented by separate objects on the bus.

In many cases, there is an inherent one-to-many relationship in the data model: one firewall has many rules, one address book has many entries, etc. This kind of relationship can be modeled elegantly as a single parent object (the firewall, the address book, ...) that has many similar child objects (the rules, the contact entries, ...).

>> **Tip**: consider using the well-known relational database modeling tools (Entity-Relationship diagrams, Normal Form decomposition, ...) to reason about your problem domain. While those tools are not to be applied blindly, they will provide useful insights and inspiration for your own Interface decomposition efforts.

++++

++++ Don't let the object hierarchy grow beyond (approximately) 100 bus objects. |
There are limits to the scalability of the object hierarchy mechanism. As a rule of thumb, the parent/children hierarchy is suitable for up to a hundred children. If you expect more child objects, it is better to revert to an approach where child objects are not instantiated explicitly, but are modeled as elements of a single collection object. Assign some identifier to each element, and provide query methods in the collection object that allow the client to search for specific elements and retrieve their properties.

For example, it would be unwise to represent a media collection as thousands of individual bus objects, each representing a single media file. It is better to assign a unique identifier to each media file, and provide a single MediaCollection object with Search(), Browse() and GetFile() query methods.
++++


### Use of Methods

++++ Specify the errors that each method could return. |
This should be done for errors that can happen as part of processing the method call.  It is not necessary to list errors that are automatically generated by the system such as in the case the sender of a method call uses parameters that do not match the method's signature.
++++

++++ Do not use reply parameters to indicate errors. |
In many programming languages (C in particular), it is common practice to define functions as having an integer return value that indicates whether the function concluded successfully (zero return value) or what went wrong (various non-zero return values). 

Do not use this practice for the definition of AllJoyn Interfaces. Instead, use AllJoyn's dedicated method error return mechanism. The error names must adhere to the naming conventions described above. Do not use ''QStatus'' error codes (or any variation thereof) to report error conditions over the wire.
++++

++++ Methods must either return a valid reply message with valid parameters, return an error message or be defined with the ''org.freedesktop.DBus.NoReply'' annotation. |
Methods defined with the ''org.freedesktop.DBus.NoReply'' annotation must not return anything.
++++

++++ Avoid error returns if there is a reasonable way to deal with questionable input. |
Handling errors requires special case code, which is a burden for the application programmer.

Consider whether it is simpler to adapt the received input to an appropriate setting than it is to check for inappropriate values and sending an error.

As a concrete example, consider an audio volume interface, where the volume can be set between 0 and 100, but only in increments of 5. It is better to round ''SetVolume(36)'' to a volume setting of 35, than it is to return an error message.
++++

++++ Be explicit about which conditions will cause an error return. |
Do not leave the decision of sending an error return for certain conditions up to implementers.

As a concrete example, consider an audio volume interface, where the volume can be set between 0 and 100, but only in increments of 5. The interface specification must be explicit about what happens when a client invokes ''SetVolume(36)'':

*  either all implementations of this interface send an error return

*  or all implementations round the input value to an acceptable value (it is fine to leave the details of the rounding algorithm up to implementers)

An approach that allows some implementers to return error messages, while others silently round the input value, will inevitably lead to interoperability problems. Client applications that are only tested against the latter kind of implementation, will fail to deal with the former kind of implementation when they encounter it in the wild.
++++


### Use of Signals

++++ Every signal in the Interface must be of a well-defined flavor. Document which flavor is intended for which signal. |
Signals come in several flavors. The recipients of the signal vary based on the signal's flavor:

*  *unicast* signals have an explicit destination (a bus name). Only the intended recipient will receive the signal.
*  *sessioncast* signals do not specify a destination but a session id. All participants in the session (apart from the emitter) will receive the signal.
*  *local broadcast* signals are delivered to all participants that share the sender's routing node, provided that those participants installed an appropriate match rule.  Local broadcast signals should not be used in AllJoyn.
*  *global broadcast* signals are delivered to all participants that are connected to a routing node that is somehow in session with the sender's routing node. Again, the recipients must have the appropriate match rule installed.
*  *sessionless* signals are delivered to all participants on the network, if they have the appropriate match rule. Note that sessionless signals have delivery semantics that are very different from the other signal types.

The [AllJoyn Introspection XML](irb/xmlv2#signal_emission_behaviors) language defines annotations that allow you to specify the emission behavior for signals.
++++

++++ Use sessioncast signals, or explain why a sessioncast signal is insufficient. |
As a rule of thumb, use sessioncast signals. In rare cases, a unicast signal is warranted. Sessionless signals have very specific semantics, use them only in those cases where you need these semantics.  Avoid broadcast signals: the local broadcast signal is only relevant for interprocess communication on a single device (which is not exactly the scope of AllSeen), and the global broadcast signal is unpredictable: you can never know which participants will receive the signal and which ones won't.  In addition, indiscriminate use of global broadcast signals will cause a lot of spurious network traffic.
++++

### Use of Properties

++++ Do not define custom method accessors properties. |
It is possible to emulate properties by creating dedicated "getter" and "setter" methods. For example, instead of having a Color property, an Interface might define the GetColor method. Refrain from doing this.

The first argument against dedicated getter methods is simply consistency. The property mechanism exists, so use it.

The second argument may be more material: the property mechanism allows for the annotation of cacheable properties, which is not possible with dedicated getter methods.

If an object's observable state is so large that it really cannot be represented in a set of properties, a getter method that retrieves subsets of the state may be warranted. However, objects with such a large state should raise a warning flag: perhaps it is better to further decompose this object into smaller objects?
++++

++++ Do not use custom signals to distribute property change information. |
The D-Bus Properties Interface that is part of the AllJoyn framework already incorporates that functionality. Define your property as an updating property and rely on the existing framework functionality to convey the state update information to interested observers.
++++

++++ Use properties to represent externally observable state. |
Different bus objects represent different entities in the problem domain. The various interfaces represent various aspects of those entities.  The properties defined in an interface represent the observable state of an aspect of an entity.

In theory, an observer of the bus object (i.e., a client application) should be able to infer everything it needs to know about the state of that bus object from the object's properties.
++++

++++ Never create write-only properties. |
A write-only property is just a method call with no reply in disguise.
++++

++++ Avoid redundant properties. |
To keep the requirements for producers as lightweight as possible, avoid exposing the same information multiple ways.  In general, if a piece of information can be derived from another value exposed, let the consumer derive it rather than making producers expose the derived value.
++++

++++ Explicitly call out the update nature of properties. |
Properties come in three flavors, based on their associated [org.freedesktop.DBus.Property.EmitsChangedSignal](http://dbus.freedesktop.org/doc/dbus-specification.html#introspection-format) annotation value:

*  "true" defines an *updating* property. Whenever the value of such a property changes, the bus object will emit the org.freedesktop.DBus.Properties.PropertiesChanged signal with the new property value.

*  "invalidates" defines an *invalidating* property. Whenever the value of such a property changes, the bus object will emit the org.freedesktop.DBus.Properties.PropertiesChanged signal, but the new property value will not be specified.

*  "false" (the default value if the annotation is not present) defines a *non-cacheable* property that never causes the org.freedesktop.DBus.Properties.PropertiesChanged signal to be emitted.

*  "const" defines a cachable property that is guaranteed to never change during the lifetime of the object it belongs to, and hence a signal is never emitted for it.   "const" was not supported in AllJoyn 15.09 and before, and "true" should be used until support exists, to enable caching.

> **Note**: AllJoyn deviates from the DBus specification here: the default value for this annotation is "true" for D-Bus, but "false" for AllJoyn. It is best to always explicitly specify the annotation for each property, to avoid confusion.

Updating, invalidating and const properties are cacheable. Clients can rest assured that the values they acquired for those properties remain valid until a counter-notice (in the form of the PropertiesChanged signal) is received. Non-cacheable properties must be retrieved from the remote bus object every time they are needed, which may incur significant network traffic and latency.

As a rule of thumb:

*  Non-cacheable properties are only really useful for properties that change very rapidly, making the emission of the PropertiesChanged signal impractical. For example, the received byte counter on an Interface representing a network interface changes very rapidly.
*  Invalidating properties are useful for those properties that are expected to be updated more frequently than they are actually used, or that have a very large representation (large arrays or structures). In these cases, it may save network bandwidth to not send the new property value along with the invalidation message.
*  Updating properties are useful for those properties that are expected to be used more frequently than they are updated.

When in doubt, use an updating property.
++++

++++ Time-based properties should apply characteristics consistent with their usage. |
Time-based properties fall into one of 4 different categories.  Each category is comprised of a combination of 2 different sets of characteristics:

*  The Epoch or timebase to which the property's value is relative:
    * *Global Epoch* -- The globally accepted epoch for AllJoyn: 00:00:00 Jan 1, 1970 UTC.
    * *App Defined Epoch* -- Used for conveying contextually relevant time differentials.

*  Whether or not the property's value changes with the progression of time:
    * *Fixed* -- Property's value does not change as time progresses.
    * *Progressive* -- Property's value changes in step with the progress of time.

 | ^ Fixed         ^ Progressive     ^                  
 | -----------------------------------                  
 | Global Epoch      | *TimeStamp* | *Now*         |
 | App Defined Epoch | *TimeSpan*  | *Timer*       |

Time category definitions:

*  *TimeStamp* -- This is a fixed time in the future or past.  This is typically used to mark the beginning of an event.  E.g., the conference call starts at 9:00 am July 10, 2015 PDT.

*  *TimeSpan* -- This is a fixed time delta or difference between 2 time stamps.  This is typically used to indicate the duration of an event.  E.g, the conference call will last 1 hour.

*  *Now* -- This is the current date and time.  Each observation of this kind of property will yield a new value.  E.g., the wall clock.

*  *Timer* -- This indicates the time until an event will happen or the time since an event happened. E.g., an egg timer, stopwatch, or NASA mission time.

Time properties that have the *Progressive* characteristic should set the ''EmitsChangedSignal'' annotation to ''false''.  Time properties that have the *Fixed* characteristic may set the ''EmitsChangedSignal'' annotation to ''true'' or ''invalidates''.
++++

++++ Strive to use read-only properties. |
As a rule of thumb, strive to define properties as read-only.  Properties represent the state of an object, methods allow you to manipulate that state.  Typically, the outcome of a method call will be reflected by a change in the object's observable state, and hence by a change in value for the object's properties.

If it is conceptually possible to manipulate a property in isolation, then declaring the property read-write is warranted as a convenience. As an example, an audio playback device may have a Volume property. It is perfectly acceptable to make this property read-write.
++++



### State vs. Events

++++ Use signals for events and properties for state. |
Signals are most useful for representing ephemeral occurrences related to the entities in the problem domain. Ephemeral occurrences are facts that are true at a single point in time. A colloquial term for these occurrences is *events*. One can contrast this with the observable *state* of the domain entities, which remains true over a longer period of time. That state is, as argued before, best modeled as a set of properties.

For example, in a home security system, one of the domain entities is a door. A door has observable state: a location, whether it's locked, whether the door is open or closed. These aspects of the door are represented as properties in the Door Interface.  The fact that someone is walking through the open door, on the other hand, is definitely an event: this is true at this point in time, but in two seconds, that same person is no longer walking through the door. Hence, the PersonPassedThrough event would be modeled as a signal in the Door Interface.
++++

++++ Use intrinsic state and events over derived state and events. |
Intrinsic state refers to the natural state of being for the system being modeled.

Intrinsic event refers to natural events from the system being modeled.  There are actually 2 kinds of intrinsic events: those that result in state change and those that do not alter state.  In AllJoyn, intrinsic events that change state are conveyed with the PropertiesChanged signal since state is conveyed via properties.  Intrinsic events that do not alter state will need to be sent as their own signals.

As an example of intrinsic state, consider a door.  A door has 2 intrinsic states: open or closed.  An example of derived state would be that the door was opened for X time.  Such state is derived by observing the state transition from closed to open and starting a timer.  The value of that timer is the derived state.

Systems with more than one intrinsic state inherently have at least one intrinsic event to convey the transition from one state to the other.  In the case of the door, there are 2 such state transition events: door opened and door closed.  An example of a derived event could be that the door was left open for 5 minutes (derived from a 5 minute timer that started as a result of the door opened event and that the door closed event was never received before the timer expired).

For intrinsic events that do not alter state, consider a turn-style.  The intrinsic event with a turn-style is that a person passed though.  While most mechanical turn-styles include a counter, that count of the number of people who passed through is derived state.  A turn-style could ring a bell instead of increment a counter.  Regardless of what other functionality a turn-style has it will always process the event of a person passing through which is what makes that the intrinsic event.
++++


## Common Patterns

### Units

++++ Units are Non-negotiable. |
For every type of quantity (temperature, humidity, length, mass, ...) that is represented in your data model, the intended unit must be defined up front. All implementations of the interface must present values in the defined unit.
++++

++++ Use SI units where possible. |
SI units are defined by the BIPM: [http://www.bipm.org/en/measurement-units/](http://www.bipm.org/en/measurement-units/).
++++

++++ Reuse the same unit chosen for the same quantity existing used in existing standardized interfaces. |
This guideline aims to promote consistency across different interfaces.  Deviate from this guideline only where it really makes sense for the problem domain at hand.
++++

++++ Adhere to this list of agreed-upon units. |
 | Quantity           | Unit                                                                                | 
 | --------           | ----                                                                                | 
 | Absolute timestamp | The int64 value denoting the number of microseconds since midnight Jan 1, 1970 UTC. | 
 | Bandwidth          | Bits per second                                                                     | 
 | Data size          | Bytes                                                                               | 
 | Temperature        | Celsius                                                                             | 
 | Language           | IETF language tag                                                                   | 

++++

++++ Represent physical measurements with floating-point values. |

**Note** A previous version of these guidelines recommended the use of fixed-point representations for physical measurements.
++++



# Designing for Evolution

++++ Don't evolve if you can augment. |
In many cases it is better to define an auxiliary interface than to truly evolve an existing interface.  There are no hard and fast rules for this, this is the kind of judgment call that requires a lot of [Fingerspitzengefühl](http://en.wikipedia.org/wiki/Fingerspitzengef%C3%BChl).
++++

++++ Never remove obsolete members of an interface. |
Regardless of how long an interface member has been considered obsolete, it must be supported since an implementation that uses that interface may only know how to use the obsolete member.  You can never assume that all implementations will be updated to use the newest version of an interface.
++++

++++ Never change the signature of existing interface members. |
Again, the implementer of an interface has no control over when the users of that interface will be updated.
++++

++++ Do not add proprietary extensions to a standardized Interface. |
Define an auxiliary interface instead.

Obviously, the reversed domain name prefix of the auxiliary Interface must not be ''org.alljoyn''. Do make sure there is a clear link between the name of the auxiliary Interface and the name of the standardized Interface it extends.
++++

++++ Every standardized Interface must include a read-only uint16 (signature ''q'') property ''Version'' that indicates the implemented version of the Interface. |
This property is used at run time to determine the capabilities of the object offering the Interface. The value of this property must never change at run time: it is tied to the version of the interface that is actually implemented by a producer.

A note about the ''org.freedesktop.DBus.Property.EmitsChangedSignal'' annotation for the ''Version'' property: ideally, the value for this annotation is ''const'', but this value, while specified by DBus, is not supported in AllJoyn. Support for this value is under way (see https://jira.allseenalliance.org/browse/ASACORE-2254), but until the ''const'' value is actually supported, the recommended value for this annotation is ''true''. This will allow the Version property to be cached by consumers - there is no need to fetch it every time the value is needed.
++++

++++ Backwards compatibility must be preserved. |
Existing annotations and attributes are only permitted to change where they would not affect interoperability.   For example, changing a description to be more clear, or changing the EmitsChangedSignal annotation value from “true” to “const”, should not affect interoperability with a peer using an earlier version, but changing the name of a well-known dictionary key, or the value of a org.freedesktop.DBus.Method.NoReply annotation, or changing the signal emission behavior all adversely impact interoperability.
++++


# Designing for Security

++++ All Interfaces ought to be secured. |
The description of any interface not marked as secured must contain justification for not requiring security.

An interface is marked as secured by adding the ''org.alljoyn.Bus.Secure'' annotation to the interface description.

For more information about the AllJoyn security mechanisms, see [the section about Security in the AllJoyn System Description.](https///allseenalliance.org/developers/learn/core/system-description/alljoyn-security)
++++

++++ Never send private or sensitive information in the clear. |
Below are a few examples of information that should be protected:


*  Personal identity (names, government ID numbers, biometrics, etc).

*  Location of people

*  Activities of people

*  Passwords and other kinds of security keys

*  State of security devices (e.g., door unlocked)

Note that this list is **not** comprehensive.  It is meant to only provide ideas for the kinds of information that should be protected.
++++
# Interface XML Language

++++ Specify interfaces using the unified AllJoyn Introspection XML language. |
See the [AllJoyn Introspection XML](irb/xmlv2) spec for details on the interface XML language.
++++
