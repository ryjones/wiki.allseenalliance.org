###  Project Description:

Tellient, an Allseen Alliance Community member that provides Internet of Things Analytics, (IoTA) proposes the following Project and Working Group to develop a new AllJoyn implementation of a device and gateway service that will enable device analytics on AllJoyn-enabled devices.

The Allseen Alliance represents a growing membership of companies focused on building connected devices. Enabling these devices to report usage data to derive insights from analytics will benefit device manufacturers and consumers alike. Device manufacturers and network operators will gain useful and actionable information about their devices, users and environments for R&D, Customer Service, Supply Chain Management and Decision Support, while consumers could view a quantified dashboard of their entire Alljoyn device-enabled ecosystem, adding value to these devices out of the box.

Analytics, while very important, is not a core competency of most device manufacturers, and our aim is to provide an off-the-shelf solution for the Allseen Alliance community that is easy deploy.
We propose this project to establish a standard API and an extensible library for device analytics to enable a simple and common approach to deployment at the client and gateway. Wherever possible, this project will leverage open-source components and best practices and the code contribution will be based on Tellient’s IoT-specific analytics experience, service and solution.
#### Scope

The scope of the proposed Analytics project is to deliver an open source API and a common implementation to enable the following:

- Provide device manufacturers with device-level capture and reporting of events, states and other defined data via a secure protocol and gateway to a server-side analytics engine

- Provide device owners the ability to view usage information about enabled AllJoyn devices on their proximal network

The specific deliverables from this project will be:

- Open-source IoTA device Client Library for AllJoyn (HLOS and RTOS versions)

- Gateway Service: Interfaces with IoTA client code and packages usage data to be sent outside the proximal network to a server-side analytics engine

- Associated documentation, samples and test harness

####  Dependencies

The 14.10 release includes the AllJoyn Gateway project, which represents a functional enhancement that would enable the Analytics Gateway Service. We would therefore expect to commit the Client Library and the Analytics Gateway Service for the 14.10 release.

#### Project Name:

The proposed name for this project is “Analytics” and the proposed git repository name is “analytics.”

#### Proposed Working Group:

We propose that this project establish a new working group called the “Analytics” working group. The proposed working group chair is John Hardin, VP of Engineering at Tellient.

#### Committers and Contributors:

####  Project Maintainer
John Hardin, Tellient
####  Committers

John Hardin, Tellient

Matt DiMeo, Tellient
####  Contributors

Dave Harry, Tellient
####  Initial Contribution

The initial contribution will consist of a document outlining our proposed technical design and approach, including the expected interface with the Gateway project and transport protocols. We expect this to kick off the project immediately following acceptance of this proposal.

#### Proposed Release Schedule:

Following comment by the community and ratification of the design and proposed architecture, the initial deliverable from this project will coincide with the 14.10 AllJoyn release with further components following, dates TBD.
