# Deprecated

The document you are viewing is the draft 1.0 version of the Interface Design Guidelines. It is no longer maintained, and slowly getting out of date. It is preserved on the wiki for historical purposes, the discussion at the bottom of the individual subpages may still be of some relevance.

The officially approved current version of the Interface Design Guidelines is at all times linked from the [IRB home page](/interfacereviewboard).

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

*  `<del>`overload existing signals and methods, where the argument list of the overloaded version is constructed by appending arguments to the argument list of the existing version of that signal or method. FIXME((TODO this is not true today, I think. But it is on the table for 15.04. To be confirmed by the Core WG.))`</del>`

The following things are expressly forbidden:

*  remove existing members

*  change member signatures

*  `<del>`create overloaded signals and methods where the argument list is altered in any other way than by appending arguments.`</del>`


~~DISCUSSION~~

