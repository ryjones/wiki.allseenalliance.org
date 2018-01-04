# Time Service Framework Project Proposal

#### Project Description:

The Time Service will provide a common interface which allows devices to provide various time related services to the proximal network such as time of day, date, management of alarms and timers. 

Many devices of various types provide or can consume time related services from obvious alarm clock to thermostats, kitchen appliances and sprinkler systems.  It will benefit the consumer to have one common interface that allows the time to be set across all devices on the proximal network or even for new devices entering the proximal network to query other devices to determine the current time and date without the consumer intervening.

The architecture is simple client/server relationship between a device providing the service and the consuming device.
#### Scope:

There are three areas of functionality that will be provided, time of day/date, alarms and timers.

Time of day/date:
The Time Service will allow the time of day, date, time zone and day light savings time status to be read and set.

Alarms:
The service will allow multiple alarms to be created, edited and deleted.  The action to be taken when an alarm expires is left to the context of the device.

Timer:
The service will allow multiple count-down or count-up timers to be created, edited and deleted.  As with alarms, the action to be taken when timer expires is left to the context of the device.  For example, a cooking timer may "ding" when the timer expires, a fan may turn off.

The interfaces to be developed with be determined at the completion of the design but current expectation is that each functional area (time of day, alarm and timer) will be implemented in separate interfaces.

#### Dependencies:

The Time Service is anticipated to be released in the 14.10 release but no new functionality or other features are relied upon for this functionality.
#### Project Name:

The project will be called "Time Service Framework". It will be added as one of the base services under the allseen/services/base.git repository
#### Proposed Working Group:

Base Services Working Group
#### Committers and Contributors:

Committers:  

*  Josh Hershberg

*  Tsahi Asher

*  Adina Geffen
#### Initial Contribution:

The Java and C Thin Library code has been committed to the master allseen git repository. 
#### Proposed Release Schedule:

14.12 Base services release
