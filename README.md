# Eine hybride Software-Architektur für die plattformübergreifende Anwendung "Online Planung - Routenplanung" der Stadtwerke München

Weitere Vorschläge:

> ...

---

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

__„Was ist?“ etwa ½ Seite Text über den Startzustand: das Umfeld, den Stand der Wissenschaft und das Problem, das mit der Arbeit zu lösen sein soll.__

Die eXXcellent solutions consultng & software GmbH berät, konzipiert und entwickelt mit ihren Kunden individuelle datengetriebene Softwaresysteme. Der Großteil der Software ist für den internen Betrieb vorgesehen, z.B. für Steuerungs-, Administrations- oder Verwaltungsaufgaben. Typischerweise sind dafür grafische Oberflächen zur Darstellung vieler Informationen notwendig. 

Die Oberflächen werden dem Kunden meistens über Web-Technologien, wie HTML, CSS und JavaScript im Browser bereitgestellt. Hierzu werden Single-Page-Applications (SPA) mit Web-Frameworks, wie Angular, React oder Vue.js verwendet. Zum Abruf der darzustellenden Informationen kommuniziert die SPA mit mindestens einem Server zustandslos mittels HTTP entsprechend des Representational State Transfer (REST) Paradigmas. Dabei werden die Zustände der Anwendung stets im Browser oder in der Datenbank gehalten. Eine solche Lösung setzt daher einen Büroarbeitsplatz mit stetiger Netzwerkverbindung vorraus.

Für die Stadtwerke München entwickelt die eXXcellent solutions im Kontext des Online Planungs Systems (OnPa) einen neuen Routenplaner, mit dem Baustellenprüfer der Stadtwerke ihre Arbeitstage planen können. Der Projektstart ist für März 2020 vorgesehen.

Aus dem OnPa-System werden die zu überprüfenden Baustellen exportiert und in dem neuen Routenplaner auf einer interaktiven Karte (Google Maps, Here) angezeigt. Die Baustellenprüfer haben die Möglichkeit die Reihenfolge der Termine zu tauschen, Termine des nächsten Tages vorzuziehen oder Termine mit dem Kollegen zu tauschen. Das Ziel ist eine Routenptimiertung, die zusätzlich durch das neue System unterstützt wird. Dazu findet eine automatische Optimierung der Reihenfolge der Termine (Traveling Salesman Problem) statt, die mit Echtzeitdaten über den Verkehr angereichert wird.
Der neue Routenplaner bietet zusätzlich den Zugriff auf Details zu den Terminen an, wie Kontaktdaten und Prüfprotokolle.

Die Baustellenprüfer haben an ihren Büroarbeitsplätzen die Möglichkeit die Tagesplanung im Detail vorzubereiten, Termine abzustimmen und Protokolle auszudrucken. Unterwegs soll der OnPa Routenplaner den Zugriff auf die Termine erlauben und die Navigation zu den Baustellen steuern. Die Anwendung muss daher auf Desktop Rechnern und Smartphones nutzbar sein.


