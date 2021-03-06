title: Optimizing Freeseer Controller GUI Design (Part 2)
date: 2012-11-14 02:09:50
tags:
- freeseer
- python
---
Last time we looked at redesigning the Freeseer Controller Client and found some nice ways to improve the design to make it more usable and neater. Since then I've pushed some code up for review which can be found at <https://github.com/Freeseer/freeseer/pull/225>.

Today I want to look at what can be done with the Controller Server GUI to make it neater. First lets take a look at what the server GUI looks like today.

![Current Controller Server GUI](server-01.png)

Couple things I noticed when playing around with UI that you can't see from the screenshot. File, and Edit menus don't seem to do anything. A quick look at the code behind finds that there's no code to support those buttons. Actually the Edit button has no options listed when clicked either. For this I think the Quit button in the file menu should be coded to close the app. The edit menu will likely change to a Language menu and allow the user to change languages of the UI via the menu.

The send message button seems pointless to me. What it does is sends a message to all clients connected to the Server but this message is shown as a log on the clients. I'm not sure if there's any real purpose for this and it adds complexity to the settings window for no reason. I'm thinking this will likely be removed.

The properties section at the bottom allows the user to copy text and paste it to something like email / IM etc... so that someone at the client end can copy paste it into the client settings. I think these properties can be simplified and take up less space.

This leaves us with Server settings (IP, Port, Passphrase) and the Client Controls (List, Buttons). We can save some screen estate if we utilize the toolbox like we did with the Client GUI. I also noticed the Port is not configurable, in the redesign I would like port to be a configurable option.

I made a mockup of some ideas I had for what I think can be improved upon below. First lets look at the new Server Settings tab.

![Server Settings](server-02.png)

Server settings now consists of simply the IP address, Port, and Passphrase (very similar to the redesigned Client Settings tab). I imagine the IP Address dropdown will be auto populated with IP addresses detected by the software including 0.0.0.0 (listen on all interfaces).

There is also a line edit below the "Status: " at the top. This is the new copy-paste dialog. When the user configurs the server this box will be auto-populated with the server settings in the format "passphrase@host:port" which can be copied and pasted and sent to someone configuring the client at the other end.

Next lets look at the Control Clients tab:

![Control Clients](server-03.png)

This tab looks very similar to what the interface for controlling clients that currently exists on the Controller Server GUI. By placing it in a tab though we can hide the settings and show just this tab once the server has started.

If anyone has any ideas on other improves please comment and let me know. I'm open to suggestions.
