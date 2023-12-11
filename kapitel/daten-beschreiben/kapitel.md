---
abstract: ""

execute: 
  echo: false
---

# Daten beschreiben

::: {.callout-warning}
## Work in Progress
:::

## Universelle Kennwerte

Die universellen Kennwerte von Datenrahmen werden mit Excel auf die Gleicheweise bestimmt, wie die Dimensionen einer Matrix (s. @sec-chapter-matrix-operationen): 

Es werden die Zeilen und Spalten der Daten bestimmt. Beim Stichprobenumfang müssen ggf. ungültige Datensätzte gefiltert werden. Hierzu hilft meist ein Sekundärindex, mit dem die gültigen Datensätze markiert werden.

## Variablenumfänge

Die Variablenumfänge ist durch die Anzahl der gültigen Werte gegeben. Die Funktion `ANZAHL()` ignoriert sowohl die leeren Zellen als auch Fehlerwerte, Wahrheitswerte und Zeichenketten. Sie eignet sich damit zur Bestimmung des Variablenumfangs für Zahlenvektoren. 

Für alle anderen Vektoren bietet sich die Funktion `ANZAHL2()` an. Diese Funktion ignoriert jedoch keine Fehlerwerte. Deshalb müssen für Zeichenkettenvektoren fehlenden Werte, die mit `#NV` markiert wurden, gefiltert werden, bevor der Vektorumfang bestimmt wird. 

## Ungültige Werte entfernen

Wird diese Operation über mehrere Adressen verteilt, wandelt Excel die leeren Zellen in den Wert 0 um. Deshalb müssen zuerst alle leeren Zellen und anschliessend alle Fehlerwerte gefiltert werden.

::: {#exm-ungültige-werte-entfernen}
## Entfernen ungültiger Werte

```
= FILTER(
    Tabelle[Vektor]; 
    NICHT(ISTLEER(Tabelle[Vektor]) + ISTFEHLER(Tabelle[Vektor]))
)
```
:::

Erst über diese bereinigten Daten darf der Vektorumfang bestimmt werden. Weil durch das Entfernen der ungültigen Werte die Vektorlänge identisch mit dem Vektorumfang ist, kann der Vektorumfang auch mittels der Funktion `ZEILEN()` bzw. `SPALTEN()` bestimmt werden.

Ist der Datentyp eines Vektors festgelegt, dann lässt sich das Filtern ungültiger Werte stark vereinfachen. Dazu wird die Typenerkennung mit der entsprechenden `IST`-Funktion als Filter eingesetzt. 

::: {#exm-ungültige-werte-entfernen}
## Entfernen ungültiger Werte durch erzwingen des Datentyps Zeichenkette

```
= FILTER(
    Tabelle[Vektor]; 
    ISTTEXT(Tabelle[Vektor])
)
```
:::

Diese Strategie hat den Vorteil, dass auch alle Werte mit falschen Datentyp als ungültig erkannt und entfernt werden. 

::: {.callout-note}
## Merke

Ungültige Werte müssen auch für alle Lagemasse entfernt werden.
:::

## Lagemasse 

### Median

Der Median wird mit der Funktion `MEDIAN()` bestimmt. Dabei muss beachtet werden, dass diese Funktion ***ausschliesslich*** mit Rohdaten verwendet werden **muss**. Werden aggregierte Werte dieser Funktion übergeben, liefert diese Funktion den Median der aggregierten Werte und nicht den gesuchten Wert. 

Ordinalskalierte Daten können auch als Zeichenketten vorliegen. Diese Werte müssen zuerst in Zahlen kodiert werden, um den Median bestimmen zukönnen.

::: {#exm-median-bestimmen}
## Bestimmen des Medians
```
=MEDIAN(
    FILTER(
        Tabelle[Vektor]; 
        ISTZAHL(Tabelle[Vektor])
    )
)
```
:::

### Mittelwert

Der Mittelwert wird mit der Funktion `MITTELWERT()` bestimmt. Dieser Kennwert darf nur für metrisch-skalierte Daten bestimmt werden. Diese Daten liegen immer als Zahlen vor, weshalb diese Werte nicht kodiert werden müssen. 


::: {#exm-median-bestimmen}
## Bestimmen des Medians
```
=MEDIAN(
    FILTER(
        Tabelle[Vektor]; 
        ISTZAHL(Tabelle[Vektor])
    )
)
```
:::

## Streumasse

### Bandbreite

Die Bandbreite ergibt sich aus der Differenz zwischen dem kleinsten und dem grössten gemessenen Wert. Die Bandbreite wird nur als eigenständiger Wert angegeben, um ähnliche Bandbreiten in unterschiedlichen Wertebereichen anzuzeigen. Sonst wird nur das Minimum mit `MIN()` und das Maximum mit `MAX()` für den Vektor bestimmt. 

### Quartiele

Die Quartile werden mit der Funktion `QUARTILE.INKL()` bestimmt. Dazu wird der bereinigte Vektor als erster Parameter übergeben und anschliessend der das jeweilige Quartil. Das untere Quartil wird mit dem Wert `1` als zweiten Parameter berechnet und das obere Quartil mit dem Wert `3`.

Es ist möglich, die Minimalwert, den Maximalwert und den Median zusammen mit den beiden Quartilen mit der Funktion `QUARTILE.INKL()` zu bestimmen. Dazu wird als zweiter Parameter eine Sequenz von `0`-`4` übergeben.

Wie beim Median können die Werte für die Quartile mit Zahlenwerten berechnet werden. 

::: {#exm-alle-ordinalen-kennwerte}
## Bandbreite, Median und Quartile mit `QUARTILE.INKL()` bestimmen.
```
=QUARTILE.INKL(
    FILTER(
        Tabelle[Vektor]; 
        ISTZAHL(Tabelle[Vektor])
    );
    SEQUENZ(1; 5; 0)
)
```
:::

### Varianz und Standardabweichung

Die Varianz der gemessenen Werte eines Vektors werden mit der Funktion `VAR.S()` bestimmt. Die Standardabweichung der gemessenen Werte wird mit der Funktion `STABW.S()` bestimmt. Excel kennt für die echte Varianz und die echte Standardabweichung die Funktionen `VAR.P()` udn `STABW.P()`, diese werden für die Beschreibung gemessener Daten nicht verwendet. 

### Interquatilsabstand

Excel kennt keine Funktion für den Interquartilsabstand. Dieser muss aus den beiden Quartilen mit der Formel aus @exm-Interquartilsabstand berechnet werden.

::: {#exm-Interquartilsabstand}
```
= Quartil3 - Quartil1
```
:::

### Mittlere Absolute Abweichung (MAD)

Die mittlere absolute Abweichung muss in EXCEL ebenfalls händisch berechnet werden.

::: {#exm-mad-berechnen}
```
=LET(
    Werte; FILTER(
        Tabelle[Vektor]; 
        ISTZAHL(Tabelle[Vektor])
    ); 
    MEDIAN(
        ABS(
            Werte - MEDIAN(Werte)
        ) 
    )
)
```
:::
