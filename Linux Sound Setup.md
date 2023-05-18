* entfernen der Knackgeräusche:

https://askubuntu.com/questions/1177762/sound-cracking-and-popping-ubuntu-19-04

Verify how is your sound card's power_save parameter:

    cat /sys/module/snd_hda_intel/parameters/power_save
If it returns 1, do the following to change it temporally:

    echo "0" | sudo tee /sys/module/snd_hda_intel/parameters/power_save
If the previous step worked for you, persist that configuration (otherwise the problem will continue after reboot):

    echo "options snd_hda_intel power_save=0" | sudo tee -a /etc/modprobe.d/audio_disable_powersave.conf

---

* Alsa auf 5.1 umstellen:

`alsamixer` öffnen, Device auswählen, Channels auf 6 stellen, `sudo alsactl store`

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
