https://wiki.archlinux.org/title/NVIDIA/Tips_and_tricks#Preserve_video_memory_after_suspend

* edit /etc/modprobe.d/nvidia-power-management.conf:
  
      sudo nano /etc/modprobe.d/nvidia-power-management.conf 
      options nvidia NVreg_PreserveVideoMemoryAllocations=1 NVreg_TemporaryFilePath=/tmp/tmp-nvidia

* enable nvidia-suspend.service and nvidia-hibernate.service:

      sudo systemctl enable nvidia-suspend.service
      sudo systemctl enable nvidia-hibernate.service

* update initramFS:

      sudo update-initramfs -u
* reboot
