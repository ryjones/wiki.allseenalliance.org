# Developer Tools 14.12 Release Review

## Features

This version of the code generator adds:


*  DDAPI code generation

*  Android feature is supported (was experimental in 14.06).
    * The same data types as the thin library target are now implemented.

*  Named types in interface XML

*  Compatibility with core 14.12

*  Bug fixes

## Non-Code Aspects


*  [Wiki Documentation](devtools/code_generator)

*  [2014-03-13 Video Presentation and Training Slides](/Training)

## Architectural Issues

N/A

## Security Issues

N/A

## Quality Assurance

The code generator code base contains extensive unit tests.

In addition, manual tests were conducted across Linux and Windows platforms to validate generated programs and execution of the code generator itself.

Code generation for DDAPI has been extensively tested from within the Data-driven API project through the use of automated end-to-end system tests.
## Known Issues

There are currently (as this is being written) no known bugs. Bugs are recorded at https://jira.allseenalliance.org/browse/ASADT under the [Code Generator](https///jira.allseenalliance.org/browse/ASADT-1?jql=project%20%3D%20ASADT%20AND%20component%20%3D%20%22Code%20Generator%22) component.

There are some unsuppored AllJoyn data types for both Android and Thin Library:


*  Structures containing structures

*  Structures containing arrays

*  Structures containing dictionaries

*  Structures containing variants

*  Arrays of variants

*  Multi-dimensional arrays

## End-of-life

N/A

## Standards Compliance

N/A

## Schedule Post-Mortem

The release was made on the originally scheduled date.