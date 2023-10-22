---
# bibliography: references.bib

title: Daten visualisieren

abstract: ""

execute: 
  echo: false
---

::: {.callout-warning}
## Work in Progress
:::

Daten und Diagramme

## Diagramme erstellen

::: {.callout-warning}
Excels Diagrammtypen erfordern, dass die Daten in einem bestimmten Format vorliegen. Das notwendige Format hängt vom Diagrammtyp ab. Es lassen sich deshalb nicht alle Visualisuerungen aus den gleichen Datenstrukturen erzeugen. 
:::

### Datenvorbereitung

Die verschiedenen Diagrammtypen erfordern unterschiedliche Datenformate. Deshalb müssen die Daten für die Visualisierung vorbereitet und in eine geeignete Form gebarcht werden.

Alle Werte, die visualisiert werden sollen, müssen einen Bereich bilden. Dieser Bereich kann innerhalb einer Tabelle liegen oder dynamische Felder umfassen.

Excel organisiert die Werte für die Darstellung in *Datenreihen*. Je nach Visualisierung besteht eine Datenreihe aus einer Überschrift und einer, zwei oder drei Spalten mit Werten.

::: {.callout-tip}
## Praxis
Es vereinfacht die Arbeit, wenn die Spalten einer Datenreihe möglichst nebeneinander geschrieben werden. Alternativ können die gleichen Teilspalten organisiert werden. Letzteres bietet sich immer dann an, wenn die Werte in die Breitform *transponiert* werden müssen.
:::

Erlaubt ein Diagramm horizontale oder vertikale Achsbeschriftungen, dann werden diese normalerweise in den Spalten *vor* den eigentlichen Werte für den Darstellungsbereicht positioniert. 

### Diagrammerstellung

Um ein Diagramm zu erstellen müssen die vorbereiteten Daten markiert werden. Excel Diagramme können *nicht* mit dynamischen Feldern umgehen, so dass *alle* darzustellenden Werte markiert werden müssen.

Ausser den Spaltenüberschriften sollten keine weiteren Daten markiert werden. Dazu gehören auch die Werte, die für die Beschriftung der X-Achse benötigt werden. @fig-diagramme-werte-markieren zeigt eine solche Markierung.

