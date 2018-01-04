# Objective

To compare the performance of NameService between 14.02 and 14.06. 14.06 implements NGNS which is aimed at improving performance of discovery and sessionless-based signals.

*Note: This is the first time ever that Seattle test team has run a scalability test involving:*

*  *About Announcement signals*

*  *Wireless medium*

# Task specification

A consumer that is interested in receiving ''org.alljoyn.About::Announce'' signal from providers implementing a particular interface ''I1''.

*  A test program was written to accomplish this task using 14.02 SDK\\ The Announce handler checks each and every received Announcement and filters out the ones that implement ''I1''.

*  A test program was written to accomplish this task using 14.06 SDK\\ The RegisterAnnounceHandler is called with ''I1'' as a parameter\\ *(It takes lesser lines of code to accomplish task in 14.06 due to the support added in AllJoyn About Standard Core Library.)*

# Details of Setup

 1.  Providers in the network running as distinct processes on four different Linux machines.\\ *(For eg. 32 providers distributed into 12, 12, 4, 4 - as per the strength of each machine)*
 2.  One Consumer running on a fifth Linux machine *(measurements are made at the consumer's end)*
 3.  All the five machines are connected to an access point via wireless

# Test iteration

Each test iteration consists of the following steps *(as taken from 14.06 NGNS HLD)*:
 1.  Start 32 Providers, where 16 providers implement ''I1'' and 16 providers implement ''I2''. There is one Announce signal from each Provider. \\ // Note: Each provider exits after 80s for the purpose of simpler test automation. //
 2.  Sleep for 45 seconds to ensure that all NameService traffic associated with Announce is completely sent out. \\ *In case of 14.02, where scheduled advertisement interval is ''0s...40s...80s'' and so on, no traffic will be sent for a duration of 35 seconds when above sleep completes.*
 3.  Start one Consumer on DUT looking for providers that implement ''I1''.\\ *Note: Consumer exits after 30s. That is, what is received with in 30s counts. What isn't received, isn't received. We need to choose some timeout and we chose 30s. There is no loss of generality here as we are making a relative comparison.*
 4.  Sleep for some more time till all Providers exit.\\ *This is done to avoid Providers from one run interfering with the next run.*

# Test Results

Test was launched to run for 200 iterations *(i.e. 200 test runs for 14.02 and 200 test runs for 14.06)*. However, due to DUT's wireless adapter giving up on us, the test stopped at 133 iterations *(the number of results is still significant enough to draw conclusions)*.

## Number of Announce signals received

For each test run, 16 About Announce signals are waiting to be taken (1 signal from 16 separate producers - i.e. 16 separate fetches per consumer are required). Thus for 133 iterations, it is a total of 2128 Announce signals which can be received. The following table shows the comparison between 14.02 and 14.06, for the total number of Announce signals received:

 | Release | Absolute Number of Announce\\ Signals Received | % of Total signals | 
 | ------- | ---------------------------------------------- | ------------------ | 
 | 14.02   | 1525                                           | 71%                | 
 | 14.06   | 2040                                           | 96%                | 

Consider the questions viz. In how many iterations were all the 16 signals received? How about the number of iterations in which at least three Announce signals were received? The following graph displays the minimum number of Announce signals received on the x-axis and the number of iterations on the y-axis

{{:core:received-signal-count.png|}}

The above graph was generated based on the following table *(each cell indicates the number of iterations out of a total of 133 iterations)*:
 | Minimum Number of Announce\\ signals received | 14.02 | 14.06 | 
 | --------------------------------------------- | ----- | ----- | 
 | 1                                             | 133   | 133   | 
 | 2                                             | 133   | 133   | 
 | 3                                             | 133   | 133   | 
 | 4                                             | 131   | 133   | 
 | 5                                             | 118   | 133   | 
 | 6                                             | 116   | 133   | 
 | 7                                             | 113   | 133   | 
 | 8                                             | 111   | 133   | 
 | 9                                             | 109   | 133   | 
 | 10                                            | 104   | 131   | 
 | 11                                            | 71    | 127   | 
 | 12                                            | 65    | 127   | 
 | 13                                            | 60    | 127   | 
 | 14                                            | 56    | 126   | 
 | 15                                            | 43    | 118   | 
 | 16                                            | 29    | 87    | 

## Average duration to receive Announce signals

Announce signals involve discovery of Providers, followed by the retrieval of signals via ''SessionlessObj'' *(using JoinSession)*. The following graph displays the minimum number of Announce signals received on the x-axis vs. the average duration it took to receive them on the y-axis:

{{:core:average-time-taken-to-receive-annonce-signals.png|}}

The above graph was generated based on the following table *(each cell indicates the average duration to receive the signals in milliseconds)*:
 | Minimum Number of Announce\\ signals received | 14.02   | 14.06  | 
 | --------------------------------------------- | -----   | -----  | 
 | 1                                             | 1619ms  | 390ms  | 
 | 2                                             | 1849ms  | 467ms  | 
 | 3                                             | 2512ms  | 512ms  | 
 | 4                                             | 3895ms  | 811ms  | 
 | 5                                             | 9227ms  | 1973ms | 
 | 6                                             | 10026ms | 2322ms | 
 | 7                                             | 11326ms | 2422ms | 
 | 8                                             | 12909ms | 2893ms | 
 | 9                                             | 13860ms | 4540ms | 
 | 10                                            | 15296ms | 5379ms | 
 | 11                                            | 19811ms | 6978ms | 
 | 12                                            | 20884ms | 7139ms | 
 | 13                                            | 21990ms | 7523ms | 
 | 14                                            | 23165ms | 7715ms | 
 | 15                                            | 24723ms | 7947ms | 
 | 16                                            | 25459ms | 8998ms | 

*Note: How are the above time values calculated when some of the expected 16 Announce signals weren't even received? For every signal that is not received, the time at which it is received is set to 30s (the time after which Consumer exits). To avoid too many artificial settings of time values, this is only applied to the difference in number of signals between 14.02 and 14.06.*
