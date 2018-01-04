## AllSeen Node.js Project Proposal

#### Project Description

* *What is the purpose and intent of the project*

* *Include any architecture diagrams or specifications*

* *How will it benefit the community*

This project will create an AllJoyn NPM module to be published via http://npmjs.org for use with Node.js (http://nodejs.org). The AllJoyn Node.js NPM module could be used by hobbyists, makers, hackfests, the open source connected car, and various other products.

The initial goals are to help:


*  Teach people AllJoyn - high school or university level.

*  Create a hackfest asset, i.e. @IoTPHX, @NodeAZ, @HeatSyncLabs, @localmotors, AT&T Hackfest Sept 6-7 (http://attcarhomehackathon.com)

*  Integrate with different Node.js platforms and projects, like AllJoyn Nodebots (http://nodebots.io/)

There is some discussion of this plugin being leveraged by Gateway Agent APIs. Node.js has been very effective for bridging and gateways, especially in the Node-RED and Octoblu's NodeBLU variants which adapt Node.js for IoT with visual flow design.

#### Scope

* *What features and functionality will be developed*

* *How will the development be staged*

* *What AllJoyn interfaces will be developed*

* *What is the completion criteria*

The basic architecture uses node-gyp build a native Node.js addon to access the AllJoyn Standard Library core and basic service implementations.

Initial development will focus on creating a proof-of-concept that exposes essential AllJoyn features. As the project matures, the AllJoyn Node.js module will develop a feature set comparable to other AllJoyn language bindings will maintain compatibility with future versions of AllJoyn and Node.js.

#### Dependencies:

* *Identify existing projects this new proposal depends on*

* *Are there any external dependencies*


*  AllJoyn 14.06 core and base services

*  Node.js (version?)

*  node-gyp module

*  Node-RED (version?)

*  NodeBLU (version?)

#### Project Name

* *Proposed name for the project*

* *Proposed name for the git repository*

Proposed name: "AllJoyn Node.js"

Proposed git repository: devtools/aj_nodejs

#### Proposed Working Group:

* *Will this project be part of an existing working group or is a new working group being proposed*

* *Name of the working group*

* *Are any other projects being proposed in parallel for this working group*

We propose that this be done under the Developer Working Group. No other projects are proposed in parallel.

There is already a mailing list: [allseen-nodejs@lists.allseenalliance.org](https///lists.allseenalliance.org/mailman/listinfo/allseen-nodejs)

#### Committers and Contributors:

* *Name of and affiliation of the maintainer*

* *Names and affiliations of the committers*

* *Any other contributors*

* *What QA and test resources will be available*


*  Maintainer: Luis Montes of Octoblu

*  Committers: Luis Montes of Octoblu, Mike Young of Weaved

*  QA and Test Resources: Octoblu

#### Initial Contribution

* *Is there an initial contribution being made to the project*

* *If so what is the nature of the contribution*
    *//Specifications//
    *//Design documents//
    *//Code//
    *//Test plans//


*  Code

*  Specification for how to map AllJoyn APIs to JavaScript in node-gyp

*  Test code to exercise the plug-in to show it works correctly

#### Proposed Release Schedule:

* *When is the first release planned*

* *Will this align with the current release cadence*

Targeted to be part of the 14.10 Alliance release.
