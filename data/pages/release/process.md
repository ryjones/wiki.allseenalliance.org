# Release Process

The goal of the AllSeen Alliance release planning process is to define a straightforward way to ensure work groups and projects can coordinate with each other. This is done through simple, clear, public declarations of what contributors will do and when, and with updates showing when work is complete. Mature work groups publish a Release Plan at the beginning of the release cycle, update Release Status as work proceeds, and publish a Release Review just prior to the release. These documents should be short, simple, and publicly accessible.

### Release Cycle

The AllSeen Alliance Core Working Group releases code on a six month cycle, with major versions every April and October. Bug-fix versions may be released for high priority bugs and security issues. 

Each service will release as determined by their associated work group and be based on the prior Core release.  For example, if the last release of Core is 14.02, then the service release would leverage that Core build and be labeled as `<Service>`-14.02


*  Major releases are numbered with the two digit year and month: **14.02**, **14.06**, **14.12**, **15.04**, etc.


*  Minor service feature releases add a third numeric value: 14.02.**01**, 14.02.**02**\\ Minor releases should only add new features, and need to be reverse-compatible with previous service releases having the same year/month numbers in the version. For example, code written for service version 14.02.01 should continue to compile and run with service version 14.02.02.\\ The core standard and thin libraries do not make minor feature releases.


*  Bug fix releases add a letter: 14.06**a**, 14.06**b**, 14.06.01**a**\\ These releases are interchangeable. There are no feature changes, developer API changes, or AllJoyn interface changes. In general the most recent bug fix release should be used for development.

A service might have this sequence of release numbers:

*  **14.06**: First release based on the 14.06 core

*  **14.06a**: Bug fix release with no new features relative to 14.06. Only critical fixes addressing issues like security, memory leaks, or crashes.

*  **14.06.01**: Feature added, but service still uses the 14.06 core. Contains all changes from 14.06a.

*  **14.12**: First release based on 14.12 core. May contain new features, or may simply have the same features as 14.06.01 but validated to work with the 14.12 core.

### Work Group Release Ownership

Each work group designates two representatives for each release interval, a Development Lead and a QA Lead. Both leads are designated by the work group chair and must be employed by AllSeen Alliance member companies. They must sign off on the release when it is ready. 

The Development Lead is responsible for the Release Plan, Release Status, and Release Review documents that are posted on the wiki. They are the point of contact for release issues and coordinate with other work group leads.

The QA Lead is responsible for the Test Plan and Test Results documents that are posted on the wiki.

### Documents


*  Release Plan
    * [ Plan Template](release/template/Plan )
    * Contents
      * Introduction
        * Name working group dev lead and QA lead for this release.
      * Deliverables
      * Milestones
        * API Freeze, Feature Freeze, Documentation Complete, QA Complete
        * Different freeze milestones may be defined for specific features to allow dependent work groups to set meaningful milestones. For example, another Work Group may need a specific API to begin work, so that API may have an earlier milestone than other APIs. 
        * In general, keep the number of milestones low to ease tracking
      * Expected dependencies on other work groups
      * Compatibility with previous releases
      * Themes and priorities

*  Release Status
    * [ Status Template](release/template/Status )
    * Provide ongoing project status for the current release cycle
    * Show milestone status
      * Date milestone met
      * Changes to expected milestone dates
    * Any changes relative to plan, including dropped features due to schedule
    * Schedule changes due to work group dependencies

*  Release Review
    * [ Review Template](release/template/Review )
    * Contents
      * Features
      * Non-code aspects
        * User documents, examples, tutorials
      * Architectural issues
      * Security issues
      * Quality Assurance
        * Test coverage
      * End-of-life
        * Newly discontinued APIs or features
      * Known issues
      * Standards compliance
      * Schedule post-mortem
        * Compare actual project milestones and results to the published Release Plan estimates

### Products


*  Release announcements

*  Tag applied to all git repositories

*  Source tarballs

*  Update web content with latest documentation

*  Future: Binary SDKs

### Notes

These procedures were adopted during the October 2013 Technical Workstream meeting.
