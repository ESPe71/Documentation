# Dokumentation

## SmartHome mit Raspberry Pi 4 als Zentrale



## Anleitungen
- Hardware und Installationen
  - Zusatzhardware
    - Gehäuse Argon ONE
    - 19" Einbau    
      - [19 inch rack mount 1U for 1-4 pcs of  RASPBERRY Pi + 3x blank cover](https://amzn.to/376T3FH)  
      - [Monoprice Patchpanel](https://amzn.to/2Y9k07t)  
      - [Pi-Einschub zum selberdrucken](https://www.thingiverse.com/thing:3845551)
      - [SSD-Halterung zum selberdrucken](https://www.thingiverse.com/thing:3126622)
    - POE-Hat
      - Pi Foundation  
        [POE-Hat](https://www.raspberrypi.org/products/poe-hat/)  
        [Stapelleiste](https://amzn.to/3eZvVvw)
      - DSLR-KIT
    - LED
    - OLED  
      [OLED bei Amazon](https://amzn.to/2MeAtls)
  - Grundsystem mit Rasbian
    - SD
    - SSD
```
Overall, updating your Pi 4’s OS is simple and straightforward. An overview of the steps are as follows:

Ensure you’re connected to a stable internet connection.

Check what version of firmware your Pi 4 is running to see if you need to update it. You can do this by opening a new terminal window and entering the command 
```
sudo rpi-eeprom-update.
```

If an update is required, install the latest software for the Raspberry Pi 4 by first running the command sudo apt upgrade, and after that has completed, run 
```
sudo apt full-upgrade.
```

Next, update and install the latest firmware by entering in the command 
```
sudo apt install rpi-eeprom.
```

Once the installation process has finished, reboot the Pi by entering in sudo reboot.
```

  - Homematic mit Raspberrymatic  
  
    ##### LED ein-/ausschalten
    *Programme & Verknüpfungen => Skript testen*
    ```
    system.Exec("rm /etc/config/disableLED");
    system.Exec("touch /etc/config/disableLED");
    ```
    *Einstellungen => Systemsteuerung => Allgemeine Einstellungen => Info-LED*  
    Servicemeldungen  
    Alarmmeldungen  
    *Programme & Verknüpfungen => Neu*  
    ![](images/hm/led_prog.png)
    ##### Firewall
    Einstellungen => Systemsteuerung => Firewall konfigurieren
    
    ![Firewalleinstellungen](images/hm/firewall.png "Firewalleinstellungen")
    
    ##### Update-URLs
    
    |CCU|URL
    |---|----
    |ccu2|https://update.homematic.com/firmware/download?cmd=js_check_version&version=2.22.22&product=HM-CCU2&serial=NEQ7777777
    |ccu3|http://update.homematic.com/firmware/download?cmd=js_check_version&version=3.22.22&product=HM-CCU3&serial=NEQ7777777
    |RaspberryMatic|https://raspberrymatic.de/LATEST-VERSION.js
    |pivccu2|https://www.pivccu.de/pivccu.latestVersion
    |pivccu3|https://www.pivccu.de/pivccu3.latestVersion
    |debimatic|https://www.debmatic.de/latestVersion
    |testing_pivccu|https://www.pivccu.de/pivccu.latestVersion
    |testing_pivccu3|https://www.pivccu.de/pivccu3.latestVersion
    |testing_debimatic|https://www.debmatic.de/latestVersion

    ##### Fehlende Systemvariablen (Servicemeldungen, Alarmmeldungen, Anwesenheit)
    Falls die o.g. Systemvariablen nicht vorhanden sind, oder nur irgendwelche andere unbekannte, kann man sie sich mit Hilfe eines Skriptes anzeigen lassen und wahrscheinlich auch wiederherstellen.
    ```
    ! Servicemeldungen
    WriteLine(dom.GetObject(41).Name());
    ! Alarmmeldungen
    WriteLine(dom.GetObject(40).Name());
    ! Anwesenheit
    WriteLine(dom.GetObject(950).Name());
    ```
    In der Ausgabe sollten nun die entsprechenden Systemvariablen aufgelistet werden. Sollte dies nicht der Fall sein, dann kann man die Namen der Systemvariablen wie folgt wiederherstellen:
    ```
    ! Servicemeldungen
    WriteLine(dom.GetObject(41).Name("Servicemeldungen"));
    ! Alarmmeldungen
    WriteLine(dom.GetObject(40).Name("Alarmmeldungen"));
    ! Anwesenheit
    WriteLine(dom.GetObject(950).Name("Anwesenheit"));
    ```
    
  - Pi-Hole
  - [ioBroker](https://technikkram.net/blog/2020/11/16/io-broker-auf-dem-raspberry-pi-installieren/)
  - USV  
    [USV mit ioBroker](https://bloggerbu.de/usv-iobroker/)
  
- Flashen von China-Cloud-Geräten
  - Tasmota
    - Flashen mit Stick
    - OTA-Flashen
  - Gosund Zwischenstecker SP111
  - Gosund WLAN-Lampe WB3
  - LVWIT WLAN-Lampe A70-3
  
### ioBroker

## Resourcen
- https://www.bytebee.de/raspbian-installieren/  
- https://ownsmarthome.de/2019/12/07/tasmota-mit-tuya-convert-over-the-air-flashen/  
- https://www.verdrahtet.info/2020/03/06/tasmota-flashen-ota-update/  
- https://www.youtube.com/watch?v=Z8PDWtepEjE&list=WL&index=45  
- https://www.verdrahtet.info/2020/05/22/raspberry-pi-4-von-ssd-booten-ganz-ohne-sd-karte/  
- https://github.com/raspberrypi/rpi-eeprom/tree/master/firmware/beta  
- https://jensmueller.one/amazon-link-generator/
- https://www.trojaner-board.de/96344-anleitung-cleanup-massnahmen-absicherung-rechners.html#post627442
- https://github.com/Baenker/Pruefung-CCU-Firmware/blob/master/CCU-Firmware.js
  