![Markierung der zu visualisierenden Werte](figures/markierte_werte_ohne_beschriftungen.png){#fig-diagramme-werte-markieren}

::: {.callout-important}
## Achtung
Oft liegen Daten als Tabellen oder Dynamische Felder vor. Verändert sich die Anzahl der Werte einer solchen Datenstruktur, betrifft diese Änderung **nicht** den markierten Wertebereich. Liegen neue Werte ausserhalb des markierten Bereichs für ein Diagramm, dann werden diese Werte nicht dargestellt. In solchen Fällen muss der Bereich für die Darstellung nachträglich erweitert werden.
:::

Nachdem wie zu visualisierenden Werte markiert wurden, kann das eigentliche Diagramm eingefügt werden. Dazu muss aus dem Menübalken `Einfügen` im Abschnitt `Diagramme` (@fig-menu-diagramme) die gewünschte Darstellung ausgewählt werden.

![Menübalken Einfügen/Diagramme](figures/menu-einfuegen-diagramme.png){#fig-menu-diagramme}

Die Auswahl erzeugt das gewünschte Diagramm für die markierten Daten auf dem aktuellen Arbeitsblatt.

### Diagrammbearbeitung

Sobald ein Diagramm erstellt wurde, kann es über das Menüband `Diagrammentwurf` angepasst werden. Dieses Menüband wird nur angezeigt, wenn ein Diagramm ausgewählt wurde.

![Menüband Diagrammentwurf](figures/menu_diagrammentwurf.png){#fig-menu-diagrammentwurf}

::: {.callout-tip}
## Praxis
Für die Datenvisualisierung sind das Untermenü `Diagrammelement hinzufügen` und das Kommando `Daten markieren` zentral, weil über sie die Darstellung gesteuert wird. 

Daneben wird das Farbschema über das Menü `Farben ändern` gesteuert.
:::

Das Untermenu `Diagrammelement hinzufügen` erlaubt es, einzelne Diagrammelement zur Visualisierung hinzuzufügen **oder zu entfernen**. Die möglichen Diagrammelemente hängen vom jeweiligen Diagrammtyp ab. 

Das Untermenu `Schnelllayout` bietet Vorlagen für die einzelnen Diagrammelemente. Diese Vorlagen dienen oft als Basis für die weitere Verfeinerung mit dem Untermenü `Diagrammelement hinzufügen`. 

Mit dem Untermenü `Farbenändern` können die im Diagramm verwendeten Farben angepasst werden. In diesem Menü finden sich verschiedene Farbpaletten. Diese Farbpaletten werden durch das aktuelle Farbschema der Arbeitsmappe bestimmt.

Im Bereich `Diagrammformatvorlagen` kann die allgemeine Darstellung angepasst werden. Diese Einstellungen sollten nur angepasst werden, um ein Diagramm für eine besondere Präsentation vorzubereiten. Normalerweise werden über diesen Bereich keine Änderungen vorgenommen. 

Das Kommando `Zeile/Spalte tauschen` ist bei guter Vorbereitung der Daten nicht notwendig. Dieses Kommando ändert für eine Visualisierung die Verwendung von Spalten in die Verwendung von Zeilen. Dieses Kommando ist entsprechend nur Notwendig, wenn die Daten zeilenweise anstatt spaltenweise vorbereitet wurden.

::: {.callout-warning}
Manche Visualisierungen verwenden ein komplexes internes Datenmodell, so dass die mehrfache Anwendung des Kommandos `Zeile/Spalte tauschen` nicht zwingend zur urspünglichen Darstellung führt. 
::: 

Mit `Daten markieren` werden die Datenreihen und Quellen für Achsbeschriftungen in der Arbeitsmappe festgelegt. Dieses Kommando öffnet den Dialog `Datenquelle auswählen`, mit dem die Daten den einzelnen Darstellungselementen zugewiesen werden. Mit diesem Kommando können die Datenreihen korrigiert werden, wenn die automatische Erkennung von Excel nicht das gewünschte Ergebnis erzielt hat.

Das Untermenü `Diagrammtyp ändern` erlaubt es, den Typ eines Diagramms zu verändern, ohne den Diagrammbereich zu verändern. Weil die verschiedenen Diagrammtyp recht unterschiedliche Anforderungen an die Datenorganisation haben, sollte hier nur Diagrammtypen innerhalb der gleichen Gruppe ausgewählt werden. Beispielsweise könnte so ein Balkendiagramm in ein Säulendiagramm geändert werden. 

Das Kommand `Diagramm verschieben` erlaubt es, ein Diagramm auf einem eigenen Arbeitsblatt zu platzieren. Dieses Kommando ist nur dann sinnvoll, wenn eine Arbeitsmappe zur Präsentation der Daten verwendet wird. 

### Dialog `Datenquelle auswählen`

Über das Kommando `Daten markieren` wird der Dialog `Datenquelle auswählen` (@fig-dialog-daten-markieren-windows) geöffnet, über den die Daten den Darstellungselementen zugewiesen werden.

![Dialog Datenquelle auswählen (Windows)](figures/datenquellen_auswaehlen_windows.png){#fig-dialog-daten-markieren-windows}

Durch einen Doppelklick auf eine Datenreihe öffnet sich ein zweiter Dialog, um eine Datenreihe zu konfigurieren (@fig-datenreihe-konfigurieren-windows). Über diesen Dialog sollten die Datenreihen konfiguriert werden, damit sicher gestellt wird, dass die Datenreihen auf die richtigen Werte verweisen.

![Datenreihe konfigurieren (Windows)](figures/datenreihe_konfigurieren_windows.png){#fig-datenreihe-konfigurieren-windows}

::: {.callout-warning}
## MacOs vs. Windows

Unter MacOS ist die gleiche Funktion etwas anders angeordnet. 

![Dialog Datenquelle auswählen (MacOS)](figures/dialog_daten_markieren.png){#fig-dialog-daten-markieren-macos}

Der Dialog besteht aus drei Teilen: 

- Der Teil `Bereichdetails` zeigt den Datenbereich des Diagramms an. Der angezeigte Bereich sollte **nicht** in diesem Teil verändert werden.
- Der Teil `Legendeneinträge (Reihen)` weist Spalten mit Werten den Datenreihen des Diagramms zu. In diesem Teil werden die verwendeten Datenbereiche angepasst, die im Teil `Bereichdetails` zusammengefasst angezeigt werden. 
- Im Teil `Ausgeblendete und leere Zellen` wird die Behandlung von leeren Zellen und `#NA`-Werten festgelegt. In diesem Teil sind nur selten Anpassungen notwendig.
:::

### Diagramme formatieren

Die Darstellungselemente von Diagrammen können über den **Formatierungsbereich** angepasst werden. Über den Formatierungsbereich lassen sich die alle Details eines Diagramms anpassen. 

::: {.callout-warning}
## MacOs vs. Windows

Zur Formatierung der Datenreihen wird der Formatierungsbereich benötigt. Dieser wird unter Windows über das Kommando `Auswahl formatieren` geöffnet. Die wichtigsten Formatierungen sind die Datenreihenformatierungen. Je nach Diagrammtyp lassen sich in dieser Rubrik Formatierungen in Abhängigkeit zu den abgebildeten Daten justieren.

![Formatierungsbereich öffnen (Windows)](figures/diagramm_formatierung_windows.png){#fig-formatierungsbereich-windows}

Unter MacOS wird der Formatierungsbereich über das Kommando `Formatierungsbereich` im Menüband `Format` geöffnet.

![Formatierungsbereich öffnen (MacOS)](figures/diagramm_formatierung_macos.png){#fig-formatierungsbereich-macos}

Nach dem Öffnen des Formatierungsbereichs können die einzelnen Darstellungselemente gezielt formatiert werden. Immer wenn ein Darstellungselement sich auf Datenreihen bezieht, lassen sich zuätzliche Formatierungen unter der Rubrik `Reihenoptionen` konfigurieren. Diese Optionen werden unter MacOs und Windows leicht unterschiedlich dargestellt (@fig-formatierungsbereich-datenreihen)

::: {#fig-formatierungsbereich-datenreihen layout-ncol=2 layout-valign="bottom"}

![Windows](figures/datenreihen_formatieren_windows.png){#fig-formatierungs_data-macos}

![MacOS](figures/datenreihen_formatieren_macos.png){#fig-formatierungs_data-macos}

Datenreihen formatieren
:::
:::



### Diagramme exportieren

Um ein Diagramm zum Einbetten in andere Programme bereitzustellen, muss das Diagramm aus Excel exportiert werden. Dazu ein Rechtsklick auf das Diagramm öffnet ein *Kontextmenü*, in welchem sich der Punkt `Als Grafik speichern ...` findet (@fig-diagramm-exportieren). 

::: {.callout-warning}
## MacOS vs. Windows

Das Kommando zum Speichern von Diagrammen heisst unter MacOS `Als Bild speichern ...` und unter Windows `Als Grafik speichern ...`.
::: 

![Kontextmenu zum Exportieren eines Diagramms](figures/diagramm_speichern_windows.png){#fig-diagramm-exportieren}

Anschliessend erscheint ein Dialog zum Speichern der Diagrammdatei (@fig-diagramm-speichern-unter). Standardmässig bietet dieser Dialog als `Dateityp` das Grafikformat `PNG` an, was in den meisten Fällen gewählt werden sollte. Alternativ können Diagramme in den Formaten `JPEG`, `GIF`, `PDF`, `BMP` und `SVG` exportiert werden. Hier sind für die Praxis nur die beiden Formate `PDF` und `SVG` von Bedeutung.

::: {.callout-tip}
## Praxis
Das `PDF`-Format sollte gewählt werden, wenn eine Grafik einzeln ausgedruckt werden soll. 
:::

::: {.callout-tip}
## Praxis
Das `SVG`-Format sollte gewählt werden, wenn das Diagramme grossformtig oder in hoher Qualität auf Web-Seiten veröffentlicht werden soll.
:::

![Auswahl zum Speichern eines Diagramms](figures/dialog_als_grafik_speichern.png){#fig-diagramm-speichern-unter}


## Diagrammtypen

Alle Excel Diagramme visualisieren Werte vom Datentyp **Zahl**. Um andere Datentypen zu visualisieren, müssen diese zuerst in Zahlen kodiert werden. 

### Balkendiagramme 

Excel unterscheidet zwischen Balken- oder Säulendiagrammen. Technisch unterscheiden sich die beiden Diagrammtype nur durch die Orientierung der Balken. Im Folgenden werden beide Diagrammtypen als Balkendiagramme bezeichnet. 

::: {.callout-note}
## Merke
Für ein  Balkendiagramm entspricht jeder Wert einem Balken und der Wert bestimmt dessen Grösse. 
:::

Die Anzahl der Werte entspricht der Anzahl der Balken. Daraus folgt, dass ein Balkendiagramm immmer diskrete Daten auf der X- und Zahlenwerte auf der Y-Achse abbildet.

Balkendiagramme können keine Werte zusammenfassen. Deshalb müssen Daten vor der Visualisierung als Balkendiagramm aggregiert werden. Normalerweise erfolgt ein gruppiertes Zählen mit `ZÄHLENWENNS()`. 

Die Werte können als Zeile oder als Spalte angegeben werden. Wird ein zweiter Vektor mit Textwerten angegeben, dann übernimmt Excel diese Werte als Beschriftung der X-Achse. 

::: {#fig-barchart-mono layout="[[45, 55]]" layout-valign="bottom"}

![Daten](figures/bar_chart_mono_data.png){#fig-daten}

![Diagramm](figures/bar_chart_mono.png){#fig-barchart-mono-vis}

Vorbereitete Datentabelle mit Balkendiagramm
:::

::: {.callout-note}
## Merke
Für Balkendiagramme mit zwei oder mehr Gruppen, **müssen** die Daten in der *Breitform* vorliegen.
:::

Gruppierte Daten werden farblich voneinander abgehoben. Die Farben können über das Farbschema der Arbeitsmappe über das Kommando `Farben ändern` angepasst werden.

::: {#fig-barchart-multi layout-ncol=2 layout-valign="bottom"}

![Daten](figures/balken_kategorisiert_daten.png){#fig-daten}

![Diagramm](figures/balken_kategorisiert.png){#fig-barchart-mono-vis}

Gruppierte Datentabelle mit Balkendiagramm 
:::

Sollen einzelne Kategorien farblich hervorgehoben werden, dann müssen die Werte gruppiert organisiert werden, wobei jeder Wert in einer eigenen Gruppe geführt wird (@fig-barchart-multicolor). 

::: {#fig-barchart-multicolor layout-ncol=2 layout-valign="bottom"}

![Daten](figures/balken_farblich_abgehoben_daten.png){#fig-daten}

![Diagramm](figures/balken_farblich_abgehoben.png){#fig-barchart-mono-vis}

Datentabelle und Balkendiagramm mit farblich abgehobenen Kategorien.
:::

### Spezielle Balkendiagramme 

Excel bietet zwei spezielle Formen von Balkendiagrammen: *Trichterdiagramme* und *Wasserfall*-Diagramme. Beide Diagramme sind *eindimensional*. 

Trichterdiagramme stellen die Balken horizontal zentriert dar, wobei nur positive Werte zulässig sind. Deshalb haben Excels Trichterdiagramme *keine* Beschriftung der X-Achse (@fig-trichterdiagramm).

::: {.callout-note}
## Merke
Trichterdiagramme unterscheiden sich von anderen Balkendiagrammen nur in der Anordnung der Balken.
:::

![Trichterdiagramm mit fünf Werten](figures/trichterdiagramm.png){#fig-trichterdiagramm}

::: {.callout-tip}
## Praxis
Weil Trichterdiagrammen keine beschriftete X-Achse haben und die Anordnung der Balken schwerer zu dekodieren ist, sollten diese Diagramme **nicht** verwendet werden.
:::

Wasserfalldiagramme stellen die Balken so dar als Folge dar. Diese Diagramme stellen positive und negative Werte gerichtet nebeneinander. Der Start des von links nach rechts gelesenene nächste Balken beginnt bei dem Wert, an dem der vorherige Balken endete. Bei positiven Werten befindet sich der Endpunkt über dem Startpunkt, bei negativen Werten darunter (@fig-wasserfall-leserichtungen). 

![Wasserfalldiagramm mit Leserichtungen](figures/wasserfalldiagramm2_richtungen.png){#fig-wasserfall-leserichtungen}

::: {.callout-note}
## Merke
Wasserfalldiagramme werden zur Visualisierung von Veränderungen über die Zeit verwendet.
:::

Bei Wasserfalldiagrammen kann die **Beschriftung** der X-Achse über ein zweite Datenspalte mitgegeben werden. Bei Trichterdiagrammen können auf die gleiche Weise die Beschriftungen der Y-Achse angepasst werden. In beiden Fällen müssen die Beschriftungen in der Spalte *vor* den Werten gespeichert sein.

### Histogramm

Ein Histogramm ist in Excel **immer** ein eindimensionales Balkendiagramm. Werden Werte aus mehreren Spalten übergeben, dann werden alle Werte im Histogramm abgebildet. 

::: {.callout-tip}
## Praxis
Für Daten mit diskreten Wertebereichen, sind Balkendiagramme **immer** einem Histogramm vorzuziehen.
:::

### Boxplot

### Punktdiagramm

### Blasendiagramm

Blasendiagramme ähneln Punktdiagrammen. Weil drei Merkmale kodiert werden, müssen die Daten in drei Spalten vorliegen. Dabei wird die linke Spalte für die X-Achse verwendet. Die mittlere Spalte wird für die Y-Achse verwendet. Die rechte Spalte enthält die Werte für die Grösse der Punkte. Prinzipiell lassen sich die Werte nachträglich noch umorganisieren, oft ist es aber einfacher, die Spalten vorher anzuordnen.  

![Beispiel eines Blasendiagramms](figures/bubble_chart.png){#fig-bubble-chart}

Eine Datenreihe eines Blasendiagramms besteht aus drei Merkmalen.

![Konfiguration der Datenreihen eines Blasendiagramms (MacOS)](figures/bubble-chart-datenreihen.png){#fig-datenreihen-bubble-chart}

### Linien-, Kreis- und Donutdiagramme 

Linien-, Kreis- und Donutdiagramme sind in Excel Varianten von Balkendiagrammen: Sie verwenden das gleiche Format für die Datenreihen und werden ansonsten gleich konfiguriert. Wie bei Balkendiagrammen, wird die X-Achse als eine diskrete Datenskalierung behandelt. Die Daten können also nominal- oder ordinalskaliert sein. 

::: {.callout-tip}
## Praxis

Kreis- und Donutdiagramme sind identisch mit Balkendiagrammen, wenn alle Werte **positiv** sind. Für mehr als drei Werte können die meisten Menschen sich diese Diagramme oft nicht richtig interpretieren. Deshalb sollten Kreis- und Donutdiagramme möglichst nur zur Darstellung (extremer) Mengenverhältinisse verwendet werden. Grundsätzlich ist ein Balkendiagramm einem Kreis- oder Donutdiagramm vorzuziehen. (s. @fig-kreisdiagramm-aehnliche-groessen und @fig-balken-aus-kreisdiagramm)
:::

![Kreisdiagramm mit ähnlich grossen Werten](figures/kreisdiagramm.png){#fig-kreisdiagramm-aehnliche-groessen}

![Balkendiagramm für die gleichen Werte aus @fig-kreisdiagramm-aehnliche-groessen](figures/balken_fuer_kreis.png){#fig-balken-aus-kreisdiagramm}

Excels **Liniendiagramme** zeichnen für jeden Wert auf der Y-Achse einen Punkt und verbinden die Punkte mit geraden Linien.

::: {.callout-warning}
## Achtung
Weil die X-Achse immer diskrete Daten abbildet, dürfen Liniendiagramme nicht mit Punktdiagrammen mit *interpolierten Linien* verwechselt werden. 
:::

::: {.callout-tip}
## Praxis
Excels Liniendiagramme sollten nur für sog. Paralleldiagramme verwendet werden, in denen mehrere diskrete Merkmale mit dem gleichen Wertebereich gegenübergestellt werden. Durch die Linien werden Unterschiede in den Ausprägungsprofilen sichtbar. 

@fig-parallel-plot zeigt ein solches Paralleldiagramm. Dieses Beispiel macht die Grenzen dieses Diagrammtyps sichbar, weil Excel sich überlagernde Linien nicht nebeneinander darstellen kann. 
:::

![Anwendung eines Liniendiagramms als Paralleldiagramm](figures/diagramm_parallel_plot.png){#fig-parallel-plot}

::: {.callout-note}
Eine Variante von Paralleldiagrammen sind sog. Netzdiagramme (bzw. Spider-Web-Diagramme). Netzdiagramme ordnen die Kategorien sternförmig an. In Excel finden sich Netzdiagramme unter der Kategorie `Wasserfalldiagramme`.
::: 

<!--
### Treemap-Diagramme
-->

## Mathematische Funktionen visualisieren



