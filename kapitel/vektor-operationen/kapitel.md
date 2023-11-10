---
# bibliography: references.bib

abstract: ""

execute: 
  echo: false
---

# Vektoroperationen {#sec-chapter-vektor-operationen}

::: {.callout-warning}
## Work in Progress
:::

**Vektoren** sind zusammengesetzte Datenstrukturen, die Werte vom gleichen Datentyp darstellen. Vektoren werden in Excel entweder als *Bereiche* (z.B. `A1:A5`), als *Arrays* (z.B. `B1#`) oder als *Tabellenspalten* (z.B. `Tabelle1[[Spalte1]]`) adressiert. 

::: {.callout-warning}
## Wichtig
Excel erzwingt das Datentyp-Kriterium von Vektoren nicht, so dass Vektoren strenggenommen Listen sind.
:::

Falls der gleiche Datentyp in einem Vektor nicht vorausgesetzt werden kann, müssen die Daten für die Verarbeitung vorbereitet werden. Das kann beispielsweise dadurch geschehen, dass der gewünschte Datentyp (oder Wertebereich) durch **filtern** eingeschränkt wird. 

::: {.callout-note}
## Merke
Excel kennt keine abstrakten Vektoren, sondern unterscheidet Zeilen- und Spaltenvektoren.
:::

