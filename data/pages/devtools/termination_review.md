# Code Generator Project Termination Review

The Developer Support working group proposes that the Code Generator project is archived, with the completed v15.09 release being the final version.
 
## Reason for termination

The code generator has had only minimal updates for the past year, to maintain compatibility with current core releases. However, the project requires significant work to be viable in the 16.04 timeframe:

   * Major updates to support the unified XML format for core 16.04 (https://jira.allseenalliance.org/browse/ASACORE-964)
   * Should use about-based discovery for AJTCL, the current best practice
   * The code generator creates Eclipse Android projects, but Android Studio is the current supported environment. While Android Studio can import older Eclipse projects, it would be better to support the current tools.

In addition, DDAPI support was removed for v15.09 and the only code generator committer is stepping down. Efforts to find a new committer in meetings and on mailing lists have not been successful.

## Impact on other projects, users and communities

 
The DDAPI project depended on the code generator, but was archived following v15.04.

For users and the community, the impact should be minor. There has not been significant code generator activity on mailing lists or the Q&A site.

With the AJTCL code reorganization in v15.09, the v15.09 code generator is likely to work with v16.04 and future revisions, until APIs used by the code generator are deprecated or toolchains change too much.
 
## Where should the project be archived?

 
The ''devtools/codegen'' repository will remain in place. The Code Generator wiki page at https://wiki.allseenalliance.org/devtools/code_generator will be updated to We will also do the same on the main wiki page for the DDAPI project, and in the DDAPI documentation that is published on [the Alliance documentation pages](http://allseenalliance.org/developers/learn/ddapi).
