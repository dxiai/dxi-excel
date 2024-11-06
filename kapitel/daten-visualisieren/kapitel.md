---
# bibliography: references.bib

title: Daten visualisieren

abstract: ""

execute: 
  echo: false
---

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
Für die Datenvisualisierung sind das Untermenü `Diagrammelement hinzufügen` und das Kommando `Daten auswählen` zentral, weil über sie die Darstellung gesteuert wird. 

Daneben wird das Farbschema über das Menü `Farben ändern` gesteuert.
:::

Das Untermenu `Diagrammelement hinzufügen` erlaubt es, einzelne Diagrammelement zur Visualisierung hinzuzufügen **oder zu entfernen**. Die möglichen Diagrammelemente hängen vom jeweiligen Diagrammtyp ab. 

Das Untermenu `Schnelllayout` bietet Vorlagen für die einzelnen Diagrammelemente. Diese Vorlagen dienen oft als Basis für die weitere Verfeinerung mit dem Untermenü `Diagrammelement hinzufügen`. 

Mit dem Untermenü `Farbenändern` können die im Diagramm verwendeten Farben angepasst werden. In diesem Menü finden sich verschiedene Farbpaletten. Diese Farbpaletten werden durch das aktuelle Farbschema der Arbeitsmappe bestimmt.

Im Bereich `Diagrammformatvorlagen` kann die allgemeine Darstellung angepasst werden. Diese Einstellungen sollten nur angepasst werden, um ein Diagramm für eine besondere Präsentation vorzubereiten. Normalerweise werden über diesen Bereich keine Änderungen vorgenommen. 

Das Kommando `Zeile/Spalte tauschen` ist bei guter Vorbereitung der Daten nicht notwendig. Dieses Kommando ändert für eine Visualisierung die Verwendung von Spalten in die Verwendung von Zeilen. Dieses Kommando ist entsprechend nur Notwendig, wenn die Daten zeilenweise anstatt spaltenweise vorbereitet wurden.

::: {.callout-warning}
Manche Visualisierungen verwenden ein komplexes internes Datenmodell, so dass die mehrfache Anwendung des Kommandos `Zeile/Spalte tauschen` nicht zwingend zur ursprünglichen Darstellung führt. 
::: 

Mit `Daten auswählen` werden die Datenreihen und Quellen für Achsbeschriftungen in der Arbeitsmappe festgelegt. Dieses Kommando öffnet den Dialog `Datenquelle auswählen`, mit dem die Daten den einzelnen Darstellungselementen zugewiesen werden. Mit diesem Kommando können die Datenreihen korrigiert werden, wenn die automatische Erkennung von Excel nicht das gewünschte Ergebnis erzielt hat.

::: {.callout-warning}
## MacOS vs. Windows
Das Kommando `Daten auswählen` heisst unter MacOS `Daten markieren`.
::: 

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

#### Darstellung optimieren {#sec-barcharts-optimieren}

Bei der Darstellung von Balkendiagrammen verwendet Excel immer  Standardeinstellungen. Diese nutzen die Fläche des Diagramms nicht unbedingt optimal: Auf der Y-Achse wird immer eine Hauptbeschriftung oberhalb des grössten Wers eingefügt und die Abstände  zwischen den Balken sind grösser als die Balken (@fig-balken-mit-standard). 

