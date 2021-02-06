# Raspberry Pi 4 Grundsystem

[Download des Images](https://www.raspberrypi.org/software/operating-systems/) **Raspberry Pi OS Lite**

Wenn das EEPROM des Pi bereits mindestens vom ``Do 3. Sep 12:11:43 UTC 2020`` ist, kann statt einer SD-Karte auch eine SSD verwendet werden. Falls eine SSD verwendet werden soll, dass EEPROM jedoch älter ist, muss zuerst das EEPROM nach den gleichen Anweisungen mit einer SD aktualisiert werden.

```sudo rpi-eeprom-update```

Dann kann der Vorgang mit einer SSD wiederholt werden. Die SSD sollte dann an einen USB3-Anschluss angeschlossen werden.

> [USB 3.0 zu SATA Konverter](https://amzn.to/2Z4jpFb)
>
> [USB C M.2 Festplattengehäuse, SATA auf USB C](https://amzn.to/3jood18)
>
> [X862 V2.0 M.2 SATA SSD Storage Expansion Board with USB 3.1 Connector](https://amzn.to/3opdfdh)
>
> [120G - Interne SATA SSD](https://amzn.to/39Qyy2W)
>
> [128GB M.2 SATA III](https://amzn.to/3oWv9UD)

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


