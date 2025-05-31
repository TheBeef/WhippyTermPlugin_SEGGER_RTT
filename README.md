# WhippyTermPlugin_IODriverRTT
A WhippyTerm IO Driver for SEGGER RTT connections

This is a plugin for WhippyTerm (https://whippyterm.com) that adds support for SEGGER's Real Time Terminal (RTT).
RTT is a technology for interactive user I/O in embedded applications
(https://www.segger.com/products/debug-probes/j-link/technology/about-real-time-transfer/).

# Installing
Download the plugin, start WhippyTerm and select the "Plugins->Install Plugin" menu item.
Select the .wtp file and click open.

You must have the JLink tools installed for the plugin to work.  You can go to https://www.segger.com/downloads/jlink/
to download and install the needed tools.

When the plugin is started (when WhippyTerm loads) it will search for the .dll (or .so).  On Linux it will try to
load /opt/SEGGER/JLink/libjlinkarm.so.  On Windows it will search for one in xxxxxxxxxxx