![Balkendiagramm mit Standardeinstellungen](figures/balken_standardeinstellungen.png){#fig-balken-mit-standard}

Die Y-Achse kann immer auf den Maximalwert begrenzt werden. Dazu wird die Achsbeschriftung mit der Maus ausgewählt. Anschliessend können in den Achsenoptionen die Grenzen der Y-Achse festgelegt werden. Hier sollte das Maximum auf den grössten dargestellten Wert gesetzt werden (s. @fig-achseneinstellungen).

![Konfiguration der Achseneinstelleungen](figures/balken_einstellungen_achsenintervall.png){#fig-achseneinstellungen}

::: {.callout-note}
## Merke
Für Balkendiagramme sollte das Minimum der Y-Achse immer `0.0` sein.
:::

Die Abstände zwischen den Balken werden über die Formatierung der Balken gesteuert. Dazu muss ein Balken mit der Maus ausgewählt werden. Die einzige Einstellungskategorie für die Datenformatierung sind die `Reihenoptionen`, wo sich die beiden Einstellungen `Reihenüberlappungen` und `Abstandsbreite` finden (s. @fig-balken-abstaende).

![Balkenbreite und -abstände konfigurieren](figures/balken_abstaendeeinstellungen.png){#fig-balken-abstaende}

@fig-balken-einstellungen-visualisierung zeigt die Bedeutung der beiden Optionen.

![Unterschied zwischen Reihenüberlappung und Abstandsbreite](figures/balken_abstaendeeinstellungen-visualisierung.png){#fig-balken-einstellungen-visualisierung}

Die Option `Reihenüberlappung` legt die Abstände ziwschen Balken in der gleichen Kategorie fest. Die Abstände werden in Prozent der Überlappung angegeben. 0% bedeutet keine Überlappung ohne Abstand. 100% bedeutet vollständige überlappung und -100% bedeutet einen Abstand einer Balkenbreite.

Die Option `Abstandsbreite` legt die Abstände zwischen den Kategorien fest. Die Abstände werden in Prozent der Balkenbreite angegeben.

::: {.callout-warning}
## Achtung

Die Überlappung und die Balkenbreite wird auch dann berücksichtigt, wenn ein Balken nicht dargestellt wird!
:::

Um farblich voneinander unterschiedene Kategorien mit gleicher Balkenbreite wie in @fig-barchart-multicolor zu erzeugen, muss die `Reihenüberlappung` auf `100%` gesetzt werden. Anschliessend können die Abstände mit der Option `Abstandsbreite` kontrolliert werden. @fig-barchart-multicolor verwendet eine `Abstandsbreite` von `10%`.

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

::: {.callout-note}
## Merke
Ein Histogramm ist eine Visualisierung der Werteverteilung als Balkendiagramm. 
:::

Histogramme visualisieren *kontinuierliche* bzw. metrischskalierte Wertebereiche, indem zwischen dem kleinsten und dem grössten Wert gleichmässige Intervalle gebildet werden und anschliessend die Anzahl der Werte in den Intervallen bestimmt wird.

::: {.callout-note}
## Merke
Für ein Excel-Histogramm müssen die Werte vor der Visualisierung **nicht** aggregiert werden.
:::

Ein Histogramm wird oft über einen Vektor erstellt. Werden die Daten so vorbereitet, dass unter den Werten keine anderen Daten stehen, dann kann die *gesamte Spalte* markiert werden, indem auf den Spaltenbuchstaben mit der Maus geklickt wird. Anschliessend kann das Histogramm in die Arbeitmappe eingefügt werden (@fig-histogramm-erstellen)

![Histogramm erstellen](figures/histogramm_erstellen.png){#fig-histogramm-erstellen}

Ein Excel-Histogramm ist **immer** ein eindimensionales Balkendiagramm. Werden Werte aus mehreren Spalten übergeben, dann fliessen alle Werte in das Histogramm ein. 

#### Histogramme optimieren

::: {.callout-tip}
## Praxis
Im Gegensatz zu Balkendiagrammen wird die Y-Achse von Histogrammen in der Regel **nicht** angepasst.
::: 

Excel versucht die Intervalle für ein Histogramm aus dem vorliegenden Wertebereichen automatisch zu ermitteln. Dazu werden zwischen dem minimalen und maximalen Werten gleichgrosse Intervalle *proportional* zur Anzahl der Werte gewählt. Das bedeutet, dass Excel grössere Intervalle wählt, wenn weniger Werte vorhanden sind. Das ist nicht immer gewünscht oder die Intervallgrenzen liegen ungeeignet.

Die Intervalle eines Histogramms lassen sich über die Formatierung kontrollieren. Dazu wird mit der Maus ein Balken angeklickt und anschliessend die Datenreihenoptionen ausgewählt. 

![Histgrammintervalle konfigurieren](figures/histogramm_konfigurieren.png){#fig-histogramm-konfigurieren}

Die Option `Intervalle` steht nach dem Erstellen des Histogramms auf `Auto`. Hier stehen die beiden Optionen `Invervallbreite` und `Anzahl der Intervalle` zur Auswahl. 

Mit `Intervallbreite` wird der **Abstand** zwischen zwei Intervallen angegeben (@fig-histo-breite). Die Intervallgrenzen werden durch den kleinsten und grössten Wert definiert. Wird beispielsweise die Intervallbreite mit 500 angegeben und der kleinste Wert ist 33, dann sind die Intervallgrenzen 33, 533, 1066 usw. Diese Grenzen sind nicht immer intuitiv, besonders wenn Histogramme zum Vergleich von Daten verwendet werden. Mit der Option `Unterlaufintervall` kann die erste Intervallgrenze festgelegt werden. Es bietet sich an, das Unterlaufintervall genauso breit zu machen, wie die Intervallbreite.

Mit `Anzahl der Intervalle` wird die Anzahl der Balken im Histogramm festgelegt (@fig-histo-anzahl). Excel berechent aus diesem Wert einen geeigneten Intervallabstand.

Die beiden Optionen `Überlaufintervall` und `Unterlaufintervall` ermöglichen es die Ober- bzw. Untergrenze der regulären Intervalle zu definieren. Die beiden Intervalle entsprechen dem ersten bzw. letzen Balken im Histogramm. Diese beiden Intervalle werden für die Intervallbreite **nicht** berücksichtigt, zählen aber zur Anzahl der Intervalle. Diese Intervalle können verwendet werden, wenn unterhalb der Grenze des Unterlaufintervalls bzw. oberhalb der Grenze des Überlaufintervalls vereinzelt "Ausreisser" mit grösseren Abständen als die Intervallbreite auftreten.

::: {#fig-histogramm-intervalle layout-ncol=2 layout-valign="bottom"}

![Intervallbreite](figures/histogramm_Intervall_breite.png){#fig-histo-breite}

![Intervallanzahl](figures/histogramm_intervall_anzahl.png){#fig-histo-anzahl}

Einstellungsmöglichkeiten für Histogrammintervalle
:::

::: {.callout-tip}
## Praxis
Für die erste Sichtung neuer Daten ist es leichter ein Histogramm über die Anzahl der Intervalle zu definieren. Wird anschliessend auf `Intervallbreite` gewechselt, zeigt Excel die verwendete Intervallbreite an. So lassen sich die Intervalle einfach feinjustieren.
:::

#### Histogramme für diskrete Daten

In der Datenreihenformatierung findet sich zusätzlich die Option `Nach Kategorie`, die keine weiteren Konfigurationsmöglichkeiten bietet. In diesem Fall akzeptiert Excel einen Vektor mit diskreten und einen mit numerischen Daten. Wird diese Option für die Intervalle gewählt, dann bilden die eindeutigen diskreten Werte Kategorien. Über diese Kategorien **summiert** Excel den numerischen Vektor, um die Höhe der Balken zu bestimmen. Das Ergebnis ist in den meisten Fällen kein Histogramm im eigentlichen Sinn, weil es eine Summe anstatt einer Anzahl anzeigt.

::: {.callout-important}
## Achtung

Die Option `Nach Kategorie` erfordert Zeichenketten, die nicht in Zahlen umgewandelt werden können. Zahlen oder Zeichenketten, die wie Zahlen aussehen, werden für diese Option nicht unterstützt. Um Zahlenwerte in eine "Kategorie" umzuwandeln, muss dem Zahlwert ein Buchstabe vorangestellt werden, welcher nicht in Zahlen vorkommen kann.  

Die folgende Operation führt eine solche Umwandlung beispielhaft durch. 

```
= "K " & Tabelle1[diskreteZahlen]
```
:::

Wird als numerischer Vektor der Einsvektor (@sec-chapter-vektor-operationen)verwendet, dann entspricht die Summe der einzelnen Kategorien der Anzahl der Werte in der Kategorie. Ein solcher Einsvektor wird mit der @lst-einsvektor-cat erzeugt.

```{#lst-einsvektor-cat lst-cap="Einsvektor für Kategorien aus einer Tabelle"}
= 1 * (Tabelle1[disktrekeWerte] == Tabelle1[diskreteWerte])
```

Auf diese Weise lässt sich in Excel ein Histogramm für diskrete Daten erstellen (@fig-histo-diskret). 

![Beispiel eines Histogramms diskreter Daten](figures/histogramm_nach_kategorie.png){#fig-histo-diskret}

Im Fall von *nominalskalierten Werten* ist es oft wünschenswert die Balken in der Reihenfolge der Häufigkeiten zu organisieren. Das ist mit der Histogrammvisualisierung von Excel **nicht** möglich. Für solche Visualisierungen muss auf ein reguläres Balkendiagramm zurückgegriffen werden und die Daten vor der Darstellung entsprechend aufbereitet werden. 

### Box-Plot

Boxplots oder *Kastendiagramme* dienen der Visualisierung von Verteilungen. Im Gegensatz zu den festen Intervallen von Histogrammen, mit denen Häufigkeiten bestimmt werden, wird für Boxplots von **festen Häufigkeiten** ausgegangen. Diese Darstellung erlaubt es, auch sehr unterschiedliche Verteilungen miteinander zu vergleichen. 

![Beispiel eines Boxplots](figures/boxplot.png){#fig-boxplot-ex}

Weil Boxplots auch für ordinalskalierte Wertebereiche erstellt werden können, sind sie ein flexibles Werkzeug zur Visualisierung von Verteilungen.

::: {.callout-note}
## Merke
Für Boxplots **dürfen** Werte **nicht** aggregiert werden.
:::

Werden einem Boxplot aggregierte Werte übergeben, dann bestimmt Excel die Intervallgrenze für die aggregierten Werte und nicht die ursprüngliche Verteilung. 

In der Regel wird eine ganze Arbeitsblattspalte ausgewählt, um alle relevanten Werte zu markieren. Anschliessend wird aus der Diagrammkategorie `Statistik` der Diagrammtyp `Kastendiagramm ausgewählt. `

Excel kann gruppierte Bloxplots erstellen. Dazu muss ein zweiter Vektor mit diskreten Werten angegeben werden. Excel gruppiert dann die Werte entlang des zweiten Vektors. 

![Beispiel eines gruppierten Boxplots](figures/boxplot-categ.png){#fig-boxplot-categ}

#### Boxplots optimieren

Wie auch bei Balkendiagrammen fügt Excel zusätzliche Werte auf der Y-Achse ein. Diese Werte sind nur für offene Wertebereiche zulässig. Für geschlossene Wertebereiche müssen diese zusätzlichen Werte entfernt werden. Dazu wird die Beschriftung der Y-Achse ausgewählt und in der Datenreihenformatierung unter Optionen angepasst (@fig-boxplot-konfig-y). Damit die Werte auch tatsächlich übernommen werden, muss die automatische Feststellung des Wertebereichs deaktiviert werden. 

![Wertebereich der Y-Achse beim Boxplot anpassen](figures/boxplot_yachse_anpassen.png){#fig-boxplot-konfig-y}

Die Breite der Box kann über die Datenformatierung der X-Achse festgelegt werden (@fig-boxplot-config-breite). Die Option `Abstandsbreite` gibt den Abstand der Box zur nächsten Box als Vielfaches der Boxbreite an. Der Abstand zum Diagrammrand ist die Hälfte des Abstands zur nächsten Box. Aus den Abständen berechnet Excel die Breite der Boxen.

- Ein Wert von `1.0` bedeutet, dass der Abstand genauso breit wie die Box ist. 
- Ein Wert von `0.5` bedeutet, dass der Abstand halbso breit wie die Box ist. Dadurch wird die Box breiter. 
- Ein Wert von `2.0` bedeutet, dass der Abstand doppelt so breit wie die Box ist. Dadurch wird die Box schmaler.

![Konfiguration der Breite eines Boxplots](figures/boxplot_breite_config.png){#fig-boxplot-config-breite}

::: {.callout-warning}
## Achtung
Werten mehrere Vektoren gleichzeitig als Boxplot dargestellt, werden die Boxen unmittelbar nebeneinander dargestellt. Diese Abstände können nicht konfiguriert werden (@fig-boxplot-multimulti)
::: 

![Gruppierter Boxplot mit mehreren Vektoren (Blau und Orange)](figures/boxplot-multi-multi.png){#fig-boxplot-multimulti}

### Punktdiagramm

Ein Punktdiagramm stellt zwei Vektoren mit *kontinuierlichen Daten* gegenüber. Ein Vektor wird der X-Achse zugewiesen, der andere der Y-Achse. Entsprechend besteht jede Datenreihe für ein Punktdiagramm **immer** aus zwei Vektoren.

![Beispiel eines Punktdiagramms mit einer Ausgleichsgeraden](figures/punkt-beispiel.png){#fig-bsp-punktdiagramm}

Werden mehr als zwei Vektoren für ein Punktdiagramm markiert, dann verwendet Excel standardmässig die äusserst linke Spalte *immer* für die Werte auf der X-Achse. Um dieses Verhalten zu ändern, müssen die Datenreihen unter `Daten auswählen` angepasst werden. 

::: {.callout-tip}
## Praxis
Sollen mehrere Gruppen von Wertepaaren in einem Punktdiagramm dargestellt werden, sollten die Gruppen dem Punktdiagramm schrittweise als separate Datenreihen hinzugefügt werden. 
:::

#### Ausgleichsgeraden

Ausgleichsgeraden heissen in Excel *Trendlinien*. Drei Arten von Trendlinien können direkt in ein Punktdiagramm eingebettet werden.

- Linear
- Lineare Prognose
- Gleitender Durchschnitt 

Von diesen drei Trendlinienarten ist nur `Linear` eine Ausgleichsgerade im eigentlichen Sinn. Die `Lineare Prognose` ist identisch mit der Ausgleichsgeraden und unterscheidet sich nur dadurch, dass die X-Achse einen etwas grösseren positiven Wertebereich erhält. 

Zusätzlich können die folgenden Ausgleichslinien konfiguriert werden. 

- Exponentiell
- Logarithmisch
- Polynomisch
- Potenz

::: {.callout-warning}
Exponentielle, logarithmische und Potenzierte Ausgleichslinien sind nur für geeignete Wertebereiche ($\mathbb{R}^+$) zulässig 
:::

Die Trendlinie `Gleitender Durchschnitt` setzt voraus, dass die Werte auf der X-Achse aufsteigend sortiert sind. Diese Trendlinie wird meist nur dann verwendet, wenn die Werte auf der X-Achse Zeitangaben sind.

Eine Ausgleichsgerade wird über den Menübalken `Diagrammentwurf` das Untermenu `Diagrammelement hinzufügen` unter `Trendlinien` die Option `Linear` gewählt.

![Einfügen einer Ausgleichsgeraden](figures/punktdiagramm_ausgleichsgerade_config.png){#fig-ausgleichsgerade}

Eine Ausgleichsgerade kann angepasst werden, indem die Linie angelickt wird und unter `Trendlinie formatieren` die Trendlinienoptionen verändert werden. In diesem Dialog können auch die weiteren Ausgleichslinien konfiguriert werden (@fig-trendkonfig).

![Konfigurationsmöglichkeiten für Ausgleichsgeraden](figures/punkt-trend-konfig.png){#fig-trendkonfig}

### Jitter-Diagramm

Excel stellt für diskrete Werte keine eigene Visualisierung für den Vektorenvergleich bereit. Eine direkte Anwendung des Punktdiagramms führt zum Problem, dass die Punkte für jedes Wertepaar genau übereinander liegen. So lassen sich die Verteilungen in der Visualisierung nicht ablesen. Um ein Jitter-Diagramm zu erzeugen, müssen die Werte vor der Visualisierung leicht angepasst werden, so dass die Punkte nicht exakt übereinander liegen. Für diese Anpassung müssen die Werte beider Vektoren als Zahlen vorliegen (s. @sec-chapter-kodieren-gruppieren). Weil die Werte diskret sind, kann der Bereich zwischen den Werten genutzt werden. Grundsätzlich steht der Bereich bis 0.5 Abstand vom jeweiligen Wert für das Jittering zur Verfügung. Weil dadurch aber die Punkte nebeneinanderliegender Werte nicht mehr korrekt zugeordnet werden können, sollte zwischen zwei Werten eine *Pufferzone* vorgesehen werden, in der keine Punkte vorkommen dürfen. Dadurch wird eine visuelle Grenze zwischen den Werten erzeugt. 

::: {.callout-warning}
## Wichtig

Bei Jitter-Diagrammen sollten zusätzlich angeführt werden, dass die Punkte von den tatsächlichen Werten abweichen. 
::: 

::: {.callout-tip}
## Praxis

Die Pufferzone sollte bei ganzzahligen Werten .4 breit sein, damit eine ausreichend grosse visuelle Grenze wahrgenommen werden kann. Daraus ergibt sich ein Bereich von ±0.3 um den tatsächlichen Wert für den Darstellungsbereich. 
::: 

Für ein Jitter-Diagramm müssen alle Werte zufällig vom tatsächlichen Wert ein klein wenig verschoben werden. Damit vermieden wird, dass zu viele Werte exakt übereinander dargestellt werden, wird also für jeden Wert in den Daten ein eigener Zufallswert bestimmt. Dieser Wert muss im Intervall zwischen -0.3 und 0.3 liegen (s. Praxis-Box).

Der zweite Parameter ist immer `2`, weil eine X- und eine Y-Achse vorliegt. Anschliessend werden diese Verschiebungen auf die tatsächlichen Werte addiert. Diese neuen Werte bilden die Grundlage für das Diagramm, dass wie oben beschrieben als Punktdiagramm erstellt wird. 

::: {#exm-werte-puffer-addieren}
## Pufferwerte addieren

Dieses Beispiel nimmt an, dass die beiden Vektoren an den Adressen A1 und B1 beginnen. 

Im ersten Schritt werden die Werte für den Darstellungsbereich um den ursprünglichen Wert erzeugt. 

```
= ZUFALLSMATRIX(zeilen(A1#); 2; -0.3; 0.3)
```

Im zweiten Schritt werden diese Verschiebungen auf die Werte addisert. 

``` excel
= A1#:B1# + D1#
```

Das Ergebnis ist ein Bereich, der visualisiert werden kann. 
:::

![Beispiel für ein Jitter-Diagramm](figures/jitterplot.png){#fig-jitterplot}

### Blasendiagramm

::: {.callout-note}
## Merke
Blasendiagramme sind Punktdiagramme mit drei dargestellten Merkmalen.
:::

Für Blasendiagramme gelten die gleichen Optionen und Konfigurationen, wie für Punktdiagramme. 

Weil drei Merkmale kodiert werden, müssen die Daten in drei Spalten vorliegen. Dabei wird die linke Spalte für die X-Achse verwendet. Die mittlere Spalte wird für die Y-Achse verwendet. Die rechte Spalte enthält die Werte für die Grösse der Punkte. Prinzipiell lassen sich die Werte nachträglich noch umorganisieren, oft ist es aber einfacher, die Spalten vorher anzuordnen.  

![Beispiel eines Blasendiagramms](figures/bubble_chart.png){#fig-bubble-chart}

Eine Datenreihe eines Blasendiagramms besteht aus drei Merkmalen.

![Konfiguration der Datenreihen eines Blasendiagramms (MacOS)](figures/bubble-chart-datenreihen.png){#fig-datenreihen-bubble-chart}

In Blasendiagrammen lassen sich die Grössenwerte auf zwei Arten abbilden:

1. Über den Durchmesser der Kreise.
2. Über die Fläche der Kreise.

Wird der Durchmesser gewählt, werden die Kreise für grössere Werte schneller grösser als bei der Einstellung, über die Fläche zu kodieren. Die Kodierung über den Durchmesser ist sinnvoll, wenn nur ein kleiner Wertebereich (3-5) mit dicht zusammenliegenden Werten dargestellt werden muss. In allen anderen Fällen sollte die Kodierung über die Fläche der Kreise erfolgen.

Die Blasengrösse wird konfiguriert, indem zuerst auf einen Kreis mit der Maus geklickt wird und anschliessend unter Datenreihen formatieren unter `Reihenoptionen` die Strategie für die Blasengrösse angepasst wird (@fig-bubblechart-config)

![Konfiguration der Blasengrösse](figures/bubble-config-size.png){#fig-bubblechart-config}

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

Eine Variante von Paralleldiagrammen sind sog. Netzdiagramme (bzw. Spider-Web-Diagramme).

::: {.callout-note}
## Merke
Netzdiagramme ordnen die Kategorien der X-Achse sternförmig an. 
::: 

In Excel finden sich Netzdiagramme unter der Kategorie `Wasserfalldiagramme`. Diese Diagramme werden oft zum Vergleich von Merkmalsprofilen verwendet, z.B. als Ergänzung einer Stärken- und Schwächen-Analyse (SWOT-Analyse) 

![Netzdiagramm mit den gleichen Daten wie @fig-parallel-plot](figures/spidereweb_diagramm.png){#fig-spiderweb-diagramm}

<!--
### Treemap-Diagramme
-->

## Mathematische Funktionen visualisieren

::: {.callout-note}
## Merke
Mathematische Funktionen werden immer über **Punktdiagramme** oder **Punkte mit interpolierten Linien** dargestellt.
::: 

Excel kann mathematische Funktionen nicht direkt visualisieren. Stattdessen müssen die Funktionen für einen gewünschten Wertebereich berechnet werden. Dazu werden Punkte auf der X-Achse ausgewählt und berechnet. Zwischen diesen Punkten berechnet Excel die Funktion nicht, sondern verbindet diese Punkte nur durch eine Linie. Diese Linie muss keine Gerade sein. Stattdessen versucht Excel eine Kurve so durch einen Punkt zu legen, sodass die Kurve keine Ecke hat. Die Folge dieses Verbinden von Punkten ist, dass je weniger Werte auf der X-Achse ausgewählt werden, desto ungenauer wird die Funktionsdarstellung.

Um eine mathematische Funktion mit Excel zu visualisieren, muss eine Wertetabelle erstellt werden. Diese Tabelle wird in den folgenden Schritten erstellt. 

1. Die Unter- und Obergrenze des Darstellungsbereichs auf der X-Achse werden festgelegt. 
2. Aus diesen Intervallgrenzen wird die Differenz gebildet, woraus sich die Länge des Intervalls ergibt.
3. Die Anzahl der Punkte in diesem Intervall festgelegt. 
4. Die Länge des Intervalls wird durch die Anzahl der Punkte geteilt. Daraus ergibt sich der Abstand der Punkte im Intervall. 
5. Es wird eine ***Sequenz*** mit einer Länge der Anzahl der Punkte plus Eins gebiltet. Der Startwert dieser Sequenz ist die Untergrenze des Darstellungsbereichs. Die Schrittweite entspricht dem Abstand der Punkte Abstand der Punkte.
6. Die mathematische Funktion wird als Formel in die Spalte rechts neben der Sequenz eingegeben. Die Werte der Sequenz werden als Argumente der mathematischen Funktion verwendet.

::: {.callout-note}
Die Sequenz für die Wertetabelle muss die Anzahl der Punkte *plus Eins* enthalten, damit sowohl die Untergrenze als auch die Obergrenze des Darstellungsbereichs als Argumente verwendet werden. 
:::

Sollen mehrere Funktionen über das gleiche Intervall dargestellt werden, dann wird der letzte Schritt für jede zusätzliche Funktion wiederholt werden. Das Intervall der *Funktionsargumente* bildet immer die erste Wertespalte. Anschliessend wird die gesamte Wertetabelle visualisiert. 

Diese Wertetabelle kann als Punktdiagramm dargestellt werden. Dazu wird die gesamte Wertetabelle markiert und als **Punkte mit interpolierten Linien** visualisiert.  

![Beispiel der Visualisierung der Funktionen $f(x) = 2x^2 -3$ und $g(x)=2x+4$ ](figures/funktionen_visualisieren.png){#fig-funktionen-visualisieren}