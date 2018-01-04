### Audio Service Proposal

#### Project Description:

The Audio Service is a unified method for AllJoyn devices to discover and stream audio from a source device to an audio sink device, e.g., from a wireless doorbell to a speaker.


* Support for discovery of available audio content files

* Registering a listener for sink information

* Support for basic playback controls for pause, stop, play, volume up/down and mute.

* Support for retrieving audio metadata
Note that the Audio Service is already in the Git repository. This proposal is solely about moving it into the Base Services Working Group for support and maintenance.
 
#### Scope:

The Audio Service introduces two top level architectural components

* Source – A discoverable source of audio content
    *Enumerates audio content including media “types” and metadata 
    *Streams audio to a sink

* Sink – A discoverable audio player
    *Advertises capabilities
    *Receives streaming audio from a Source
    *Controllable, e.g., start, stop, mute, volume

#### Dependencies:

None

#### Project Name:

Project to be named “Audio Service”

Proposed git repo: multimedia/audio.git

#### Proposed Working Group:

Base Services Working Group

#### Committers and Contributors:

Gerry Rovnick, Josh Hershberg – both from QCE

#### Initial Contribution:

* Service code

* Samples

* High Level Design Document

* Usage Guide

#### Proposed Release Schedule:

14.10
