# ioBroker

## Installation

1. NodeJS Repository hinzufügen\
   Die aktuelle LTS-Version kann man unter [https://deb.nodesource.com/](https://deb.nodesource.com/) ermitteln.\
   ``curl -sL https://deb.nodesource.com/setup_20.x | sudo -E bash``
3. NodeJS installieren  
   ``sudo apt install -y nodejs``
4. ioBroker installieren  
   ``curl -sL https://iobroker.net/install.sh | bash``

> Es schadet sicher nicht, wenn man sich die Skripte die man aus dem Internet, in Punkt 1 und 3, ausführt, auch mal anschaut.

## Adapter

### Senec
Dieser Adapter liest die in einem Senec Home V2.1 verfügbaren Werte via lala.cgi aus.

Im Moment muss dieser Adapter noch durch eine _Installation aus eigener URL_ installiert werden. Dazu _Adapter aus beliebiger Quelle installieren oder aktualisieren_ und die URL https://github.com/nobl/ioBroker.senec angeben. Genauso wird dann auch ein Update durchgeführt.

### Philips Hue-Bridge Adapter
Dieser Adapter funktioniert bei mir am besten mit der Hue-Bridge.

Leider pollt der Adapter die Werte von der Bridge (Stand: 28.11.2021), so dass die Reaktionszeit von Sensoren sehr zu wünschen übrig lassen. Philips Hue stellt nun aber eine Push-API bereit, die von diesem Adapter noch nicht unterstützt wird. Wie man eine Unterstützung der Push-API dennoch bewerkstelligt zeigt der Artikel [Hue ohne Verzögerung mit Push-API in ioBroker einbinden](https://www.smarthomejetzt.de/hue-bewegungsmelder-und-lampen-ohne-verzoegerung-mit-hue-push-api-in-iobroker-einbinden/). Wie man auch die Senic Friends of Hue Schalter einbindet, zeigt der Artikel [FoH Schalter mit Hue-Push-API einbinden](https://www.smarthomejetzt.de/senic-friends-of-hue-wand-smart-switch-schalter-mit-hue-push-api-script-aus-iobroker-forum/).

## Resources

- [Installation für ConBee II](https://phoscon.de/de/conbee/install)
- [Friends of Hue Schalter anlernen](https://phoscon.de/en/support#pairing-friends-of-hue-switch)
- [Phoscon App findet kein Gateway](https://forum.iobroker.net/topic/26130/phoscon-app-findet-gateway-nicht/7)


* [Grafana Dashboard mit ioBroker Daten - so geht's! | verdrahtet.info](https://www.youtube.com/watch?v=bZLXVjUJJ4Q)
* [Grafana- Alternative Installation auf einem Raspberry Pi](https://www.smarthome-tricks.de/influxdb/1-4-grafana-alternative-installation-auf-einem-raspberry-pi/)
* [Raspberry Pi4 – Grafana auf Debian Buster installieren](https://tpolo.de/raspberry-pi4-grafana-debian-buster-installieren)
* [Raspberry Pi: Dienste starten, stoppen, neustarten, aktivieren und deaktivieren](https://www.elektronik-kompendium.de/sites/raspberry-pi/2002211.htm)
