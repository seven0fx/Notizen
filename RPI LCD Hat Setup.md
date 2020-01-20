## Notizen für manuelles Setup von https://github.com/pimoroni/displayotron

### Quellen für python3-smbus besorgen:

**#nano /etc/apt/sources.list
#apt-get update 
#apt-get source python3-smbus**

**#cd i2c-xxx**

**#make EXTRA="py-smbus"**

**#cd py-smbus**

**#python setup.py install**


### I2C usw. am RPI aktivieren:

**#nano /boot/config.txt**
```
dtparam=i2c_arm=on
dtparam=i2s=on
dtparam=spi=on
```

**#nano /etc/modules**

```i2c-dev```

### Rechte anpassen
**#nano /etc/udev/rules.d/local.rules:**
```
ACTION=="add", KERNEL=="spidev0.[0-1]*", MODE="0666"
ACTION=="add", KERNEL=="i2c-[0-1]*", MODE="0666"
ACTION=="add", KERNEL=="gpio*", MODE="0666"
```

### Sound bei Bedarf blacklisten:
**#nano /etc/modprobe.d/blacklist.conf**
```
install snd /bin/false
```

in /dev/ i2s*, spi* und gpio* checken

### PIP Module installieren:
**#pip install st7036 sn3218 cap1xxx dot3k**

https://github.com/pimoroni/displayotron/blob/master/examples/dothat/advanced/demo.py testen als User
