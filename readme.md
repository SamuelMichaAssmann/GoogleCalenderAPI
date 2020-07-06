## Java Projekt "Google Calendar"

> Erstellen Sie ein Java-Programm, das auf einen beliebigen Google-Kalender zu-greift und die Kalender-Daten 
> im [iCalender-Format](siehehttp://www.ietf.org/rfc/rfc2445.txt) in eine Datei speichert. Das Programm soll
> über die Kommandozeile aufrufbar sein in der folgenden Form:
>
> **java〈Klassenname〉 〈Start-Datum〉 〈Ende-Datum〉 〈Text-Selektionskriterium 〈Dateiname〉**
> also z.B. java myclass 2011-05-012011-05-31 DHBW* export.ics
>
> Das Programm soll alle Kalendereinträge in die Zieldatei exportieren, deren Titel den Text-Selektionskriterien 
> entspricht. Alss für ”DHBW*” werden allemit den Buchstaben ”DHBW” beginnende Kalendereinträge exportiert und für 
> DHBW alle Kalendereinträge, deren Titel die Buchstaben DHBW enthalten.

[Aufgabenstellung Teil 1](https://studentdhbwmannheimde-my.sharepoint.com/:b:/g/personal/s190165_student_dhbw-mannheim_de/EUHeZ8cJKh1Ap2_KWjQ0xxIBqAIGJN5LkyIjnEv4_cgKfA?e=6fa6Jz)
[Aufgabenstellung Teil 2](https://studentdhbwmannheimde-my.sharepoint.com/:b:/g/personal/s190165_student_dhbw-mannheim_de/EWwFtltJit5PrqUhJopub2QBHO-CKFzuO3RUFCst-0BWdA?e=Yf1Ql5)

## Used Versions

- Gradle 6.5.1 (über gradlew.bat/gradlew.sh installierbar)

- Google Api Client 1.30.9
      
- Google Oauth Client Jetty 1.31.0

- Google Api Services Calendar v3-rev411-1.25.0

- Java SDK 14.0.1

- Java JRE 1.8.0_251

## ToDo's

* [x] Google-Kalender zu-greift

* [x] Daten speichern

* [x] speichen in Calender-Format

* [x] Kommandozeile aufrufbar

* [x] Text-Selektionskriterien

* [x] objekt-orientiertes Design

* [x] [Quickstartguide](developers.google.com/calendar/quickstart/java)

* [x] [gradle](gradle.org) installieren

* [x] aktuelle JDK installieren

* [x] Quelltext kommentierten

* [x] Programm testen

* [x]  Dokumentation

* [x]  Interfaces (in class calendar)

## Erweiterung

* [x] Benutzeroberfläche

* [x] Menüs und Untermenüs

* [x] File (Save, Exit)

* [x] Application (Settings)

* [x] Help (About)

* [x] Hauptfenster enthält eine Tabelle

* [ ] Spalten ̈uberschriften (Ereignis, von, bis, Datum).

* [x] Zeitraum anzeigen

* [x] automatische Größe

* [-] Kalender-URL (nicht möglich mit OAuth2)

* [x] Informationen über den Entwickler

* [x] Input-Validierung

* [-] Spinner-Felder (nicht kompatibel mit JFrame)

* [ ] Speicherung von Einstellungen

 

## ACHTUNG:

* Kalender-URL

Aus Sicherheitsgründen habe ich diesen Punkt expliziet weggelassen, da mit einem POST zugriff via HTTP auf
die URL zugegriffen werden würde, was die hinterlegten Credetials so wie den aufgerufenen Kalender zu einem 
potenziellen Ziel für ein externes zugreifen macht. 

* Spinner-Felder

Da Spinnerfelder auf JavaFX laufen, ich jedoch JFrame gewählt habe ist es zwar möglich beide Bibliotheken 
aufzurufen jedoch können diese nicht miteinander komunizieren. Was eine Wasserfallstruktur des Programmes erfordern würde. 
Jedoch ist das Programm Objektorientiert.

Somit sind diese beiden Punkte aus genannten Gründen nicht vorhanden.


## Dokumentation und Aufbau

Folgender Aufbau:

* **main.java** --> diese Datei ist zum Starten des Programmes gedacht
	- greift und startet calendar.java


* **calendar.java** --> diese Datei Startet die Oberfläche mit JFrame
	- greift auf savedata.java zu um Dateien zu speichen
	- greift auf calendarAPI.java zu um Daten zu bekommen
	- visualisiert Daten auf der Oberfläche


* **savedata.java** --> diese Datei speichert Daten mit einem beliebigen Dateinamen in das selbe Verzeichniss

* **calendarAPI.java** --> diese Datei greift via Credentials auf einen definierten Google Kalenderzu
	- gibt an calendar.java ein String zurück
	- interne Verarbeitung in vorm "Events" 

## Liste aller Klassen (mit Vererbung)

* class calendarAPI

* class calendar implements ActionListener

* class savedata


## Liste aller Methoden (mit Exceptionvererbung)


* **void** actionPerformed(ActionEvent object)

* **String** toHtml(String s)

 ---------------------------------------

* **Credential** getCredentials *(final NetHttpTransport HTTP_TRANSPORT)* throws __IOException__

* **Calendar** apisetup *()* throws __IOException, GeneralSecurityException__

* **Events** evtstartend *(String start, String end, String count)* throws __IOException, GeneralSecurityException__

* **Events** evtsearch + evtextsearch *(String start, String end, String count, String data)* throws __IOException, GeneralSecurityException__

* **String** evttoString *(Events events)*

* **String** toString *(Events event)*

 ---------------------------------------

* **void** writedata *(String dateiName, String txt)*


## Zum Starten

Eine class main ausführen mit gradle run im Hauptordner

```sh
public static void main(String... args) throws IOException, GeneralSecurityException {
     new calendar();
}
```

## Datum Input

- yyyy-mm-dd
- dd-mm-yyyy
- yyyy.mm.dd
- dd.mm.yyyy















