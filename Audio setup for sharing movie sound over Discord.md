
Connect audio output of playing movie to Discord (can be heard by client on other end)

  
bash script:

```/bin/bash

#!/bin/bash

microphone="alsa_input.usb-Samson_Technologies_Samson_C03U-00.analog-stereo"

systemctl --user restart pulseaudio.service

# Setup sink
pactl load-module module-null-sink \
    sink_name=mix-for-virtual-mic \
    sink_properties=device.description=Mix-for-Virtual-Microphone

# Real microphone to mix-for-virtual-mic
pactl load-module module-loopback \
    source=$microphone \
    sink=mix-for-virtual-mic latency_msec=20

# Virtual microphone device to pipe stuff to
pactl load-module module-pipe-source \
    source_name=virtmic \
    file=/home/curtis/dev/virtmic format=s16le rate=16000 channels=1

pactl load-module module-combine-sink \
    sink_name=virtual-microphone-and-speakers \
    slaves=mix-for-virtual-mic,@DEFAULT_SINK@

pactl load-module module-remap-source \
    master=mix-for-virtual-mic.monitor \
    source_properties=device.description=mixed-mic


```

![[Pasted image 20230709133242.png]]

![[Pasted image 20230709133323.png]]

![[Pasted image 20230709133349.png]]

[[MOC Software Projects]]