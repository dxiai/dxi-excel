---
# bibliography: references.bib


abstract: ""

execute: 
  echo: false
---

# Daten formen {#sec-chapter-daten-formen}

::: {.callout-warning}
## Work in Progress
:::

Speziell für die Datenvisualisierung, erfordert Excel das Umformen von Daten. Dabei kann es notwendig werden, die Daten von der Normalform in eine Breitform umzuformen. Auch für andere Operationen kann es sinnvoll sein, Daten eine definierte Form zu geben. Zu diesen Operationen gehören z.B. gruppierte Aggregationen.

## Die `PIVOTMIT()`-Funktion 

Seit 2024 enthält Excel die Funktion `PIVOTMIT()`. Diese Funktion erlaubt das Überführen von Daten in eine Kreuztabelle. Diese Funktion hat vier verpflichtende Parameter: 

1. `row_fields` (Zeilenwerte)
2. `col_fields` (Spaltenwerte)
3. `values` (Aggregationswerte)
4. `function` (Aggregationsfunktion)

Diese Funktion ähnelt der den klassischen Pivot-Tabellen stark: Die beiden ersten Parameter liefern Gruppierungswerte, über die eine Zusammenfassung erstellt werden soll. Mit dem Parameter `values` werden die Werte festgelegt, die zusammengefasst werden sollen. Der vierte Parameter legt die Aggregationsfunktion fest, dabei kann jede Aggregrationsfunktion verwendet werden. 

![Ergebnis der `PIVOTMIT()`-Funktion mit `MITTELWERT()` als Aggregator](figures/pivotmit_basis_ergebnis.png)

Die Standardausgabe generiert Zeilen- und Spaltensummen. Diese Summen sind für eine Breitform unhantlich und lassen sich durch die optionalen 6. und 8. Parameter unterdrücken, wenn diese Parameter auf den Wert 0 gesetzt werden. Die Zeilensummen werden durch den 6. Parameter und die Spaltensummen werden durch den 8. Parameter  beeinflusst.

![Ergebnis der `PIVOTMIT()`-Funktion ohne Zeilen- und Spaltensummen](figures/pivotmit_basis_ergebnis_ohne_summen.png)

### `PIVOTMIT()` und fehlende Werte

Tritt ein Zeilen-und-Spaltenwertepaar nicht auf, kann `PIVOTMIT()` keine Werte aggregieren. Anders als andere Excel-Funktionen werden solche fehlenden Werte nicht durch den Wert 0 ersetzt, sondern durch eine leere Zeichenkette. Dieses Verhalten lässt sich nicht anpassen, sondern muss durch eine zusätzliche Operation korrigiert werden. 

```
= LET(breitform; PIVOTMIT(
                    data_ab[Interesse]; 
                    data_ab[Bedeutung]; 
                    data_ab[Punkte]; 
                    MITTELWERT;; 
                    0;; 
                    0);
      WENN(breitform = ""; 0; breitform)
)
```

::: {.callout-important}
## Achtung

Der Wert 0 darf **nicht** eingesetzt werden, wenn eine Breitform erzeugt werden soll, weil sonst Werte erzeugt werden, die ursprünglich nicht vorhanden waren. 
::: 

### Eine Breitform mit `PIVOTMIT()` erzeugen.

Wird als Aggregatorfunktion die Funktion `SUMME()` verwendet und jedes Wertepaar, dass sich aus den ersten beiden Parametern ergibt, dann ist diese Aggregation mit der Identifitätsfunktion funktional gleich.

```
= PIVOTMIT(Zeilenindex; Spaltenindex; Werte; SUMME;; 0;; 0)
```

::: {.callout-important}
## Achtung

Die Funktion `PIVOTMIT()` erfordert eine *Aggregationsfunktion*. Diese Funktion stellt sicher, dass mehrfach vorkommende Wertepaare zu einem eindeutigen Ergebnis führen. Dieses Verhalten führt dazu, dass die `PIVOTMIT()`-Funktion **nicht** immer **umkehrbar** ist, sobald die vorkommenden Wertepaare nicht eindeutig sind.
:::

::: {.callout-note}
## Merke

Eine Langform kann nur in eine Breitform umgeformt werden, wenn alle Wertepaare der Indexvektoren **eindeutig** sind. Eine solche Langform liegt dann in ihrer **Normalform** *für die beiden Indexvektoren* vor.
:::

### Vektoren auf ihre Normalform prüfen

Zwei Indexvektoren liegen genau dann in ihrer Normalform vor, wenn alle Wertepaare (bzw. Tupel) eindeutig sind, d.h. genau einmal vorkommen. Damit eine Breitform der Daten für diese Indexvektoren erzeugt werden kann, muss gelegentlich geprüft werden, ob diese auch tatsächlich in ihrer Normalform vorliegen.