[Link zum Prototyp des OnPa Routenplaners (ohne den Server zur Routenoptimierung)](https://swm-onpo-routenplaner-deploy.web.app/)


Seit der Vorstellung von Apache Cordova bzw. Adobe PhoneGap im Jahr 2009 sind zahlreiche Frameworks, wie Ionic, ReactNative, Flutter,  Electron und schließlich die Web-Standards für Progressive Web Apps entstanden, die eine Nutzung einer einzigen Code-Basis auf verschiedenen Plattformen ermöglichen. Anwendungen mit dieser Eigenschaft werden folgend als _hybride Anwendungen_ bezeichnet.

Im Gegensatz zum Büroarbeitsplatz unterstützt die lokale Speicherung der notwendigen Termindaten vom Server im Anwendungsclient das mobile Arbeiten der Baustellenprüfer --- ohne lange Wartezeiten und Verbindungsabbrüche. Die Navigation zwischen den Baustellen erfordert zusätzlich den Zugriff auf die Positionsdaten des Smartphones.

## Ziele

__„Was soll?“ etwa ½ Seite abstrakt: Welche Forschungsfragen sollen beantwortet werden? Was soll erreicht werden? Welche wissenschaftlichen Erkenntnisse sollen gewonnen werden?__

Im Rahmen der Arbeit wird eine Software-Architektur auf Basis der aktuellen Schichtenarchitektur der eXXcellent solutions entwickelt, die eine plattformübergreifende Nutzung unterstützt und nur eine Code-Basis nutzt. Die OnPa Routenplaner Anwendung der Stadtwerke München dient als Referenz-Projekt. 

Für die Spezifikation der hybriden Software-Architektur wird die jetzige Schichtenarchitektur (siehe Abb.) in eine hexagonale Software-Architektur überführt. 
Dieser Architekturstil wird je nach Quelle Hexagonal, Ports and Adapters, Onion oder Clean Architecture genannt und ist eine Weiterentwicklung der Schichtenarchitekturen durch Dependency Inversion (muss weiter erläutert werden). 

Im Kontext des Domain-Driven Design (vgl. (1), S. 41) definiert jedes Hexagon einen Bounded Context, bei dem das Domänen Model und die Geschäftslogik der Domäne (vgl. Businesslogikschicht der aktuellen Schichtenarchitektur) jeweils der Kern sind. Die weiteren Schichten werden als Ring um diesen Anwendungskern gelegt, dabei verlaufen die Abhängigkeiten zwischen den Schichten immer von Außen nach Innen.
Dies hat den Vorteil, dass weitere Schichten, zum Beispiel zur Realisierung der Offlinefähigkeit, ohne Änderung der innenliegenden Schichten hinzugefügt werden können.

Der Fokus der Arbeit liegt auf dem Client und der Erarbeitung einer eigenständigen hexagonalen Teil-Architektur, sodass der Client und der Server jeweils ein Hexagon besitzen und miteinander kommunizieren.
Dabei wird das Problem der aktuellen Schichtenarchitektur addressiert, bei der der Client unterrepräsentiert bzw. die konkrete Rolle der Dialogkern-Schicht unscharf ist, da der Datenzugriff auf den Server und eine globale Zustandsverwaltung mit einem Store (vgl. Flux-Pattern) inkludiert sind. 

![Schichtenarchitektur](./eXX_Schichtenarchitektur.JPG "Beispiel einer aktuellen Schichtenarchitektur")

![Hexagonale Architektur](https://speakerd.s3.amazonaws.com/presentations/de8629f0bf520131c2e20239d959ba18/slide_11.jpg?1400675141 "Hexagonale Architektur von https://fideloper.com/hexagonal-architecture")

## Artefakte

__„Was soll?“ konkret: Stichpunktartig formuliert, welche konkreten Dinge produziert werden sollen. Dazu gehört stets das Thesisdokument, ggf. Programme wie Spezifikationen, Implementationen, Prototypen, Handbücher, oder Videos, Filme.__

- Spezifikation einer Referenzarchitektur für hybride Web-Anwendungen auf Basis der OnPa Routenplaner Anwendung.
  - Als Darstellungsform werden zwei Hexagone, für den Client und den Server, gewählt. 
    - Die Bausteine der einzelnen Schichten werden erläutert.
    - Der Datenaustausch wird dargestellt.
  - Die beiden Schichten Präsentations- und Dialogkernschicht im Client werden analysiert und bei Bedarf weiter zerlegt. 
- Darstellung des Transitionsprozess der klassischen Software-Architektur des Unternehmens zur kompatiblen und hybriden Software-Architektur.
- Referenzimplementierung eines Bausteins zur Offlinefähigkeit
  - Dieser Baustein ist als Teil der Referenzarchitektur sichtbar
  - Möglicher Lösungsansatz: Ein Proxy wird als Baustein um die Client- und Server-Kommunikation gelegt. Aus Sicht des Clients repräsentiert der Proxy den Server. Der Proxy hat allerdings die Möglichkeit der Datenpersistierung, sodass Anfragen des Clients mit gespeicherten Daten beantwortet werden können.
  - Die Implementierung ist stark von dem hybriden Framework abhängig. 
  





## Aufgaben

__„Wie soll?“: Stichpunktartig einzelne Aufgabenpakete, die vom Start bis zu den Zielen zu bearbeiten sind. Ggf. Vorgehensweisen, Methoden, Lösungsansätze nennen. Ggf. Umfang abschätzen, Reihenfolgen festlegen, Prioritäten setzen.__

Die Aufagen gliedern sich in einen theoretischen und konzeptionellen Teil und einen Teil zu Implementierung eines Prototypen, die die Umsetzbarkeit des Konzeptes zeigt.

- Beschreibung der aktuellen Schichten-Architektur anhand des Referenz-Projektes
- Überfühung der Schichten-Architektur in eine hexagonale Architektur mit der Identifikation der einzelnen Bausteine pro Schicht
- Herauslösen des Clients in ein eigenes Hexagon
  - An dieser Stelle ist es ggf. notwendig eine zusätzliche Schicht einzuführen, die als äquivalent zur Datenzugriffsschicht des Servers fungiert
- Recherche zu Best-Practices der Offlinefähigkeit im Client
  - An dieser Stelle soll nur ein (max. zwei) hybride Web-Frameworks betrachtet werden, z.B. Electron oder PWAs
  - Die eXXcellent stellt eine Anforderungsliste bezüglich Funktionalität, Kompatibilität, Erweiterbarkeit und Technologien (Technologie der Code-Basis) bereit.
- Konzeption einer Lösung zur Offlinefähigkeit
- Referenzimplementierung der Lösung zur Offlinefähigkeit



## Literatur

__Bücher, Artikel, elektronische Quellen zum Thema__

- (1) ⭐ Domain-Driven Design Distilled; Vernon, Vaughn; Addison-Wesley; ISBN: 978-0-13-443442-1
- https://ddd-referenz.de/


Zu hybriden Apps:
- (2) ⭐ Formen der Datenpersitierung in Electron, mit Vor- und Nachteilen, sowie der "Bundling" Eigenschaften (DB im Electron Bundle) https://www.techiediaries.com/electron-data-persistence/ 
- https://www.heise.de/developer/artikel/Electron-und-Cordova-vs-PWA-wann-was-wie-und-warum-4634262.html


Zur "hexagonalen" SW-Architektur:
- http://alistair.cockburn.us/Hexagonal+architecture
- https://fideloper.com/hexagonal-architecture
- https://www.infoq.com/news/2014/10/exploring-hexagonal-architecture/
- ⭐ https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html
- http://www.dossier-andreas.net/software_architecture/layers.html
- Zwiebelarchitektur: https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/

## Legende

⭐: Leseempfehlung
