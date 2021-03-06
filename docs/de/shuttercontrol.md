![Logo](img/shuttercontrol.png)
# Shuttercontrol - Adapter zur automatischen Rollladensteuerung

# Inhalt
* [Grundlegendes](#grundlegendes)
* [Installation](#installation)
* [Adapterkonfiguration - HAUPTEINSTELLUNGEN](#adapterkonfiguration---haupteinstellungen)
* [Adapterkonfiguration - ZEIT-EINSTELLUNGEN](#adapterkonfiguration---zeit-einstellungen)
* [Adapterkonfiguration - EXTRA-EINSTELLUNGEN](#adapterkonfiguration---extra-einstellungen)
	* [Astro-Einstellungen](#astro-einstellungen)
	* [Extra-Einstellungen](#extra-einstellungen)
* [Individuelle Rollladeneinstellungen](#individuelle-rollladeneinstellungen)
	* [Haupteinstellungen](#haupteinstellungen)
	* [Sonnenschutz-Einstellungen](#sonnenschutz-einstellungen)
* [Datenpunkte](#datenpunkte)
	* [shuttercontrol.0.control](#shuttercontrol.0.control)
	* [shuttercontrol.0.info](#shuttercontrol.0.info)
	* [shuttercontrol.0.shutters](#shuttercontrol.0.shutters)

## Grundlegendes

> Die Anleitung ist gültig für Versionen ab 0.7.0

Shuttercontrol ist ein Adapter für eine sehr umfangreiche Steuerung von Rollläden,
Jalousien oder Markisen und umfasst sowohl die automatische Beschattung als auch
die nächtliche Verdunklung.

> Der Einfachheit halber wird hier nur von Rollläden gesprochen.

Für die Steuerung stehen sehr viele einstellbare Parameter zur Verfügung, z.Bsp.:
* zwei verschiedene globale Timer (z.B. unterschiedlich für Schlaf- und Wohnräume),
* diverse sonnenstandsabhängige Parameter die individuell je Rollladen eingestellt
werden können,
* Trigger für Tür-/Fenstersensoren die einem Aussperrschutz dienen oder ein automatisches
Öffnen zu einem individuellen Level bei Öffnen der Tür oder des Fensters dienen,
* verschiedene einstellbare Parameter für Beschattung in Abhängigkeit von z.B.
Innentemperatur, Außentemperatur, Helligkeit, Hitzesensor o.ä.,
* Einbeziehung des Sonnenstands um nur Räume zu verdunkeln, die tatsächlich beschienen
werden.

Alle Konfigurationsdatenpunkte sind bereits mit Beispielen voreingestellt, so dass
der Adapter nach Installation und Eingabe von den IDs der Rollladenaktoren schnell
betriebsbereit ist.

Die weitere Konfiguration dient dann der Anpassung an persönliche Wünsche.

> Shuttercontrol kann Aktoren nur über die Position wie zb. LEVEL mit Werten
von 0 bis 100 steuern!




## Installation
Eine Instanz des Shuttercontrol-Adapters wird über die ioBroker Admin-Oberfläche
mit klicken auf das + Zeichen installiert. Je nach eingestellten aktiven Verwahrungsort
im Admin Adapter wird die stable(default) oder latest Version  installiert.

![installation.jpg](img/installation.png)

Nach der Erstellung der Instanz öffnet sich automatisch das Konfigurationsfenster
mit den Haupteinstellungen:

## Adapterkonfiguration - HAUPTEINSTELLUNGEN

![main.jpg](img/main.png)


* **1:** hinzufügen eines Rollladenaktors

* **2:** Ändern eine ausgewählten Rollladenaktors

* **3:** individuelle Konfiguration des jeweiligen Rollladens öffnen

* **4:** Festlegung der Reihenfolge in der die Rollläden mit gleichen Einstellungen fahren.

* **5:** Löschen des Rollladenaktors mit allen konfigurierten Daten!

* **Nr:**  fortlaufende Nummer der gelisteten Rollläden

* **Aktiv:** Checkbox zur Aktivierung/Deaktivierung der Steuerung des entsprechenden Rollladens

* **Name:** Name des Aktors wird bei der Auswahl der ID automatisch aus den Objekten eingelesen
und kann danach nach eigenen Wünschen abgeändert werden.

* **Objekt-ID Rollladen:** Eindeutige ID des zu steuernden Datenpunkts in den Objekten

* **6:** Aufruf der Adapter Github Seite

* **7, 8:** Konfigurationsdatei laden bzw. speichern


Der Beispiel Aktor *shutter example* wird automatisch angelegt. Diesen bitte löschen
und anschließend durch anklicken des mit 1 markierten (+) die eigenen Rollladenaktoren
hinzufügen.


![ID_Selector_DP_Level.png](img/ID_Selector_DP_Level.png)

Nach Abschluss der ID-Auswahl ist der Adapter bereits betriebsbereit und wird nun
weiter an die eigenen Wünsche angepasst.

---
Bevor nun [individuelle Rollladeneinstellungen](#individuelle-rollladeneinstellungen) bei jedem Rollladen durchgeführt werden,
sollten die grundlegenden [Zeit-Einstellungen](#adapterkonfiguration---zeit-einstellungen) und [Extra-Einstellungen](#adapterkonfiguration---extra-einstellungen) erfolgen:

---

## Adapterkonfiguration - ZEIT-EINSTELLUNGEN
Hier werden grundlegende Zeit- bzw. Astro Einstellungen vorgenommen, die später in
den [individuellen Rollladeneinstellungen](#individuelle-rollladeneinstellungen) für jeden Rollladen ausgewählt werden.

> Hinweis:  
Das Schließen von Rollläden am Freitag erfolgt zur eingestellten Wochenendzeit
und am Sonntag zur eingestellten Arbeitswochenzeit!


![timeSettings.jpg](img/timeSettings.png)

### Einstellungen für den Wohnbereich und Schlafbereich
In oberen Abschnitt werden die gewünschten Parameter für die Rollläden im
Wohnbereich und im unteren Abschnitt für den Schlafbereich eingegeben.

> Hinweis:  
Natürlich muss diese Kategorisierung nicht zwingend für einen Wohn- oder
Schlafbereich genutzt werden, sondern ermöglicht zwei Bereiche im Gebäude
mit unterschiedlichen Fahrzeiten der Rollläden zu definieren.

**Art der Automatiksteuerung für den Wohnbereich (Schlafbereich)**, über Pulldown wird gewählt zwischen:

* **Nur die Zeit Wohnbereich (Schlafbereich):**  
Die Rollläden werden ausschließlich zeitgesteuert gefahren
* **Zeit Wohnbereich (Schlafbereich) mit Sonnenauf- & Sonnenuntergang:**  
Die Rollläden werden nach Sonnenauf- und Sonnenuntergang gesteuert, jedoch fahren nicht
vor der frühesten Zeit hoch und nicht nach der spätesten Zeit herunter.
* **Zeit Wohnbereich (Schlafbereich) mit GoldenHour:**  
Analog zu dem Sonnenauf- und Sonnenuntergang, jedoch mit dem Beginn und Ende der "Golden Hour" als Referenz


**Schließen der Rollläden in der Arbeitswoche:**  
Übliche Zeit für die Verdunklung während der Woche

**früheste Zeit für das hochfahren in der Woche:**  
zu dieser Zeit fahren die Rollläden in der Woche *frühestens* hoch

**späteste Zeit für das hochfahren in der Woche:**  
zu dieser Zeit fahren die Rollläden in der Woche *spätestens* hoch

**Zeitverzögerung für das versetzte Fahren der Rollläden (Sekunden):**  
Abstand zwischen den einzelnen Rollladenfahrten dieses Bereichs um z.Bsp.
Funkstörungen zu vermeiden, oder den Anschein zu erwecken, sie würden manuell gefahren.

**Schließen der Rollläden am Wochenende:**  
Übliche Zeit für die Verdunklung am Wochenende **und** an Feiertagen

**früheste Zeit für das hochfahren am Wochenende:**  
zu dieser Zeit fahren die Rollläden am Wochenende **und** an Feiertagen *frühestens* hoch

**späteste Zeit für das hochfahren am Wochenende:**  
zu dieser Zeit fahren die Rollläden am Wochenende **und** an Feiertagen *spätestens* hoch

> Soll der Rollladen niemals hochfahren, wenn die Sonne noch nicht einen
> bestimmten Stand überschritten hat, muss diese Zeit auf den spätesten
> Zeitpunkt dieses Sonnenstandes (am 21.12.) eingestellt werden.

---

## Adapterkonfiguration - EXTRA-EINSTELLUNGEN

In den Extra-Einstellungen werden weitere Einstellungen vorgenommen.

![extraSettings.jpg](img/extraSettings.png)

### Astro-Einstellungen
**Breiten- und Längengrad:**  
Breiten- und Längengrad übernimmt Shuttercontrol aus den ioBroker Systemeinstellungen.
Shuttercontrol berechnet anhand dieser Werte den Sonnenstand.

**Zeitverzögerung beim Hochfahren bzw. für das Herunterfahren (Minuten):**  
Hier kann ein +/- Offset eingegeben werden, um den sich die Rollladenfahrten von dem
in der [individuellen Rollladeneinstellung](#individuelle-rollladeneinstellungen) ausgewählten Astro-Event verschieben soll.

**Zeitverzögerung für das versetzte Fahren der Rollläden (Sekunden):**  
Damit nicht alle Rollläden gleichzeitig fahren, kann hier eine globale Zeitverzögerung
in Sekunden eingestellt werden.

**Beenden der Sonnenschutzfunktion mit Sonnenhöhe (Elevation):**  
Sobald die Sonne die hier eingestellte Höhe *unterschreitet*, endet die Beschattung
durch Shuttercontrol.
> Evtl. vorhandene vorzeitige Beschattung durch Bebauung oder hohe Bäume kann
> hiermit berücksichtigt werden und die Beschattungsautomatik früher beenden.

### Extra-Einstellungen

**Objekt-ID für das setzen des Urlaubs:**  
Diese Objekt-ID setzt den internen Zustand "Holiday". Hier kann z.Bsp. ein
Datenpunkt aus dem iCal-Adapter verwenden werden, der im Urlaubsfall den Wert
```true``` liefert und die Rollläden fahren entsprechend den Wochenendzeiten.

**Objekt ID des Auslösers für den Schlafbereich (Auto):**  
Mit diesem Auslöser wird der Automodus des Schlafbereichs aktiviert.

**Objekt ID des Triggers für den Wohnbereich (Auto):**  
Mit diesem Auslöser wird der Automodus des Wohnbereichs aktiviert.


**Alle Rollläden schliessen spät in der Nacht**  
Mit dieser Option können alle Rollladen spät abends nochmals runter gefahren werden.
Das deckt das Szenario ab, wenn zur normalen Zeit für das Herunterfahren das Fenster
oder die Tür noch offen war, oder wenn nach dem Herunterfahren z.Bsp. die Terrassentür
nochmal geöffnet wird. 

> Diese Option muss in der jeweiligen [individuellen Rollladeneinstellung](#individuelle-rollladeneinstellungen) separat
aktiviert bzw. falls nicht gewünscht deaktiviert werden.

**Zeit, in der alle Rollläden spät in der Nacht schließen**  
Zeit, wann alle Rollläden abends nochmals heruntergefahren werden sollen (z.Bsp. 22:30Uhr)

**Beginn des Sommers** und **Ende des Sommers:**  
Hier wird der gewünschte Beginn bzw. Ende des Sommers festgelegt.

In der jeweiligen [individuellen Rollladeneinstellung](#individuelle-rollladeneinstellungen) wird dann durch setzen der Checkbox 
bei ```Rollladen im Sommer nicht schließen``` verhindert das dieser Rollladen im Sommer
schließt. 


**Überprüfen des aktuellen Rollladenstatus:**  
Bei einigen User (unter anderen shelly User) tritt das Problem auf, dass sich das
Level noch einmal etwas verändert. Aus diesem Grund gibt es hier eine Checkbox.
Bei aktivierter Checkbox, prüft shuttercontrol 1 Minute nach der letzten Fahrt des
Rollladens das aktuelle Level und speichert es temporär.

**Verwenden der gesetzlichen Feiertage:**  
Sollen die Rollläden an Feiertagen wie an Wochenenden fahren, wird diese Checkbox
aktiviert und nebenan die entsprechende Instanz des Feiertage-Adapters ausgewählt.
> Ggf. können zwei Instanzen des Feiertage-Adapters angelegt werden:
>  eine zum Anzeigen aller möglichen Feiertage und eine mit arbeitszeitrelevanten
>  Feiertagen, auf die dann shuttercontrol zugreift.


## Individuelle Rollladeneinstellungen

Nach dem Anlegen der Rollläden unter [Adapterkonfiguration - HAUPTEINSTELLUNGEN](#adapterkonfiguration---haupteinstellungen) wird
durch das betätigen des Bleistifts (3) beim entsprechenden Rollladen mit den Reitern
[Haupteinstellungen](#haupteinstellungen) und [Sonnenschutz-Einstellungen](#sonnenschutz-einstellungen) jeder Rollladen einzeln weiter konfiguriert.

![main1.jpg](img/main1.png)

---

### Haupteinstellungen

![mainShutter.jpg](img/mainShutter.png)

Im oberen Bereich werden die Zeitpunkte für das Öffnen bzw. Schließen des Rollladens
separat per Pulldown-Menü ausgewählt.
> Diese Zeiten wurden  bereits in  [Adapterkonfiguration - Zeit-Einstellungen](#adapterkonfiguration---zeit-einstellungen) konfiguriert.

Auswahlmöglichkeiten:
* **Aus:**  
keine Zeitvorgaben verwenden

* **Wohnbereich:**  
Der Rollladen fährt zu den Zeiten wie in *Einstellungen für den Wohnbereich* konfiguriert.
* **Wohnbereich (Automatik):**  
Der Rollladen fährt zu den Zeiten wie in *Einstellungen für den Wohnbereich* konfiguriert
**und** zusätzlich wird auf den unter Extra-Einstellungen festgelegten Trigger
```Objekt-ID zum aktivieren/deaktivieren des Auto-Wohnbereichs``` geachtet. Steht
dieser auf false wird der Rollladen **nicht** automatisch gefahren.

* **Schlafbereich:**  
Der Rollladen fährt zu den Zeiten wie in *Einstellungen für den Schlafbereich* konfiguriert.
* **Schlafbereich (Automatik):**  
Der Rollladen fährt zu den Zeiten wie in *Einstellungen für den Schlafbereich* konfiguriert
**und** zusätzlich wird auf den unter Extra-Einstellungen festgelegten Trigger
```Objekt-ID zum aktivieren/deaktivieren des Auto-Schlafbereichs``` geachtet.
Steht dieser auf false wird der Rollladen **nicht** automatisch gefahren.

* **Sonnenuntergang/Sonnenaufgang:**  
Der Rollladen fährt bei Sonnenuntergang bzw. bei Sonnenaufgang.

* **Sonnenhöhe (Elevation):**  
Unterschreitet die Elevation den in der [individuellen Rollladeneinstellung](#individuelle-rollladeneinstellungen) eingestellten
Wert wird der Rollläden gefahren.

* **Golden Hour:**  
Der Rollläden fährt zur Golden Hour, die je nach Breitengrad und Jahreszeit ca. 1 Stunde
vor Sonnenuntergang bzw. nach Sonnenaufgang ist. Der Begriff stammt aus der Fotografie,
weil dort die Farben einen goldenen Schimmer haben.



**Wert des Fenster/Tür Sensors im geschlossenen Zustand:**  
Hier wird der Wert festgelegt den der Auslöser unter **Objekt-ID des Fenster/Tür Kontaktes**
(z.B. Fenster- oder Drehgriffkontakt) hat, bei der die Rollladenautomatik unbegrenzt fahren darf.
> Es können Werte wie true, false, 0, 1 oder 2 ausgewählt werden.

Ist der Rollladen nicht in der obersten Position und wird der Sensor aus der angegebenen
Position bewegt, fährt der Rollladen auf die **Rollladenhöhe bei öffnen des Fensters oder Tür**.

**Rollladen fahren bei Änderung des Fenster/Tür Zustandes:**  
Pulldown zur Auswahl der Funktion, die bei Bewegung des Fenster/Tür Sensors
durchgeführt werden soll:

* **Aus**:  keine Bewegung
* **Öffnen**:  Beim Öffnen der Tür fährt der Rollladen auf und verbleibt dort
* **Schließen**:  Nach Schließen der Tür fährt der Rollladen auf die Verdunklungsposition
* **Öffnen und Schließen:**  Der Rollladen öffnet sich mit der Tür und fährt mit dem Schließen wieder runter


**Rollladenhöhe bei öffnen des Fensters oder Tür:**  
Soll der Rollladen bei Auslösen des Sensors fahren, wird hier die gewünschte
Rollladenposition eingegeben (z.B. bei Fenstern 25% zum Lüften, oder 100% 
bei Türen um durchgehen zu können).

**Rollladenautomatik auch bei geöffneten Fenster/Tür benutzen (Aussperrschutz)**  
Entspricht zum Zeitpunkt des automatischen Schließens der Fenster/Tür Sensor 
__nicht__ dem dort eingegebenen Wert (Fenster/Tür offen) wird folgendes ausgeführt:

* **Aus**: Aussperrschutz ist in beide Richtungen aktiv, die Rollläden bewegen nicht wenn der egal wie der Sensor steht.
* **Öffnen**: Bei Verdunklungs- / Beschattungsende fährt der Rollladen hoch
* **Schließen**: Bei Verdunklungs- / Beschattungsbeginn fährt der Rollladen herunter
* **Öffnen und Schließen**: Der Rollladen darf sich egal wie der Sensor steht, in beide Richtungen bewegen



**Rollladenhöhe beim Runterfahren:** gewünschte Rollladenposition bei Verdunklung

**Rollladenhöhe beim Hochfahren:** gewünschte Rollladenposition am Morgen

> Entsprechend der verwendeten Aktoren muss die Rollladenhöhe eingegeben werden:
> 0 = geschlossen und 100 = offen bzw. 0= offen und 100 = gechlossen

**Sonnenhöhe (Elevation):**
Soll die Verdunklung bei einer fixen Elevation starten bzw. enden, wird dieser Wert hier eingegeben; sonst leer lassen.

**Objekt-ID des Fenster/Tür Kontaktes:**
über das (+) den Sensor (State) auswählen der eine Rollladenfahrt verhindern soll (z.B. Türkontakt).

**Rollladen spät schliessen:** mit dieser Option wird der Rollladen zu einer
definierten Zeit (einstellbar in den Extra-Einstellungen) zusätzlich heruntergefahen

**Rollladen im Sommer nicht schliessen:** manche Rollläden sollen im Sommer
nicht geschlossen werden. Der Zeitraum dafür wird in den Extra-Einstellungen festgelegt

---

### Sonnenschutz-Einstellungen
Der Sonnenschutz kann über Auslöser wie Himmelsrichtung, Außentemperatur, Innentemperatur
und Lichtsensor für die Beschattung und deren Ende gesteuert werden und wird über
**Art der Sonnenschutzsteuerung** eingestellt.

![sunProtect.jpg](img/sunProtect.png)


**Rollladenhöhe beim Runterfahren:**  
Der Wert wie weit der Rollladen bei Beschattung geschlossen werden soll (0 entspricht
komplett geschlossen).

**Himmelsrichtung (Sonnenposition):**  
Ausrichtung des Fensters auf der Windrose (0° = Nord; 180° = Süd)

**Art der Sonnenschutzsteuerung:**  
Folgende Kombinationen sind über Pulldown auswählbar:
* Innen- & Außentemperatur/Lichtsensor
* Himmelsrichtung
* Innen/Außentemperatur/Lichtsensor & Himmelsrichtung
* Außentemperatur/Lichtsensor & Himmelsrichtung
* Außentemperatur/Lichtsensor
* Innentemperatur

> Der Sonnenschutz löst erst aus wenn ALLE gewählten Auslöser aktiv sind (UND Verknüpfung).

**+/- Bereich der Sonnenposition für den aktiven Sonnenschutz:**  
Bereich in dem die Sonne (um den Mittelpunkt) störend in das Fenster einstrahlen
würde. Außerhalb dieses Bereichs findet keine Beschattung statt.

**Sollwert Außentemperatur:**  
Schwellwert zum Starten der Beschattung. Dieser Wert ist abhängig von dem im Feld
**Objekt-ID für die Außentemperatur** ausgewählten Sensor.

**Hysterese Außentemperatur (Prozent):**  
Hier kann eine Hysterese in Prozent eingestellt werden, damit der Rollladen bei
Schwankungen nicht ständig hoch und runter fährt.
Die Hysterese ist der Unterschied zwischen dem oberen Temperaturwert, bei dem die
Beschattung beginnen soll, und dem unteren Temperaturwert, bei dem die Beschattung
wieder endet.

**Objekt-ID für die Außentemperatur:**  
Der hier ausgewählte Sensor muss nicht zwingend die Außentemperatur messen. Er kann
irgendeinen Wert, der zur Beschattungsauslösung hinzugezogen werden kann, liefern.
Dies kann auch ein Hitzesensor (Temperaturdifferenzsensor) sein. Wird kein Außensensor
eingesetzt, dieses Feld leer lassen.

**Sollwert des Sonnenschutzlichtsensors:**  
Schwellwert zum Starten der Beschattung. Dieser Wert ist abhängig von dem im Feld
**Objekt-ID für die Sonnenschutzlichtsensors** ausgewählten Sensor.

**Hysterese Lichtsensor (Prozent):**  
Hier kann eine Hysterese nach unten in Prozent eingestellt werden, damit der
Rollladen bei Schwankungen durch wechselnde Bewölkung nicht ständig hoch und runter fährt.
Die Hysterese ist der Unterschied zwischen dem eingestellten Sollwert, bei dem die
Beschattung beginnen soll, und dem unteren Helligkeitswert, bei dem die Beschattung
wieder endet.

> Beispiel:
> Sollwert des Sonnenschutzlichtsensors ist auf 30.000, Hysterese auf 40 eingestellt:
> Der Sonnenschutz ist aktiv ab > 30.000 und bleibt aktiv bis der Wert unter 18.000 fällt.

**Objekt-Id des Sonnenschutzlichtsensors:**  
Analog zum Außentemperatursensor; wenn nicht benutzt leer lassen

**Sollwert Innentemperatursensor:**  
Hier kann eine Temperatur eines zu dem Rollladen zugeordneten Innentemperatursensors
eingegeben werden unter der keine Beschattung stattfinden soll, um z.B. die Wärme-
einstrahlung im Winter zur Heizungsunterstützung zu nutzen.

**Hysterese Innentemperatur (Prozent):**  
Hier kann eine Hysterese in Prozent eingestellt werden, damit der Rollladen bei
Innentemperaturschwankungen nicht ständig hoch und runter fährt. Die Hysterese
ist der Unterschied zwischen dem oberen Temperaturwert, bei dem die Beschattung
beginnen soll, und dem unteren Temperaturwert, bei dem die Beschattung wieder endet.

**Objekt-ID des Innentemperatursensors:**  
über das (+) den Temperatursensor (State) auswählen der eine Rollladenfahrt verhindert.
Wird kein Innensensor eingesetzt, dieses Feld leer lassen.

> Hinweis:  
Wird ein Rollladen manuell verstellt und entspricht die Position nicht der
automatisch angefahrenen, setzt die Automatik aus!
Ausnahme:  
Wenn der Rollladen das erste Mal am Tag manuell auf 100% geöffnet
wird, wird ebenso der Sonnenschutz ermöglicht. Hierbei fährt der Rollladen
bei Bedarf kurz nach dem manuellen Hochfahren in den Sonnenschutz.
Wird der Rollladen automatisch hochgefahren und sind die Voraussetzungen für
den Sonnenschutz erfüllt, so fährt er direkt die Höhe des Sonnenschutzes an.



## Datenpunkte
Shuttercontrol legt verschiedene Datenpunkte unter folgenden Ordnern an:
* shuttercontrol.x.control
* shuttercontrol.x.info
* shuttercontrol.x.shutters

> x steht für die jeweilig installierte Instanz

---
### shuttercontrol.0.control

![datapointscontrol](img/datapointscontrol.PNG)

Datenpunkte zur Steuerung verschiedener Funktionen wie:
* Holiday  
Bei ```true```fahren die Rollläden zu den eingestellen Zeiten Wochenende und bei
```false``` zu den Zeiten unter der Woche.
> Kann von eigenen Skripten, die den Urlaub, freie Tage o.ä. berechnen oder darstellen, 
auf true gesetzt werden um die Wochenend-Einstellungen zu aktivieren.

* autoLiving  
Bei Steuerung der Rollläden mit **Wohnbereich (Automatik)** wird hier die Automatik 
mit ```true``` ein- und mit ```false```ausgeschaltet.

* autoSleep  
Bei Steuerung der Rollläden mit **Schlafbereich (Automatik)** wird hier die Automatik 
mit ```true``` ein- und mit ```false```ausgeschaltet.

* closeAll  
Button um **alle** Rollläden in **allen Bereichen** zu schließen

* closeLiving  
Button um **alle** Rollläden im Wohnbereich zu schließen

* closeSleep  
Button um **alle** Rollläden im Schlafbereich zu schließen

* openAll  
Button um **alle** Rollläden in **allen Bereichen** zu öffnen

* openLiving  
Button um **alle** Rollläden im Wohnbereich zu öffnen

* openSleep  
Button um **alle** Rollläden  im Schlafbereich zu öffnen

* sunProtect  
Button um die Rollläden in die Sonnenschutzpostion zu fahren.

---
### shuttercontrol.0.info
Datenpunkte zur Anzeige berechneter Werte und zur Überprüfung von konfigurierten
Zeiten:

![datapointsinfo](img/datapointsinfo.png)

---
### shuttercontrol.0.shutters
![datapointsshutters](img/datapointsshutters.png)

* autoDown  
Für jeden Rollladen kann hier das automatische Schließen mit ```false```deaktiviert 
bzw. mit ```true```aktiviert werden.

* autoLevel  
Zeigt für jeden Rollladen die aktuelle Position an (nicht hierrüber steuerbar).

* autoState  
Zeigt für jeden Rollladen den aktuellen Status (up, down, Manu_Mode, sunProtect) (nicht hierrüber steuerbar).

* autoSun  
Für jeden Rollladen kann hier die Sonnenschutzfunktion mit ```false```deaktiviert 
bzw. mit ```true```aktiviert werden.

* autoUp  
Für jeden Rollladen kann hier das automatische Öffnen mit ```false```deaktiviert 
bzw. mit ```true```aktiviert werden.