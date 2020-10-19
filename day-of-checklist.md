# Live Stream Day of Checklist

## Pre-Event Logistics

1. Pre-schedule the Zoom call (you'll need a paid account or someone with one)
1. Copy the invite details into a calendar invite including your Guests, Producer, and Streamer with a fifteen minute setup time buffer ahead of the event.
1. Create an invite for the **public calendar**; include a description folks can use for social and add only redhatstreaming AT gmail DOT com to that invite. Include a link to [openshift.tv](https://openshift.tv) (NEVER the Zoom details)
1. A public calendar maintainer will make sure the invite for public consumption is published
1. You need a stream key for OBS (or otherwise capable software); ask Erik Jacobs or Chris Short through official Red Hat channels (if you're using Restream Live we can accommodate).

It's encouraged to test streaming with your own account(s) to get the hang of it

## Pre-stream

1. Establish a back channel to communicate with all participants. Slack or GChat can be used but make sure you're not spamming the live stream with notification sounds. Using the Zoom or BlueJeans chat (you're all in it automatically) has drawbacks as well (like displaying when there are messages publicly to the world)
1. Download the streaming-tools repo (put it in /opt/)
1. Linux users: Install the [Linux Browser plugin](https://github.com/cloud-platforms-streaming/streaming-docs/blob/master/streamers-guide.md#linux-browser-plugin)
1. Check your OBS scenes are configured correctly. Zoom launches two windows; make sure the right Zoom window is slecteed in the Main Zoom Scenes -> Mac/Linux Zoom Window
1. Rotate through the scenes make sure you're seeing what is expected
1. Get everyone on Zoom EARLY so you can test their setups, font sizes, screen sharing, etc.
1. Make sure Side by Side in Zoom Settings is enabled (buried in Zoom Screen Sharing settings)
1. Make sure you’re in Gallery View (not available until two people are on call)
1. Make sure font sizes look good when screen sharing
1. Update the title and description of the show in [Restream](https://app.restream.io/titles) (note: happens immediately; will impact content that's currently on air)
1. Make sure all the destinations are set correctly in [Restream](https://restream.io/channel) (note: the only thing that should be off is the Custom RTMP destination; that's for DevNation)
1. About 3-5 minutes before the scheduled stream start time; click Start Streaming on the “Starting Soon” Scene (unless of course you're still cat herding in which case it is recommend hitting the Starting Soon animation at the start time).

TODO: Need to figure out auto scene switcher and the auto unmutes

## Go Live

1. Ask participants to be quiet
1. Unmute all audio sources (minus the streaming box's mic if you're in a two computer setup)
1. Switch Scenes to "OpenShift Intro Bumper"
1. Once Intro Banner plays, switch to the Main Zoom Scene

## Ending the stream

1. Encourage folks to follow the channel
1. Point folks to the calendar at every chance
1. Tell people about upcoming streams
1. Switch scenes to "OpenShift Outro Bumper"
1. Once the bumper is complete, switch scenes to "Ended". Let that run for a few seconds.
1. Hit Stop Streaming in OBS
1. The stream is complete.

TODO:
* Have Erik review it
