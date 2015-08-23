title: Reporting in Freeseer
date: 2012-06-24 01:53:32
tags:
- freeseer
- python
---
Occasionally when doing a recording issues could occur such as the audio not working, video is not working or perhaps the presenter does not wish to be recorded. After a conference it is difficult for one person to know which talks have issues, especially if 100s of talks are recorded at the event.

To solve this issue Freeseer comes with a basic reporting tool that will allow the person recording to report issues with their talks inside the application. This will allow whomever is uploading the videos after the talk to quickly scan through and find which videos have issues.

To access the reporting interface, with freeseer-record open simply click **Help > Report**. The reporting interface will open a basic form for the currently selected talk.

![Reporting Interface](report-1.png)

The form has 3 fields which need to be assessed by the reporter.

1. A comment describing the issue seen
2. A type of issue, one of "No Issue", "No Audio", "No Video", and "No Audio/Video"
3. A checkbox indicating if a Release Form was received or not

The last item is a new feature we added for events where presenters must sign a release form indicating they are giving permission to record their talk. Typicially this option is used with the "No Issue" flag unless there are issues with the recording.

Freeseer also provides a **Report Editor** which will allow the organizer after the event to quickly browse through all the reports and find out which ones have issues.

![Report Editor](report-2.png)