::: {#def-vektor-orientierung}
Als **Orientierung** eines Vektors wird die Anordnung der Werte bezeichnet.
:::

Für viele Vektoroperationen existiert deshalb eine Funktion für Spaltenvektoren und eine für Zeilenvektoren. 

Um Vektoren von der einen zur anderen Orientierung zu überführen, dient die Funktion `MTRANS()`. Soll eine *bestimmte* Orientierung für beliebige Vektoren erzwungen werden, dann kann die Funktion `ZUSPALTE()` zum Erzwingen eines Spaltenvektors oder die Funktion `ZUZEILE()` zum Erzwingen eines Zeilenvektors verwendet werden.

::: {#exm-erzwingen-spaltenvektor}
## Erzwingen eines Spaltenvektors
```
= ZUSPALTE(A1:D1)
```
::: 

## Vektorlänge bestimmen.

Jeder Vektor hat eine Länge, wobei diese Länge nicht zwingend der Anzahl der Werte entsprechen muss. Deshalb sollte die Länge eines Vektors mit Excel *nicht* mit der Funktion `ANZAHL()` bzw. `ANZAHL2()` bestimmt werden, sondern über die Funktionen `ZEILEN()` und `SPALTEN()`. Der Vorteil dieser beiden Funktionen ist, dass sie die Vektorlänge auch dann korrekt bestimmen, wenn einzelne Werte im Vektor nicht vorhanden sind.

Die Funktionen `ZEILEN()` und `SPALTEN()` geben die Anzahl der Zeilen respektive Spalten für den übergebenen Bereich zurück. Für einen Spaltenvektor gibt die Funktion `ZEILEN()` die Länge des Vektors zurück und die Funktion `SPALTEN()` hat den Wert `1`. Die Funktion `SPALTEN()` gibt die Vektorlänge von Zeilenvektoren zurück. Entsprechend hat in diesem Fall die Funktion `ZEILEN()` immer den Wert `1` als Ergebnis. 

::: {.callout-note}
## Merke
Die kleinste Excel Struktur ist die Zelle. Deshalb werden **keine** Vektoren der Länge `0` unterstützt! Es ist unmöglich, Vektoren der Länge `0` durch Funktionen zu erzeugen!
::: 

Aus den beiden Werten der Funktionen `ZEILEN()` und `SPALTEN()` kann die Orientierung eines Vektors mit der Operation `ZEILEN(vektor) - SPALTEN(vektor)` bestimmt werden. Ist das Ergebnis grösser `0` handelt es sich um einen Spaltenvektor und ist er kleiner `0` handelt es sich um einen Zeilenvektor. 

::: {.callout-tip}
## Praxis
Zur Feststellung der Orientierung muss in der Regel nur die erste Bedingung geprüft werden.
::: 

## Sequenzen

Sequenzen werden mithilfe der Generatorfunktion `SEQUENZ()` erzeugt. Die Funktion hat vier Parameter. Die ersten beiden Parameter der Funktion zeigen die Anzahl der Zeilen und Spalten an, über welche sich die Sequenz erstrecken soll. Der dritte Parameter erwartet den Startwert der Sequenz und mit dem letzten Parameter wird die Schrittweite der Sequenz angegeben. 

::: {#exm-sequenz-geradezahlen}
## Sequenz von geraden Zahlen erzeugen
```
=SEQUENZ(10; 1; 0; 2)
```
:::

Nur der erste Parameter der Funktion `SEQUENZ()` muss angegeben werden. In diesem Fall wird für alle anderen Parameter der Wert `1` angenommen. 

::: {#exm-einfache-sequenz}
## Sequenz der Länge 10 als Spaltenvektor erzeugen
```
=SEQUENZ(10)
```
:::

Zwei spezielle Sequenzen sind der Nullvektor und der Einsvektor. In beiden Vektoren wiederholt sich der Wert an jeder Position. Die zugehörige Sequenz hat also die Schrittweite `0`.

::: {#exm-einsvektor-via-sequenz}
## Einsvektor der Länge 10 erzeugen
```
=SEQUENZ(10; 1; 1; 0)
```
:::

Analog zum Einsvektor in @exm-einsvektor-via-sequeny wird der Nullvektor erzeugt, wobei der dritte Parameter den Wert `0` haben muss. 

## Konkatenation

Die Konkatenation verbindet zwei Vektoren zu einem neuen **Vektor**, wobei die Reihenfolge der Werte erhalten bleibt. Deshalb können in Excel nur Vektoren mit gleicher Orientierung konkateniert werden. 

Zum Konkatenieren von Spaltenvektoren dient die Funktion `VSTAPELN()` (für "vertikal stapeln"). Zum Konkatenieren von Zeilenvektoren dient die Funktion `HSTAPELN()` (für "horizontal stapeln"). 

Die beiden Funktionen `HSTAPELN()` und `VSTAPELN()` prüfen die Orientierung von Vektoren *nicht*! Werden zwei Vektoren mit unterschiedlicher Orientierung mit diesen Funktionen "gestapelt", entsteht eine Matrix, wobei die Vektoren in der Reihenfolge der Argumentübergabe als Zeile oder Spalte gezeigt werden. Die restlichen Positionen der Matrix werden mit dem Fehlerwert `#NV` belegt. 

## Transformationen

Das Ergebnis einer Transformationsoperation ist **immer** ein **Vektor** mit der **gleichen Länge** wie der ursprüngliche Vektor.

:::  {.callout-note}
## Merke
Beliebige Transformationen lassen sich mit `MAP()` umsetzen.
:::

### Skalartransformationen

Bei Transformationen mit einem Skalar, wird die Transformation für jeden Wert des Vektors und dem Skalar durchgeführt.

### Vektortransformationen

::: {.callout-note}
## Merke
Damit das Ergebnis einer Vektor-Transformation wieder ein Vektor ist, müssen beide Vektoren die *gleiche Orientierung* haben. D.h. es können nur Zeilenvektoren mit Zeilenvektoren bzw. Spaltenvektoren mit Spaltenvektoren transformiert werden
:::

### Bedingungen als Transformationen

Spezielle Transformationen sind Bedingungen. Dabei wird ein Vektor erzeugt, dessen Werte durch einen oder mehrere logische Ausdrücke bestimmt werden.



### Rezept: Beliebige Werte wiederholen

Excel fehlt eine Funktion zum Wiederholen von beliebigen Werten. Mithilfe von Sequenzen kann diese Funktionalität leicht nachgebaut werden. Dazu wird eine Sequenz der gewünschten Länge erzeugt und anschliessend für jeden dieser Werte der Wiederholungswert zurückgegeben (@exm-beliebige-werte-wiederholen). Der Wiederholungswert ist dabei ein Skalar, der für jeden Wert des erzeugten Sequenzvektors zurückgegeben wird.

:::{#exm-beliebige-werte-wiederholen}
## Zeichenkette `Daten` zehn Mal wiederholen
```
= WENN(SEQUENZ(10); "Daten")
```
:::

## Aggregationen

Beim Aggregieren werden die Werte eines Vektors durch eine Aggregationsoperation zusammengefasst.

Dass Ergebnis von Aggregationen sind Skalare **oder** Vektoren mit einer Länge von *maximal der Länge* des ursprünglichen Vektors. 

Häufig verwendete Funktionen zum Aggregieren sind: 

- `SUMME()`
- `PRODUKT()`
- `ANZAHL()`
- `MAX()`
- `MIN()`
- `MITTELWERT()`

::: {.callout-note}
## Merke
Beliebige Aggregationen lassen sich mit `REDUCE()` umsetzen.
:::

### Filtern als Aggregation

Das Filtern ist eine spezielle Aggregation, bei der das Ergebnis nur die Werte enthält, auf welche ein logischer Ausdruck zutrifft. Das Ergebnis einer Filter-Operation kann maximal die gleiche Länge haben, wie der zu filternde Vektor. In den meisten Fällen 

### Rezept: Laufende Summe

Eine laufende Summe oder *kumulative Summe* liefert für jeden Wert eines Vektors die Summe des Werts mit den Vorgängerwerten. **Diese Operation ist eine spezielle Aggregation.** Excel verfügt keine eigene Funktion für diese Aggregation. Stattdessen kann sie mit @lst-cumsum erzeugt werden.

```{#lst-cumsum lst-cap="Kumulative Summe"}
= SCAN(0; A2:A100; LAMBDA(accu; wert; accu + wert))
```

Um die laufende Summe herzuleiten, muss sich die Aggregation der normalen Summe als Reduktion mit `REDUCE()` veranschaulicht werden (s. @lst-reduce-sum)

```{#lst-reduce-sum lst-cap="Summen-Aggregation"}
= REDUCE(0; A2:A100; LAMBDA(accu; wert; accu + wert))
```

Beim Reduzieren mit `REDUCE()` muss immer ein Initialwert angegeben werden, dem der zu aggregierende Vektor folgt. Abschliessend wird die Aggregationsfunktion angegeben. Beim Reduzieren wird die Aggregationsfunktion für jeden Wert im Vektor nacheinander ausgeführt. Eine Aggregationsfunktion hat zwei Parameter: Der erste Parameter ist das Ergebnis der Aggregationsfunktion für die vorangegangenden Werte, wobei für den ersten Wert der Initialwert verwendet wird. Der zweite Parameter ist der Wert an einer Position im Vektor. 

In der Praxis ist die Funktion `SUMME()` dem Reduzieren mit `REDUCE()` immer vorzuziehen. Für die kumulative Summe fehlt aber eine entsprechende Funktion. Für diese Aggregation kann die Funktion `SCAN()` anstelle von `REDUCE()` verwendet werden. `SCAN()` erzeugt einen Vektor mit den Teilergebnissen einer Aggregationsfunktion. Dieser aggregierte Vektor hat die gleiche Länge wie der ursprüngliche Vektor.

## Zählen

Beim Zählen werden zählbare Einheiten von nicht-zählbaren Einheiten getrennt und die Anzahl der zählbaren Einheiten bestimmt. Die einfachste Form des Zählens ist das Bestimmen der der Länge eines Vektors. Dabei wird die Anzahl der Werte des Vektors *gezählt*.

Alle Zählen-Operationen bestehen entsprechend immer aus zwei Schritten:

- Einer Transformation zum Identifizieren der zählbaren Einheiten
- Einer Aggregation zum eigentlichen Zählen. 

Die Funktionen `ANZAHL()` zählt nur Werte vom Datentyp Zahl. Wahrheitswerte, Zeichenketten, Fehler und leere Zellen werden von dieser Funktion ignoriert. Die Funktion `ANZAHL2()` zählt die nicht leeren Zellen in einem Bereich unabhängig vom Datentyp. Diese Funktion zählt auch Fehlerwerte mit. 

### Zählen durch Summieren

Beim Zählen durch Summieren werden die zählbaren Elemente eines Vektors mithilfe eines logischen Ausdrucks **transformiert**. Daraus ergibt sich ein Vektor aus Wahrheitswerten. Dieser Vektor wird in einem zweiten Schritt mit der `SUMME()`-Funktion **aggregiert**. 

Auf diese Weise lassen sich gezielte Häufigkeiten bestimmen. 

::: {.callout-note}
## Merke
Vektoren, die nur die Werte `0` und `1` bzw. `FALSCH` und `WAHR` beinhalten, legen das Zählen durch Summieren nahe.
:::

::: {#exm-count-sum}
## Zählen durch Summieren
```
= SUMME(data_ab[Punkte] < 100)
```
:::

### Zählen durch Filtern

Beim Zählen durch Filtern werden die zählbaren Einheiten durch eine Filter-Aggregation isoliert. Die Anzahl der zählbaren Einheiten entspricht immer der Länge des gefilterten Vektors. 

::: {#exm-count-sum}
## Zählen durch Filtern
```
= ANZAHL2(FILTER(data_ab[Punkte] < 100))
```
:::

::: {.callout-note}
## Merke
Zählen durch Filtern sollte nur dann eingesetzt werden, wenn der Ergebnisvektor für weitere Operationen benötigt wird. Ist dies nicht der Fall, ist das Zählen durch Summieren effizienter.
:::

### Zählen durch Nummerieren

Beim Zählen durch Nummerieren werden die zu zählenden Werte eines Vektors nummeriert. Anschliessend wird der Maximal-Wert der Nummerierung bestimmt. Diese Technik nutzt aus, dass beim Nummerieren im Hintergrund eine Sequenz mit der Schrittweite `1` verwendet wird. Das letzte zählbare Element hat erhält so automatisch die Anzahl aller Element als Nummer.

::: {#exm-count-sum}
## Zählen durch Nummerieren
```
= MAX(SEQUENZ(ZEILEN(daten_ab[[Punkte]])))
```
:::

::: {.callout-note}
## Merke
Zählen durch Nummerieren sollte nur verwendet werden, wenn die Nummerierung entweder bereits vorliegt oder für weitere Operationen benötigt wird. 
:::
