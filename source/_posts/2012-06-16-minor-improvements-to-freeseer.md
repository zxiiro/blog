title: Minor improvements to Freeseer
date: 2012-06-16 02:52:15
tags:
- freeseer
---
This week I made some minor additions to Freeseer closing some old bugs. Notable ones include the following:

**Auto-Selection of Talks**

Since Freeseer is able to store the date/time of each talk via the TalkEditor we can use this data to discover which talk is most likely being recorded next. The idea for this feature is that when the user presses the STOP button, Freeseer will do a search in the database within a 15 minute window from the time the STOP button was pressed and see if there's any upcoming talks for the event-room that the user is currently recording in and automatically select it from the dropdown box. This minor addition makes the recording process slightly more automated for our volunteers at events when they are recording. You can read more about this commit at this <a href="http://github.com/Freeseer/freeseer/commit/06d14c57645917da963c924cd23c66717583ef2d">link</a>.

**Elapsed Time Display**

Another much needed feature that was added is an Elapsed Time Display which shows the user how much time has elapsed since the recording was started. At events often times volunteers are also time trackers and this feature should assist the volunteer determine if a talk is going on for too long or not.

![elapsed](elapsed.png)

As you can see in the image the Elapsed Time is placed in the bottom right corner in the statusbar of Freeseer. You can read more about this commit at this [link](http://github.com/Freeseer/freeseer/commit/fe8523de1a69ed794b36203b21f0b9f2c2355e5f).

**Test Video Source Improvements**

The testvideosrc plugin was also improved to support patterns and live mode. Patterns will let you select from a choice of various image patterns supported by the plugin while live mode will allow the test source to act as a live video source. This should be useful to simulate a webcam device when you don't have a working webcam handy.

While I've only discussed in this post the most notable changes this week but if you would like to see a full list of changes that happened this week you can always look at the commit history [here](https://github.com/Freeseer/freeseer/commits/experimental).
