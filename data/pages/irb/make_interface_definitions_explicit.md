# Deprecated

The document you are viewing is the draft 1.0 version of the Interface Design Guidelines. It is no longer maintained, and slowly getting out of date. It is preserved on the wiki for historical purposes, the discussion at the bottom of the individual subpages may still be of some relevance.

The officially approved current version of the Interface Design Guidelines is at all times linked from the [IRB home page](/interfacereviewboard).

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

~~DISCUSSION~~
