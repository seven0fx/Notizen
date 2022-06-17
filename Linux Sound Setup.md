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
