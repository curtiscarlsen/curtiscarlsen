---
page-title: "Easily Converting Audio or Video Files To Text Transcripts - Greg Hilston"
url: https://www.greghilston.com/post/audio-or-video-to-text/
date: "2023-07-25 15:37:19"
---
We’ll be leveraging [Open AI’s Whisper package](https://github.com/openai/whisper) to achieve this. They will have documentation on how to set this up, but I’ve provided a few extra steps, to help act as “training wheels”.

-   You’ll want to ensure you have Python3 installed, at least version 3.7 or newer. On my system, I’m using `3.10.4`

1.  First we’ll navigate to a directory on your computer where we want to store the Open AI package.
    -   `$ cd ~/Git/whisper-project`
2.  Then we’ll create a virtual environment for our Whisper efforts. That way, we don’t install any packages in our system’s global space, avoiding any package conflicts with other projects.
    -   `$ python3 -m venv venv`
3.  Next, we’ll activate our project, so our Python installations do in fact leverage our virtual environment.
    -   `$ source venv/bin/activate`
4.  At this point we’re ready to install Open AI’s Whisper package.
    -   `$ python3 -m pip install git+[https://github.com/openai/whisper.git](https://github.com/openai/whisper.git)`
5.  Now that we have Whisper installed, we have one more system dependency to install, which Whisper will use to convert audio and video files to other formats.
    -   If you’re on a Debian based operating system, like Ubuntu or Pop OS.
        -   `$ sudo apt update && sudo apt install ffmpeg -y`
    -   For an OSX system, assuming you have [Brew](https://brew.sh/) installed.
        -   `$ brew install ffmpeg`
6.  At this point we’re ready to use Whisper with an audio or video file. We can do this by [writing our own Python code](https://github.com/openai/whisper#python-usage) or simply by calling Whisper from the command line:
    -   `$ whisper name-of-my-video-file.m4a`
7.  The output of the command line invocation will be three files.
    -   1.  `name-of-my-video-file.m4a.txt`: This file contains ust the transcribed text
    -   2.  `name-of-my-video-file.m4a.vtt`: This file contains the transcripted text, with start and stop time stamps. This file is often used for subtitles with videos.
    -   3.  `name-of-my-video-file.m4a.srt`: This file contains the transcripted text, with start and stop time stamps, as well as a counter as to which ‘chunk’ of text this is. This file is often used for subtitles with videos.
    -   Depending on your use case, you’ll likely be interested in only a single file. If the start and stop time stampsa are important to you, its important to note that both the `vtt` and `srt` files should be able to be used. The `vtt` file format seems to be newer the `srt` file format.

This tool would be a great candidate for leveraging a Dockerized environment. Additionally, I can see this tool being useful for transcribing work meetings, lectures, or self dictated notes.



## Easily Converting Audio or Video Files To Text Transcripts - Greg Hilston
URL: https://www.greghilston.com/post/audio-or-video-to-text/

- I've installed whisper on boyo64 using instructions on this page.  It went wihtout issue.  I have not yet tested the operation of whisper


#reference/software/ubuntu 
[[MOC - software]]