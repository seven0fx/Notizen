* entfernen der Knackgeräusche:

https://askubuntu.com/questions/1177762/sound-cracking-and-popping-ubuntu-19-04

* Alsa auf 5.1 umstellen:

`alsamixer` öffnen, Device auswählen, Channels auf 6 stellen,`sudo alsactl store`

* Pulseaudio einrichten:

`sudo nano /etc/pulse/daemon.conf`

    remixing-produce-lfe = yes

    remixing-consume-lfe = yes

    lfe-crossover-freq = 250

    default-sample-channels = 6
    
* Pulseaudio default auf 5.1 stellen:

`pacmd list-sinks | grep -e 'name:' -e 'index:'`

`sudo nano /etc/pulse/default.pa`

    set-default-sink alsa_output.pci-0000_0a_00.4.analog-surround-51
