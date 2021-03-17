# Monitoring

Das Monitoring, beziehungsweise Bookmarking, kann für die Speicherung der Zwischenstände auf der Webseite verwendet werden. Die gespeicherten Konfigurationen können dann zu späteren Zeitpunkten wiederhergestellt werden, auch von einem anderen Computer.

### Bookmarks verwalten

Über das Lesezeichen-Symbol in der rechten oberen Ecke, können Bookmarks hinzugefügt oder abgerufen werden.

![Bookmark Ansicht](./../images/bookmark-ansicht.png)

### Bookmark erstellen

Durch einen Klick auf "Bookmark hinzufügen" öffnet sich ein neues Fenster, in welchem man eine Bezeichnung und eine Beschreibung festlegen kann. Diese Felder dienen später zur leichteren Wiederherstellung der Bookmarks. Unter den Eingabefeldern befindet sich ein Link, welcher kopiert werden kann, um den gespeicherten Stand im Browser aufzurufen. Sobald alles eingetragen wurde, wird durch einen Klick auf den "OK" Button der Bookmark in einer Datenbank angelegt.

![Bookmark erstellen](./../images/bookmark-erstellen.png)

#### Was wird gespeichert?

Das Bookmarking selbst kann aufgrund bestimmter Begrenzungen nicht alles abspeichern. Einfache Datenanalysen, ohne Transformationen, können zur Gänze abgespeichert und wiederhergestellt werden. Bei der Speicherung der Datensätze wird immer nur der aktuelle Datensatz abgespeichert, wodurch es nicht möglich ist Diagramme, die Zwischenstände des jeweiligen Datensatzes verwenden, korrekt wiederherzustellen. Es werden alle Diagramme stehts anhand der aktuellen Form der Datensätze, inklusive aller Transformationen, bei der Wiederherstellung neu generiert.

### Bookmark wiederherstellen

Die Wiederherstellung eines Bookmarks kann auf zwei Arten durchgeführt werden:

1. durch Eingabe des Links

Bei der Abspeicherung eines Bookmarks wird bereits ein Link angezeigt. Dieser kann direkt in die Suchleiste des Browser kopiert und aufgerufen werden. Wodurch die Applikation wiederhergestellt wird.

![Suchleiste im Browser](./../images/bookmark-browser.png)

2. direkt in der Applikation

Sollte man sich bereits auf der Webseite befinden, kann durch einen Klick auf das Lesezeichen-Symbol und einen weiteren Klick auf "Bookmarks abrufen" ein Fenster, zum Öffnen und Suchen nach Bookmarks, angezeigt werden.

![Tabelle aller Bookmarks](./../images/bookmark-table.png)

Die Tabelle zeigt alle gespeicherten Bookmarks an. Wobei "bez" für die Bezeichnung steht und "info" für die Beschreibung. Außerdem werden Datum und Uhrzeit automatisch abgespeichert. Durch einen Klick auf einen der "Abrufen" Buttons öffnet sich ein neuer Tab im Browser, welcher den gewählten Bookmark wiederherstellt.

Über die Suchleiste kann die Tabelle gefiltert werden, wobei nach den drei Spalten "bez", "info" und "time" gefiltert wird. Es genügt dabei zum Beispiel einen Teil des Zeitstempels angeben. Das gleiche gilt auch für die anderen Spalten. Zusätzlich können die Spalten durch einen Klick auf einen der Spaltennamen absteigend oder aufsteigend sortiert werden.

![Beispiel Suchleiste für Bookmarks](./../images/bookmark-search.png)