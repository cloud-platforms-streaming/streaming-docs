# Streaming Guide

Streamers are the ones that mux everything together out to the internet. Streamers are the folks that are responsible for getting everyone that's joined a Zoom call, adding in any customizations via [OBS](http://obsproject.com/), and streaming that feed out to the internet.

Streamers are the ones that will be making sure the content lands on Twitch/YouTube/Facebook/Twitter/etc.

**Some requirements must be met to stream.** As such we have [a series of producers](continuity.md) to help cover the needs of the channel.

## Bandwidth

If you have a lower end upload speed, streaming is possible but 720p and 1080p streams require at least 5 Mbps of upload bandwidth. Keep in mind, other things on your network contend for this bandwidth. Also, you'll be watching the stream too which takes additional bandwidth. It racks up fast so your mileage may vary.

While we don't intend to stream in 4K, it's worth mentioning, the upload bandwidth requirements for broadcasting 4K video is 25 Mbps.

## Equipment

Keep in mind; you can stream and participate with a wide variety of devices and hardware. What you have right now as someone who participates in meetings remotely regularly likely has good enough equipment to join in a stream. However, some regular streamers will probably be filling a [Guest](README.md#Guests) and/or [Producers](README.md#Producers) role as well. If you don't have enough compute and video power to pull this off, a two computer set up is suggested.

### Two computer set up

Streamers will need to consider how they will both broadcast a stream while participating in it (either in one of the streaming platforms and/or Zoom). While this is possible with a powerful enough setup, many Streamers choose to use two computers; one to stream the OBS feed and the other to participate in the Zoom call and streaming platforms.

#### Computer A

Computer A will be the box from which you speak, present, etc. to the audience on the stream. You'll connect to Zoom with this computer and use the microphone and camera on this machine. You will likely have the chat(s) for the streaming platform(s) open here as well.

#### Computer B

Computer B will be the machine that runs [OBS](https://obsproject.com/) to broadcast the Zoom call to the streaming platform(s). This computer should be able to handle the demand of encoding video feeds and streaming them. For example, an 8th generation Intel i3 is the bare minimum platform being recommended.

The good news is there are other people that have figured this out, so do not feel like you have to do it all yourself. If you have questions, ask away in an Issue or PR (or DM is fine too).

### Three device set up

Building on the Two computer set up, you can also have a third computer that could be used as a remote client. This client device would be in charge of managing the system OBS is running on remotely. This reduces CPU usage on the computer being used to connect to Zoom so it those resources can be used to run demos from or do other screen sharing.

This isn't a common use case, but it's possible and viable should you need it.

### Equipment suggestions

With that in mind, if you're going to be a regular [Guest](README.md#Guests) or Streamer we've assembled a list of suggested equipment to help improve the experience for our viewers.

For a tiered list of suggested equipment, see our [Streaming Equipment](pdf/streaming-equipment.pdf) guide.

Twitch also has its own [Hardware Recommendations](https://www.twitch.tv/creatorcamp/en/setting-up-your-stream/hardware-recommendations/) if you'd like to compare options.

There is a good presentation put together by the brand team that will help you make the most of your physical appearance. Ideally, you have a decent mic, good lighting, and are wearing Red Hat or neutrally colored clothing: [Webcam Video
Best practices for presentations](https://docs.google.com/presentation/d/1xnW3hm-jDfwrqma-1j8vzmq4an1mJMk0Y2hQfUkKss4/edit#slide=id.g547716335e_0_260) (Red Hat only).

TODO: open source this guide or some version of it

## OBS

[OBS](https://obsproject.com/), short for Open Broadcaster Software, is an open source project designed to making streaming easier and more professional looking. OBS is the interface to streaming services like Twitch, YouTube, etc. There are a number of useful resources across the web to help you get up and running with OBS or one of its forks. We'll provide the best here along with specific configuration settings that are needed.

All assets that are consumed by OBS for the stream are in the [**streaming-tools**](https://github.com/cloud-platforms-streaming/streaming-tools) repo

### OBS Quick References

Note: For Fedora users, the RPMFusion OBS should be used as the Flatpak has some issues with the required plugins.

* [OBS Forum Resources](https://obsproject.com/forum/resources/)
* [General Performance And Encoding Issues](https://obsproject.com/wiki/General-Performance-and-Encoding-Issues)
* [Streaming with Open Broadcaster in YouTube (LinkedIn Learning)](https://www.linkedin.com/learning/learning-video-live-streaming/streaming-with-open-broadcaster-in-youtube)
* [GPU Overload Issues](https://obsproject.com/wiki/GPU-overload-issues)

### OBS Scene Creation

#### Cropping

Cropping inputs is something that you'll find yourself doing quite a bit of in OBS as you're building scenes. The "ALT crop" (Option key on Macs) is a great way to get a crop *just right*. When editing a source, hold the ALT (Option on Mac) key and grab any point in the frame to crop it to suit the scene. Once you have your crop just right, it's encouraged that you do a "Fit to Screen" (CTRL/CMD+F) to make sure the crop is the best you can make it.

For those comfortable with photo editing, this might feel a little awkward, but the outcome is similar. You might notice a black box (letterboxing) around your object as you're positioning it. This is due to the resulting image not fitting the aspect ratio of the screen being streamed. Keeping crops at a 16:9 aspect ratio will help with black boxes.

* [How To CROP, RESIZE And STRETCH In OBS Studio! Easy (YouTube)](https://youtu.be/qEKBaeTJfpc)

### OBS Settings (aka problems and how to fix them)

#### (Linux) Browser Plugin

In order to use various overlays and alerts on Twitch, a browser plugin is available. This plugin does not ship for Fedora and must be installed. Other operating systems already have a browser plugin packaged. For Fedora, simply follow the [binary release installation instructions](https://github.com/bazukas/obs-linuxbrowser#installing-binary-release).

#### Video Settings

**Broadcasting in 1080p at 30 fps** is the goal. To get that set up, Open Settings, Video. Then make sure the settings are for 1080p (1920x1080) and 30 fps.

![Settings -> Video](img/1080p-settings-video-resolution.png)

#### x264 CPU Usage Preset

If your on stream video is laggy, lagging significantly, or jittering tuning the x264 CPU Usage preset on your device might help.

The bitrate should be set to 4500 Kbps due to the 1080p@30fps requirement. This bitrate is the amount of data you send when you stream. If you have an upload speed of less than 4500 Kbps, you should not be a [Streamer](https://github.com/cloud-platforms-streaming/streaming-docs#streamers).

You should be using a setting of veryfast (but superfast or ultrafast might be necessary depending on your setup). The higher the setting the better performance. But, the lower the quality; there's a sacrifice. This is device-specific; testing is required. "The image may look a bit blockier or pixelated, but you will be able to retain your resolution/fps."

There is also a worthwhile **Tune** option in the Output settings. If you're streaming content, configuring the x264 Tune option to `zerolatency` should help performance.

![Settings -> Output -> Streaming](img/settings-output-streaming.png)

Reference: [Twitch Broadcasting Guidelines](https://stream.twitch.tv/encoding/)

#### Sound Settings

In general, sound quality is the most important part of a livestream. If the sound isn't pleasant and of high-quality, people tune out. Much like radio, silence is bad. When in doubt, talk about whatever plugins are being used by the person showing their screen or ask for some more color around a particular feature or setting.

General OBS sound settings should be set to 48 kHz and Stereo. Some services support a full 5.1 surround sound experience but, unless you intend to use 5.1 channels of audio during your production, keep it in Stereo.

![Settings -> Audio](img/settings-audio.png)

#### Error: `Encoding overloaded! Consider turning down the video settings of using a faster preset.`

This is a common error usually related to the stress that video encoding is putting on the system.

Downscaling the output resolutions to 720p is the biggest thing that can be done to fix this. This is a huge sacrifice to video quality though.

Try to see if there are updated drivers available for your system. At the very least, reach out to @chris-short for help here because ***720p isn't good***.

![Settings -> Video](img/720p-settings-video-resolution.png)

TODO:

* Streaming key acquisition
* Scenes and more assets (D. Russo helping with animations)
* Add more resources, hints, and refined settings (almost done)