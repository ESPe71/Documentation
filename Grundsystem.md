# Raspberry Pi 4 Grundsystem

[Download des Images](https://www.raspberrypi.org/software/operating-systems/) **Raspberry Pi OS Lite**

Wenn das EEPROM des Pi bereits mindestens vom ``Do 3. Sep 12:11:43 UTC 2020`` ist, kann statt einer SD-Karte auch eine SSD verwendet werden. Falls eine SSD verwendet werden soll, dass EEPROM jedoch älter ist, muss zuerst das EEPROM nach den gleichen Anweisungen mit einer SD aktualisiert werden.

```sudo rpi-eeprom-update``` zeigt die Version des EEPROMs an.

Dann kann der Vorgang mit einer SSD wiederholt werden. Die SSD sollte dann an einen USB3-Anschluss angeschlossen werden.

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

## Zusätzliche Software

### Git

```
sudo apt install git-core
git --version
```

### WiringPi

> [WiringPi ist deprecated](http://wiringpi.com/wiringpi-deprecated/), aber immer noch nützlich.

```
sudo apt install wiringpi
```
Testen mit 
```
gpio -v
gpio readall
```

#### Alternative Installation

Falls es zu einem Fehler mit ``gpio readall`` kommt, kann man wiringPi auch aus alternativen Quellen installieren.

Vorher ist wiringPi zu deinstallieren.

```
sudo apt remove wiringpi
```

```
wget https://project-downloads.drogon.net/wiringpi-latest.deb
sudo dpkg -i wiringpi-latest.deb
```

#### Grundlegende Möglichkeiten

```
gpio readall
gpio mode 25 OUTPUT
gpio read 25
gpio write 25 1
gpio write 25 0
```

Die Pinbezeichnung ist  kann man mit ``gpio readall`` in der Spalte wPi ablesen.

### Python

Achtung, in den meisten Fällen, wenn Python schon installiert ist, wurden zwei Pythonversionen installiert. Python2 und Python3.  
Die Version 2 wird mit ``python`` angesprochen, die Version 3 mit ``python3``.
Falls man dieses Kommando eingibt, kommt man in den Python-Interpreter, bei dem die Version am Anfang mit ausgegeben wird. Die aktuelle Version kann man auch mit
``python --version`` bzw. ``python3 --version`` ermitteln.

Wenn man Python 2 nicht benötigt, kann man es auch deinstallieren.
```
sudo apt remove python
sudo apt autoremove
```

Falls python in der Version 3 noch nicht installiert ist:
```
sudo apt install python3
sudo apt install python3-pip
sudo pip3 install RPi.GPIO
sudo pip3 install gpiozero
```
Die zweite Zeile installiert PIP für Python3. Mit Pip kann man Module für Python3 installieren und entfernen.


## Referenzen
[Raspberry Pi Pinout](https://keytosmart.com/single-board-computers/raspberry-pi-4-gpio-pinout/)

[GPIO mit "wiringPi"](https://www.elektronik-kompendium.de/sites/raspberry-pi/2202111.htm)

[Unofficial mirror and ports of WiringPi](https://github.com/WiringPi)

[wiringPi update 2.52](http://wiringpi.com/wiringpi-updated-to-2-52-for-the-raspberry-pi-4b/)

[Python-Modul GPIO-Zero](https://gpiozero.readthedocs.io/en/stable/index.html)

### SSD-Hardware
> [USB 3.0 zu SATA Konverter](https://amzn.to/2Z4jpFb)
>
> [USB C M.2 Festplattengehäuse, SATA auf USB C](https://amzn.to/3jood18)
>
> [X862 V2.0 M.2 SATA SSD Storage Expansion Board with USB 3.1 Connector](https://amzn.to/3opdfdh)
>
> [120G - Interne SATA SSD](https://amzn.to/39Qyy2W)
>
> [128GB M.2 SATA III](https://amzn.to/3oWv9UD)
