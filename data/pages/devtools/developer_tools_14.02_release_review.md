# Developer Tools 14.02 Release Review

## Features

This is the initial release of the Code Generator. It creates AllJoyn Thin Library code from XML interface descriptions.

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

## Known Issues

There are some unsuppored AllJoyn data types:


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

The project was originally scheduled to release at the same time as v14.02 of the Core Thin Library, on February 28, 2014. Due to test team availability, the date was moved to the end of March, and then beyond March. Bug fixes and installation issues further postponed the release until June.

