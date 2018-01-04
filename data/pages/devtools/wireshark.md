# What is Wireshark?

Wireshark is a described as "The World's Most Popular Network Protocol Analyzer".

Wireshark 1.11 or later supports AllJoyn. This allows us to parse, filter, and display AllJoyn network traffic either in real time or save network packets to a file and examine it at our leisure or use it for other purposes such as attaching the data to bug reports.

Download and install Wireshark from here [http://www.wireshark.org/download.html](http://www.wireshark.org/download.html). Be sure to get version 1.11 or later.
## Android

The best approach appears to be running a packet capture program on the device and generate a .pcapng file to be loaded into your Windows or Linux version of Wireshark.

tcpdump for Android works on rooted devices. There are several apps in the store that would sort-of work, but tcpdump is the granddaddy app. A quick search on Bing shows it’s widely available.

You will probably need to use the flag "-s 0" with tcpdump. If you don't you will not capture the entire packet.

## AllJoyn Filters

To limit the network traffic being displayed to only AllJoyn traffic type bring up WireShark and in the "Filter:" toolbar type "aj or ajns" and then click "apply".

Other filters are available too. In the filter expression window type "alljoyn." and you will see the various AllJoyn data types available to filter upon. For example type, then apply "alljoyn.string.data". This will limit the packets shown to only packets that contain that date type. You can further filter upon values of that data type. For example you could apply the filter "alljoyn.string.data==org.datatypes.test" to see only packets which have have AllJoyn string data with values of "org.datatypes.test". You can construct some very detailed filters right done to the bit level in many cases with a filter like: "alljoyn.header.flags.allowremotemessages==true".

You can also build complex expression like:

"(aj or ajns) and ip.src==192.168.1.119 and alljoyn.string.data==BusHello"
## Flow Graphs

To see a sequence diagram click on menu item "Statistics", click on "Flow Graph", then click "Okay" on the dialog box that comes up. See FlowGraph.png in this directory for an example.

There is also a tool to generate a msc from pcap: [http://code.google.com/p/pcap2msc/](http://code.google.com/p/pcap2msc/)

Make sure your Wireshark installation is on your path then run this against one of the capture files and specify the following options:

pcap2msc.py sample.pcapng "aj" | mscgen -T png -o output.png

The file "sample.pcapng" can be any Wireshark captured file you have saved. The "aj" is a filter and can be any of the filters described above.
