# HomeMatic

HomeMatic- und HomeMatic IP-Geräte steuere ich mithilfe von RaspberryMatic auf einem Raspberry Pi4 2GB.  
Da ich mein Pi in einem Netzwerkschrank eingebaut habe, wurde das Funkmodul mittels USB (HB-RF-USB) abgesetzt und außerhalb des Schrankes platziert. 
Zusätzlich wird noch eine externe Antenne verwendet.

## Systemhandlungen

### Installation

Auf dem [Github-Account von Jens Maus](https://github.com/jens-maus/RaspberryMatic/releases) kann man sich die aktuelle Version herunterladen.
Diese wird dann auf eine SD-Karte mit ``dd``, ``Win32DiskImager`` oder ``BalenerEtcher`` geflasht. Eine SSD macht hier keinen Sinn, da der 
Platzverbrauch nicht so hoch ist und die Wahrscheinlichkeit des versagens der SD minimal ist, da RaspberryMatic ein Readonly-Filesystem einsetzt.

Nachdem die SD-Karte eingelegt, der Pi gestartet und die IP ermittelt wurde, kann man auf die WebUI mittels Browser zugreifen. 
Beim ersten Start wird man noch durch eine Grundkonfiguration geführt. Hier kann man die vorgeschlagenen Einstellungen verwenden.

### Update

RaspberryMatic weist auf der Startseite auf ein evtl. verfügbares Update hin.

Unter ``Einstellungen`` ==> ``Systemsteuerung`` ==> ``Zentralenwartung`` kann man unter dem Punkt ``RaspMatic Software`` ein Update durchführen. 
Normalerweise sollten alle Einstellungen dabei erhalten bleiben. Dennoch ist es sinnvoll voher ein Backup anzulegen.

### Backup

Unter ``Einstellungen`` ==> ``Systemsteuerung`` ==> ``Sicherheit`` kann man unter dem Punkt ``Backup-Verwaltung`` ein Backup erstellen und auch wieder einspielen.

Mit Hilfe von __ioBroker__ kan man über den __BackItUp__-Adapter ebenfalls Backups automatisch erstellen lassen.

### Firewall

Im Normalfall wurde die Firewall beim ersten Start schon sinnvoll konfiguriert. Alle Einstellungen sollten so restriktiv wie möglich eingestellt 
werden und nur Ausnahmen in die entsprechenden Listen eingetragen werden. Diese Listen sollten dann aber auch entsprechend gepflegt werden. 
D.h. nicht mehr benötigte Einträge werden zeitnah entfernt. Ich habe nur die IP meiner ioBroker-Installation angegeben.

__Hinweis:__ Die Angabe von IP-Adressen ist für den Zugriff auf die WebUI nicht erforderlich.


``Einstellungen`` ==> ``Systemsteuerung`` ==> ``Firewall konfigurieren``

![Firewalleinstellungen](images/hm/firewall.png "Firewalleinstellungen")

#### ioBroker
__Remote Homematic-Script API__ muss auf ``Eingeschränkt`` für *HM-Rega* (bei mir hm-rega.0) und *HomeMatic IP* (bei mir hm-rpc.1) gestellt werden.

__Homematic XML-RPC API__ muss auf ``Eingeschränkt`` für *rfd* (HomeMatic) (bei mir hm-rpc.0) gestellt werden.

__IP-Adressen für den eingeschränkten Zugriff__ hier wird die IP-Adresse der ioBroker-Installation angegeben.

## Nützliches

### LED ein-/ausschalten

#### Datei
Um die LEDs auszuschalten legt man eine Datei an. ``Programme & Verknüpfungen`` ==> ``Skript testen``
```
system.Exec("rm /etc/config/disableLED");
system.Exec("touch /etc/config/disableLED");
```

#### WebUI
Über die WebUI kann man das gleiche Ergebnis auch erreichen: ``Einstellungen`` ==> ``Systemsteuerung`` ==> ``Allgemeine Einstellungen`` unter dem Punkt ``Info-LED`` 
kann man die LEDs für Servicemeldungen und Alarmmeldungen jeweils getrennt voneinander ein- oder ausschalten.

#### Zeitgesteuertes ein-/ausschalten
Möchte man zeitgesteuert die LEDs ein- bzw. ausschalten, kann man dies mit Hilfe eines Programmes erreichen.  
``Programme & Verknüpfungen`` ==> ``Neu``  
![](images/hm/led_prog.png)  
Dabei als Bedingung eine Zeitsteuerung und als Aktivität ein einzeiliges Skript mit den oben genannten Befehlen.

### Update-URLs

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

### Fehlende Systemvariablen (Servicemeldungen, Alarmmeldungen, Anwesenheit)
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

### HomeMatic IP Dimmer für Markenschalter mit letztem Dimmwert einschalten
Es gibt keine Einstellung, dass beim Einschalten mit dem letzten Dimmwert erfolgen soll. 

Beim Anlegen des Aktors, werden jedoch zwei Direktverknüpfungen mit den Tastern erstellt. Dort kann man den Pegel im Zustand ein anpassen.



## Resourcen

- [Pruefung CCU-Firmware](https://github.com/Baenker/Pruefung-CCU-Firmware/blob/master/CCU-Firmware.js)
- [Expertenmodus vom Experten erklärt (Video 65min)](https://www.youtube.com/watch?v=1B4iwtK1Rmo)
- [HomeMatic IP Dimmer für Markenschalter mit letztem Dimmwert einschalten](https://homematic.simdorn.net/dimmer-mit-letztem-dimmwert-einschalten/)