Gegeben seien die folgenden Daten im Bereich A1:C6: 

| Index 1 | Index 2 | Werte |
| :---: |:---: |:---: |
| a | e | 1 |
| b | f | 2 |
| c | g | 3 |
| d | e | 4 |
| a | e | 5 |

Die Indexvektoren liegen in `Index 1` und `Index 2`, also in `A2:A6` bzw. `B2:B6`. 

Dazu werden alle eindeutigen Wertepaare mit `EINDEUTIG()` erzeugt. In diesem Beispiel wird diese Operation in Zelle `D2` durchgeführt. 

```
= EINDEUTIG(A2:B6)
```

Der Bereich `D2#` enthält jetzt alle eindeutigen Wertepaare der Indexvektoren. 

Die Normalform ist also dann gegeben, wenn jedes eindeutige Wertepaar höchstens einmal auftritt. Das liesse sich mit der folgenden Formel überprüfen, die als Ergebnis `WAHR` hat, wenn die Indexvektoren in ihrer Normalform vorliegen. 

```
= 1 = MAX(NACHZEILE(
    D2#;
    LAMBDA(zeile; 
        ZEILEN(
            FILTER(
                A2:A6;
                (SPALTENWAHL(zeile;1)=A2:A6) * 
                (SPALTENWAHL(zeile;2)=B2:B6)
            )
        )
    )
))
```

Diese Prüfung ist recht komplex und lässt sich stark vereinfachen, wenn die Voraussetzungen für die Normalform berücksichtigt werden. Dazu wird die Eigenschaft der Normalform ausgenutzt: Weil eine Normalform erfordert, dass die Wertepaare der Indexvektoren höchstens einmal vorkommen dürfen, muss das Ergebnis der Funktion `EINDEUTIG()` die gleiche Länge haben, wie die ursprünglichen Vektoren. Weil beide Indexvektoren aus der Definition des Datenrahmens die gleiche Länge haben müssen, lässt sich die Normalform mit der folgenden Operation prüfen.

```
= ZEILEN(A2:A6) = ZEILEN(D2#)
```

Diese Prüfung lässt sich in eine Operation zusammenfassen.

```
= ZEILEN(A2:A6) = ZEILEN(EINDEUTIG(A2:B6))
```

Ergibt diese Operation `WAHR`, dann kann die Breitform ohne Informationsverlust erzeugt werden. 

### Breitform ohne Überschriften erhalten

Weil die Funktion `PIVOTMIT()` auch Zeilen- und Spaltenüberschriften erzeugt, lassen sich die einzelnen Vektoren nicht direkt mit `SPALTENWAHL()` extrahieren. Leider lassen sich die Spaltenüberschriften nicht unterbinden.

Damit die Überschriften nicht in den Daten vorliegen, müssen diese nach der Transformation entfernt werden: 

```
= LET(breitform; PIVOTMIT(
                    Zeilenindex; 
                    Spaltenindex; 
                    Werte; 
                    SUMME;; 
                    0;; 
                    0);
      zeilenwerte; ZEILEN(breitform) - 1;
      spaltenwerte; SPALTEN(breitform);
      wertezeilen; SEQUENZ(zeilenwerte; 1; 2);
      wertespalten; SEQUENZ(1;spaltenwerte; 1);
      INDEX(breitform; wertezeilen; wertespalten)
)
```

Um auch die Werte des Zeilenindex zu entfernen, muss die Spaltenanzahl ebenfalls verringert werden.

```
= LET(breitform; PIVOTMIT(
                    Zeilenindex; 
                    Spaltenindex; 
                    Werte; 
                    SUMME;; 
                    0;; 
                    0);
      zeilenwerte; ZEILEN(breitform) - 1;
      spaltenwerte; SPALTEN(breitform) - 1;
      wertezeilen; SEQUENZ(zeilenwerte; 1; 2);
      wertespalten; SEQUENZ(1; spaltenwerte; 2);
      INDEX(breitform; wertezeilen; wertespalten)
)
```

::: {.callout-important}
## Achtung

Intuitiv bietet sich die Funktion `BEREICH.VERSCHIEBEN()` ebenfalls an. Diese Funktion erfordert jedoch eine Zellbezug, so dass diese Funktion nicht in Operationen mit `LET()` und `LAMBDA()` eingesetzt werden kann.
:::

## Die `INDEX()`-Funktion

Die Funktion `PIVOTMIT()` hat keine unmittelbare Umkehrfunktion. Mithilfe der `INDEX()`-Funktion lässt sich eine Umkehrfunktion konstruieren. Diese Funktion wurde bereits im letzten Abschnitt zum entfernen der Werte der Indexvektoren eingesetzt.

