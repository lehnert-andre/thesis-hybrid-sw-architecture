# Tranistion der klassischen zur hybriden Software-Architektur

- Arbeitstitel: ``` ```
- Student: ``` ```
- Matrikelnummer: ``` ```
- Datum der Erstellung: ``` ```
- Betreuender Professor: ``` ```
- Betrieb: 
  ```
  eXXcellent solutions
  consulting & software gmbh
  Industriestraße 48
  70565 Stuttgart
  ```
- Betreuer im Betrieb: ```Andre Lehnert```

## Kontext und Gegenstand der Arbeit

„Was ist?“ etwa ½ Seite Text über den Startzustand: das Umfeld, den Stand der Wissenschaft und das Problem, das mit der Arbeit zu lösen sein soll.

- Entwicklung individueller datengetriebener Softwaresysteme
- Großteil der Software für den internen Betrieb vorgesehen, z.B. für Steuerungs-, Administrations- oder Verwaltungsaufgaben.
- Darstellung vieler Daten
- Fokus liegt auf Single-Page-Applications (SPA) für die Darstellung im Client.
- Web-Frameworks für die Umsetzung von SPAs sind zurzeit Angular und Vue.js
- Die SPA kommuniziert mit mindestens einem REST-Service zum Datenaustausch.
- Die Backend-Services besitzen meistens eine Datenbank zur Persistierung.
- Zustände der Anwendung bzw. der Sessions werden stehts beim Client oder in der Datenbank gehalten.
- Diese Lösung setzt einen Büroarbeitsplatz mit stetiger Netzwerkverbindung vorraus.

- Das "mobile Arbeiten" ist mit der aktuellen Situation kaum sinnvoll.
- Daten, Kennzahlen und Metriken sollen vom Geschäftsführer per Tablet abgerufen werden können.
- Aktionen sollen per Smartphone von unterwegs ausgelöst werden können.
- Die Arbeit im Zug soll auch ohne permanente Netzwerkverbindung möglich sein.

- Seit der Vorstellung von Apache Cordova im Jahr XXXX sind zahlreiche Frameworks, wie Phonegap, Ionic, ReactNative, Flutter und Electron  entstanden, die die hybride Nutzung einer Code-Basis auf verschiedenen Plattformen und Betriebssystemen ermöglichen.
- In dieser Arbeit wird eine SPA-Anwendung vorrausgesetzt, sodass HTML, CSS und JavaScript als Basis dienen.


## Ziele

„Was soll?“ etwa ½ Seite abstrakt: Welche Forschungsfragen sollen beantwortet werden? Was soll erreicht werden? Welche wissenschaftlichen Erkenntnisse sollen gewonnen werden?

- Analyse einer aktuellen Schichtenarchitektur mit einem Client, Server und einer Datenbank
- Überführung der Schichtenarchitektur in eine hexagonale Software-Architektur (auch Zwiebel- oder Clean-SW-Architektur), um die einzelnen Bausteine der ursprünglichen Schichten präsent darzustellen
  - Im Kern die Geschäftslogik
  - Schichten der Datenaufbereitung mit ihren Bausteinen Richtung Client und Richtung Datenhaltung/ externer Systeme
  - Zugriffsschichten mit ihren Bausteinen Richtung Client und Richtung Datenhaltung/ externer Systeme
  - Der **Fokus liegt dabei auf dem Client**, dessen Rolle, den eigenen Schichten und Bausteine zur Datenbereitstellung.
    In der aktuellen Schichtenarchitektur ist der Client unterrepräsentiert bzw. die konkrete Rolle der "Dialogkern-Schicht" unscharf.
    Häufig wird der "Dialogkern" als Teil einer Komponente (vlg. Angular) gesehen. Die Schichtentrennung wird dadurch aufgeweicht.
  - Es wird empfohlen für den Client und den Server jeweils eigene Hexagone zu verwenden
- Nach der Analyse und während der Überführung wird sich der Bedarf nach einem Proxy, Adapter bzw. Bridge zeigen. 
  Falls ein solcher Baustein zur Lösung notwendig ist, ist eine Referenzimplementierung vorzunehmen.

![Schichtenarchitektur](./eXX_Schichtenarchitektur.JPG "Beispiel einer aktuellen Schichtenarchitektur")

![Hexagonale Architektur](https://speakerd.s3.amazonaws.com/presentations/de8629f0bf520131c2e20239d959ba18/slide_11.jpg?1400675141 "Hexagonale Architektur von https://fideloper.com/hexagonal-architecture")

### Optional/ in Klärung

- Die Code-Basis des Clients sind HTML, CSS und JavaScript. Daher steht das Problem der nativen UI-Elemente und dem Look´n´Feel, z.B. für Android, Apple MacOS oder Windows im Raum.

## Artefakte

„Was soll?“ konkret: Stichpunktartig formuliert, welche konkreten Dinge produziert werden sollen. Dazu gehört stets das Thesisdokument, ggf. Programme wie Spezifikationen, Implementationen, Prototypen, Handbücher, oder Videos, Filme.

- Spezifikation einer Referenzarchitektur für hybride Web-Anwendungen.
  - Eine Darstellungsform wären zwei Hexagone, für den Client und den Server, und deren Bausteine auf den einzelnen Schichten
- Transitionsprozess der klassischen Software-Architektur des Unternehmens zur kompatiblen und hybriden Software-Architektur.
- Referenzimplementierung einer Proxy-, einer Adapter- oder einer Bridge-Komponente, falls notwendig.
  - Diese Komponente/ dieser Baustein wäre als Teil der Referenzarchitektur sichtbar

## Aufgaben

„Wie soll?“: Stichpunktartig einzelne Aufgabenpakete, die vom Start bis zu den Zielen zu bearbeiten sind. Ggf. Vorgehensweisen, Methoden, Lösungsansätze nennen. Ggf. Umfang abschätzen, Reihenfolgen festlegen, Prioritäten setzen.



## Literatur

Bücher, Artikel, elektronische Quellen zum Thema

- ⭐ Formen der Datenpersitierung in Electron, mit Vor- und Nachteilen, sowie der "Bundling" Eigenschaften (DB im Electron Bundle) https://www.techiediaries.com/electron-data-persistence/ 

Zur "hexagonalen" SW-Architektur:
- http://alistair.cockburn.us/Hexagonal+architecture
- https://fideloper.com/hexagonal-architecture
- https://www.infoq.com/news/2014/10/exploring-hexagonal-architecture/
- ⭐ https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html
- http://www.dossier-andreas.net/software_architecture/layers.html

## Legende

⭐: Leseempfehlung
