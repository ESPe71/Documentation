# Raspberry Pi 4 Grundsystem

[Download des Images](https://www.raspberrypi.org/software/operating-systems/) **Raspberry Pi OS Lite**

Flashen des Images mit ``dd``, ``Win32DiskImager`` oder ``BalenerEtcher``.

Auf der boot partition eine leere Datei mit Namen ``ssh`` erstellen.

SD-Karte in Pi einlegen und starten.

IP-Adresse im Router ermitteln.

Mit SSH auf Pi einloggen.

```
sudo raspi-config
```
``System Options`` --> ``Hostname``

``Interface Options`` --> ``I2C``

``Localisation Options`` --> ``Locale``

``Localisation Options`` --> ``Timezone``

``Advanced Options`` --> ``Expand Filesystem``

``Advanced Options`` --> ``Boot Order``

``Advanced Options`` --> ``Bootloader Version``

Beenden und neu starten.

```
sudo apt update
sudo apt full-upgrade
sudo apt install rpi-eeprom
```



# Referenzen
[Raspberry Pi Pinout](https://keytosmart.com/single-board-computers/raspberry-pi-4-gpio-pinout/)