Die `INDEX()`-Funktion ist eine sog. Referenzfunktion, mit der auf Werte mittels ihrer Position in einem Vektor oder einer Matrix zugegriffen werden kann. Die `INDEX()`-Funktion erwartet drei Parameter: 

1. Die zu referenzierende Matrix
2. einen gültigen Zeilenindex, und 
3. einen gültigen Spaltenindex.

Der Zeilen- und Spaltenindex sind Ganzzahlen, die sich auf die Position der Werte beziehen. Auf diese Weise lassen sich Werte aus einem Vektor oder einer Matrix extrahieren. 



### `INDEX()` mit Vektoren als Indexparameter

Die INDEX()-Funktion erlaubt Vektoren für den Zeilen- und Spaltenindex. Auf diese Weise lassen sich mehrere Werte auf einmal referenzieren. Liegen die Vektoren in gleicher Orientierung vor, dann bildet die Funktion Indexpaare. Die Operation `= INDEX(A1:C5; {1; 2; 4}, {1; 2; 2})` wählt beispielsweise nur die Werte an `A1`, `B2` und `B4` aus.

Liegen die Indizes in verschiedenen Orientierungen vor, dann bildet die `INDEX()`-Funktion eine Indexmatrix mit allen Permutationen der angegebenen Indizes. Die Werte werden dann als Matrix angeordnet. Z.B. die Operation `=INDEX(A1:D4; {1;2;4}; ZUZEILE({1;2;2}))` wählt die Werte an `A1`, `A2`, `A4`, `B1`, `B2`, `B4` sowie nocheinmal `B1`, `B2` und `B4` aus. Diese Dopplung entsteht durch die doppelte Angabe des Werts `2` im Spaltenindex. Auf den ersten Blick erscheint dieses Verhalten unpraktisch, im folgenden Abschnitt wird genau diese Eigenschaft ausgenutzt. 

Die Funktion INDEX() behält die Orientierung der Parametervektoren bei. Diese Eigenschaft lässt sich ausnutzen, um eine Verkettung mit `MTRANS()` zu vermeiden. Die Operation `=MTRANS(INDEX(A1:D4; {1;2;4}; ZUZEILE({1;2;2})))` ist mit der Operation `=INDEX(A1:D4; ZUZEILE({1;2;4}); {1;2;2})` funktional gleich. 

### Die Umkehrung von `PIVOTMIT()` konstruieren

Beim Umformen von der Breitform in die Langform müssen nicht nur die Werte als Vektor dargestellt werden, sondern auch die beiden Indexvektoren wiederhergestellt werden. Entsprechend reicht der naive Aufruf von `ZUSPALTE()` nicht. 

### `SPALTENWAHL()` und `ZEILENWAHL()`

Die beiden Funktionen `SPALTENWAHL()` und `ZEILENWAHL()`, sind Vereinfachungen der `INDEX()`-Funktion. 

Die Funktion `SPALTENWAHL()` wählt ganze Spalten aus. Beispielsweise wählt der Aufruf von `SPALTENWAHL(A1:D17; 2)` die zweite Spalte des Bereichs `A1:D17` aus. Man erhält dann die Werte im Bereich `B1:B17`. Diese Funktion entspricht der folgenden Operation mit `INDEX()`.

```
= INDEX(
    A1:D17;
    SEQUENZ(ZEILEN(A1:D17));
    2
)
```

Analog verhält sich die Funktion `ZEILENWAHL()`. Sie wählt die angegebene Zeile aus einem Bereich aus. Für den Bereich `A1:D17` wählt der Aufruf `ZEILENWAHL(A1:D17; 7)` die Werte im Bereich `A7:D7` aus. Dieser Aufruf entspricht der folgenden Opeation mit `INDEX()`.

```
= INDEX(
    A1:D17;
    7;
    SEQUENZ(1; SPALTEN(A1:D17))
)
```

Ähnlich wie die `INDEX()`-Funktion unterstützen beide Funktionen die Auswahl mehrerer Spalten bzw. Zeilen. Dazu muss entsprechend ein Vektor mit den gewünschten Zeilen- bzw. Spaltennummern übergeben werden.

::: {.callout-tip}
## Praxis

Die Funktionen `SPALTENWAHL()` und `ZEILENWAHL()` sind der Funktion `INDEX()` vorzuziehen, wenn nur Spalten oder Zeilen in einer Operation extrahiert werden müssen. Operationen, die `SPALTENWAHL()` und `ZEILENWAHL()` verketten, sollten jedoch vermieden werden. In solchen Fällen ist die Funktion `INDEX()` meist besser geeignet, weil dann die Funktionsverkettung entfällt. 
:::
