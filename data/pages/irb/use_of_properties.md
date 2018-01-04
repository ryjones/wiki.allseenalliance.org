### Use of Properties

This section covers some best practices for the use of Properties in Interfaces.

#### Properties Represent Externally Observable State

As discussed in the [object granularity](Object Granularity) section, different bus objects represent different entities in the problem domain. The various Interfaces represent various aspects of those entities. The properties defined in an Interface represent the observable state of an aspect of an entity.

In theory, an observer of the bus object (i.e., a client application) should be able to infer everything it needs to know about the state of that bus object from the object's properties.

#### Types of Properties

Properties come in three flavors, based on their associated org.freedesktop.DBus.Property.EmitsChangedSignal annotation value:

*  "true" defines an *updating* property. Whenever the value of such a property changes, the bus object will emit the org.freedesktop.DBus.Properties.PropertiesChanged signal with the new property value.
*  "invalidates" defines an *invalidating* property. Whenever the value of such a property changes, the bus object will emit the org.freedesktop.DBus.Properties.PropertiesChanged signal, but the new property value will not be specified.
*  "false" (the default value if the annotation is not present) defines a *non-cacheable* property that never causes the org.freedesktop.DBus.Properties.PropertiesChanged signal to be emitted.

Updating and invalidating properties are cacheable. Clients can rest assured that the values they acquired for those properties remain valid until a counter-notice (in the form of the PropertiesChanged signal) is received. Non-cacheable properties must be retrieved from the remote bus object every time they are needed, which may incur significant network traffic and latency.

The Data-driven API for AllSeen, for example, will automatically cache all cacheable properties for discovered objects on behalf of the application.

As a rule of thumb:

*  Non-cacheable properties are only really useful for properties that change very rapidly, making the emission of the PropertiesChanged signal impractical. For example, the received byte counter on an Interface representing a network interface changes very rapidly.
*  Invalidating properties are useful for those properties that are expected to be updated more frequently than they are actually used, or that have a very large representation (large arrays or structures). In these cases, it may save network bandwidth to not send the new property value along with the invalidation message.
*  Updating properties are useful for those properties that are expected to be used more frequently than they are updated. Constant properties (for example, the Version property that is defined for each Interface) should also be marked as updating properties, to indicate that they are indeed cacheable.

When in doubt, use an updating property.

#### Do Not Use Methods to Emulate Properties

> **Use properties to represent externally observable state. Do not use methods to emulate properties.**

It is possible to emulate properties by creating dedicated "getter" methods. For example, instead of having a Color property, an Interface might define the GetColor method. Refrain from doing this.

The first argument against dedicated getter methods is simply consistency. The property mechanism exists, so use it.

The second argument may be more material: the property mechanism allows for the annotation of cacheable properties, which is not possible with dedicated getter methods.

If an object's observable state is so large that it really cannot be represented in a set of properties, a getter method that retrieves subsets of the state may be warranted. However, objects with such a large state should raise a warning flag: perhaps it is better to further decompose this object into smaller objects?

#### Writable Properties

As a rule of thumb, strive to define properties as read-only. Properties represent the state of an object, methods allow you to manipulate that state. Typically, the outcome of a method call will be reflected by a change in the object's observable state, and hence by a change in value for the object's properties.

If it is conceptually possible to manipulate a property in isolation, then declaring the property read-write is warranted as a convenience. As an example, an audio playback device may have a Volume property. It is perfectly acceptable to make this property read-write.

> **Do not ever, in any case, define write-only properties.**

A write-only property is just a badly disguised method.

~~DISCUSSION~~
