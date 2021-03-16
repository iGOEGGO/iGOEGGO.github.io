# Exploration

Der Teil unserer Applikation, der zur Exploration verwendet werden kann, beinhaltet folgende Funktionen, die es ermöglichen sich einen Überblick über einen etwaigen Datensatz zu verschaffen: 

* Boxplot
* Histogramm
* QQ-Plot
* ECDF

Die Exploration soll dazu dienen, ein Gefühl für die Lage einer numerischen Spalte zu bekommen. Fragen wie: Sind meine Messungen normalverteilt oder sind Ausreißer vorhanden, lassen sich mit den unten angeführten Funktionen leicht beantworten.



### Boxplot

Auf einem Boxplot sind bestimmte Dinge leicht ersichtlich: Beginnen tut ein Boxplot beim niedrigsten Wert der im Datensatz vorkommt. Dieser wird auf der horizontalen Achse aufgetragen und durch einen vertikalen Strich gekennzeichnet. Der nächste Wert stellt das erste Quartil (Q1) da. Das Q1 ist der Punkt, wo 25% der Messungen unter dem entsprechendem X-Wert liegen. Außerdem ist hier der Beginn der Box, die für den Boxplot namensgebend ist. Innerhalb der Box, nicht unbedingt in der Mitte, befindet sich ein vertikaler Strich, der die Box in zwei Teile trennt. Dieser Strich ist der Median. Im Bereich zwischen Q1 und dem Median liegen 25% der Messwerte, unter dem Median liegen 50% der Werte, über dem Median die andere Hälfte. Die Box endet beim Q3 und (75% Percentil) und der letzte Wert des Boxplots ist wiederum der höchste, der in der gesamten Spalte vorkommt. Sind Ausreißer vorhanden, dann beginnt und endet der Whisker (so werden die Linien links und rechts der Box auch genannt) nicht bei niedrigsten und höchsten Wert, sondern überlicherweise bei einer Distanz die der Boxbreite * 1.5 entspricht. 

//Bild vom example Boxplot

Im iGÖGGO kann ein Boxplot ganz leicht erstellt werden, hierzu muss man auf den `Exploration` Tab gehen, und im Drop down die `Boxplot` Funktion auswählen. Mit dem `Add` Knopf kann man ein neues Boxplot Fenster hinzufügen.

In diesem Fenster lässt sich eine numerische Spalte des geladenen Datensatz auswählen. Wenn die Spalte nicht richtig erkannt wird, dann löschen Sie das Boxplot Fenster und weisen der Spalte unter dem Transformationstab den korrekten Datentypen zu.

Standardmäßig ist im Dropdown Menü die erste numerische Spalte, die vom iGÖGGO erkannt wurde ausgewählt. Hat man die darzustellende Spalte ausgewählt, kann man durch klicken des Plot-Buttons den entsprechenden Plot erstellen.

//Gif iGÖGGO

Auf Wunsch lässt sich eine Linie am Mittelwert einblenden. Hierfür einfach in den Controls das Häkchen Linie am Mittelwert setzten. 



### Histogram

 