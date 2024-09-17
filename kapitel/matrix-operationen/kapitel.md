---
# bibliography: references.bib
abstract: ""

execute: 
  echo: false
---

# Matrix-Operationen {#sec-chapter-matrix-operationen}

::: {.callout-note}
## Merke
Alle Bereiche mit mehr als einer Zelle werden unabhängig von den vorliegenden Datentypen in Excel als *Matrix* bezeichnet. 
:::

Wie auch bei Vektoren übernimmt Excel keine Überprüfung der Bedinungen, ob tatsächlich eine Matrix in einem Bereich vorliegt.

## Matrizen erstellen

In Excel können Matrizen auf drei Arten erstellt werden.

1. Durch direkte Eingabe
2. Durch das Überführen aus der Vektorform
3. Durch eine Operation mit einem Zeilen und einem Spaltenvektors
4. Erzeugen durch eine Generatorfunktion

Bei der direkten Eingabe werden die Werte direkt in einen Bereich in Excel eingegeben. Am einfachsten wird dazu der Bereich der Matrix mit der Maus markiert und anschliessend werden die Werte eingegeben und mit der Eingabetaste oder der Tabulatortaste bestätigt. Excel bewegt die Markierung für die aktive Zelle im markierten Bereich automatisch an die nächste freie Position: Wird mit der Eingabetaste bestätigt, dann bewegt Excel die Eingabemarkierung *spaltensweise* durch den markierten Bereich. Wird die Eingabe mit der Tabulatortaste bestätigt, dann bewegt Excel die Eingabemarkierung *zeilenweise* durch den markierten Bereich.

Liegt eine *Vektorform* einer Matrix vor, dann kann sie mit den Funktionen `ZEILENUMBRUCH()` oder `SPALTENUMBRUCH()` in eine Matrix mit einer festen Spalten- bzw. Zeilenzahl erzeugt werden. Neben dem Ausgangsvektor erwarten diese Funktionen die Länge einer Zeile bzw. einer Spalte. Damit ein Vektor in eine Matrix konvertiert werden kann, muss die Länge des Vektors durch die Zeilen- bzw. Spaltenlänge teilbar sein. Erfüllt ein Vektor dieses Kriterium nicht, dann füllt Excel die Positionen bis zur vollständigen Zeile bzw. Spalte mit dem Wert `#NV` auf.

::: {#exm-zeilenumbruch-matrix-gen}
## Matrix aus einer Sequenz erzeugen
```
=ZEILENUMBRUCH(SEQUENZ(12); 3)
```
:::

Jede Transformation mit einem Spalten- und einem Zeilenvektor erzeugt in Excel eine Matrix (s. [Abschnitt @sec-äusseres-produkt]). Dabei werden die Werte über Kreuz ausgewertet, so dass jede Position der Matrix einer paarweisen Operation entspricht. Die dimensionalität der so erzeugten Matrix ist immer die Zeilenanzahl des Spaltenvektors und die Spaltenanzahl des Zeilenvektors. 

::: {.callout-note}
## Merke

Operationen über einem Spalten- und einem Zeilenvektor entsprechen dem äusseren Produkt. Das äussere Produkt ist in Excel nur für Vektoren definiert!
:::

Mit den beiden Generatorfunktionen `SEQUENZ()` und `ZUFALLSMATRIX()` lassen sich Werte in matrizenartigen Bereichen erzeugen. Dazu wird die gewünschte Zeilen- und Spaltenanzahl als die ersten beiden Argumente übergeben. Die beiden Funktionen füllen anschliessend den angegebenen Bereich mit Werten.

## Matrixdimensionen

Die Dimensionen einer Matrix ergibt sich aus den Funktionen `ZEILEN()` und `SPALTEN()`. Beide Werte müssen getrennt bestimmt werden.

## Matrixwerte referenzieren

Die Werte einer Matrix werden mit der Funktion `INDEX()` referenziert. Diese Funktion hat drei Parameter. 

1. Die Matrix
2. Der Zeilenindex des gesuchten Werts
3. Der Spaltenindex der gesuchten Werts. 

Für den Zeilen- und den Spaltenindex können Vektoren angegeben werden, um mehrere Werte auf einmal zu referenzieren.

> ::: {#exm-index-with-vectors}
> ## Werte der Matrix Diagonalen referenzieren
>
> ```
> = INDEX(A1:D4; SEQUENZ(4); SEQUENZ(4))
> ```
>
> Weil diese Operation die gleiche Sequenz zwei Mal erzeugt, lässt sie sich mit `LET()` vereinfachen.
> 
> ```
> =LET(
>     diagonalenIndex; SEQUENZ(4);
>     INDEX(A1:D4; diagonalenIndex; diagonalenIndex)
> )
> ```
> :::

Um einzelne Spalten bzw. Zeilen zu referezieren sollten die Funktionen `SPALTENWAHL()` bzw. `ZEILENWAHL()` verwendet werden, weil sie nur einen Indexwert benötigen.

## Vektorform

Die Vektorform einer Matrix wird in Excel durch die Funktionen `ZUSPALTE()` bzw. `ZUZEILE()` erzeugt. Die beiden Funktionen unterscheiden sich nur durch die Orientierung des Ergebnisvektors. Die zeilenweise Vektorform wird standardmässig von beiden Funktionen erzeugt. Um eine spaltenweise Vektorform zu erhalten, kann der dritte Parameter `scan_by_column` auf `WAHR` gesetzt werden.

::: {.callout-tip}
## Praxis
Enthält eine Matrix fehlende Werte, die durch den Fehlerwert `#NV` markiert sind, lassen sich diese in der Vektorform direkt entfernen, indem der zweite Parameter auf `2` (Fehlerwerte ignorieren) bzw. `3` (Leere Zellen und Fehlerwerte ignorieren) gesetzt wird.

Dabei muss beachtet werden, sich die Matrix anschliessend nicht mehr aus dem Vektor reproduzieren lässt.
:::

## Matrizen vergleichen

Zwei Matrizen sind genau dann gleich, wenn sie gleiche Anzahl von Zeilen und Spalten sowie an jedem Index den gleichen Wert haben. Intuitiv bietet sich der paarweise Vergleich der Indizes an. Existieren nicht alle Indizes in der jeweils anderen Matrix, füllt Excel die fehlenden Indizes mit einem Fehler auf. Das führt dazu, dass die logische Verknüpfung in diesen Fällen einen Fehler zurückgibt. Deshalb ist es notwendig, dass zusätzlich gprüft wird, ob das Ergebnis dieser Operation einen Fehlerwert ergibt (@exm-matrizen-vergleichen).

::: {#exm-matrizen-vergleichen}
## Formel zum Vergleich von zwei Matrizen

```
= WENNFEHLER(
    UND(
        Matrix1!A1# = Matrix2!A1#
    );
    FALSCH
)
```
:::

Ein zweiter praktischer Vergleich ist das Überprüfen einer quadratischen Matrix. Dabei wir nur eine Matrix geprüft. Weil die Werte in diesem Fall keine Bedeutung haben ist die Formel sehr einfach (@exm-quadratische-matrix-prüfen).

::: {#exm-quadratische-matrix-prüfen}
## Überprüfen einer quadratischen Matrix

```
= ZEILEN(Matrix1!a1#) = SPALTEN(Matrix1!A1#);
```
:::

## Matrix Operationen

### Matrizen Transponieren

Matrizen werden mit der Funktion `MTRANS()` transponiert. Dabei werden die Zeilen- und Spaltenindizes getauscht. 

::: {#exm-matrix-transponieren}
## Eine Matrix transponieren
```
= MTRANS(Matrix1!A1#)
```
:::

### Skalar- und Vektoroperationen {#sec-vektoroperationen}

Alle Skalaroperationen werden von Excel wie erwartet ausgeführt: die Operation wird mit dem Skalar für jeden Wert der Matrix ausgeführt.

Bei Vektoroperationen ist die Orientierung des Vektors für das Verhalten der Operation bestimmend. 

- Spaltenvektoren werden spaltenweise mit der Matrix verknüpft. Dabei werden die Werte mit dem jeweils gleichen Zeilenindex zusammengefasst.
- Zeilenvektoren werden zeilenweise mit der Matrix verknüpft. Dabei werden die Werte mit dem jeweils gleichen Spaltenindex zusammengefasst.

> ::: {#exm-vektoroperationen}
> ## Orientierung bei der Verknüpfung eines Vektors und einer Matrix.
> 
> ```
> = SEQUENZ(4) + SEQUENZ(4; 4)
> ```
> 
> Obwohl die folgende Operation sehr ähnlich aussieht, hat sie ein anderes Ergebnis. 
> 
> ```
> = SEQUENZ(1; 4) + SEQUENZ(4; 4)
> ```
> :::

In beiden Fällen gilt, dass der Vektor genauso viele Zeilen bzw. Spalten haben muss, wie die verknüpfte Matrix, so dass für die Verknüpfungsoperation beide Operanden vorhanden sind. Fehlt einer der Operanden, dann ist die Verknüpfung für diesen Index *nicht definiert*, so dass Excel für diese Positionen einen `#NV`-Fehler erzeugt. 

::: {#def-partielle-verknüpfung}
Excel führt eine **unvollständige** bzw. **partielle Vektoroperation** durch, wenn nicht alle Indizes entweder im Vektor oder in der Matrix vorhanden sind. 
::: 

::: {#exm-unvollständige-vektoroperationen}
## Orientierung bei der Verknüpfung eines Vektors und einer Matrix.
 
```
= SEQUENZ(5) + SEQUENZ(4; 4)
```
:::

::: {.callout-warning}
## Achtung

Für Skalar- und Vektoroperationen sind nur Operatoren und Funktionen zulässig, die einen **Skalar** zum Ergebnis haben. Grundsätzlich sind alle Arithmetischen und Vergleichsoperatoren sowie der Textketten-Operator `&` für Skalar- und Vektoroperationen geeignet.

**Manche** Operationen erzeugen einen Fehler, andere geben bei überschüssigen Werten den jeweils ersten Index aus. 
:::

### Kreuzprodukt/Matrixprodukt

Das Kreuzprodukt (oder *innere Matrixprodukt*) ist die Entsprechung zur Multiplikation von zwei Skalaren. Diese Operation wird in Excel durch die Funktion `MMULT()` ausgeführt. Das Kreuzprodukt ist nicht transitiv. Deshalb ist die Reihenfolge der Operanden wichtig, denn für das Kreuzprodukt muss die Spaltenlänge der linken Matrix mit der Zeilenlänge der rechten Matrix übereinstimmen. Ist diese Bedinung nicht gegeben, dann erzeugt Excel einen `#WERT!`-Fehler.

Das Ergebnis des Kreuzprodukts ist eine Matrix mit der Zeilenlänge der linken und der Spaltenlänge der rechten Matrix.

Weil das Kreuzprodukt die Summe mit der Multiplikation verbindet, ergeben sich interessante Vereinfachungen, wenn die Werte einer Matrix nur die Werte `0` und `1` sind (s. @sec-zeilensummen und @sec-cumsum).

> ::: {#exm-summenprodukt}
> ## Die Funktion `SUMMENPRODUKT()` als Kreuzprodukt
> 
> Die Funktion `SUMMENPRODUKT()` zwischen zwei Vektoren lässt sich auch als Kreuzprodukt formulieren: 
> 
> ```
> = MMULT(SEQUENZ(1;4); SEQUENZ(4))
> ```
> 
> Das Ergebnis dieser Operation ist eine $1 \times 1$-Matrix (bzw. ein Skalar), weil die linke Matrix nur eine Zeile und die rechte Matrix nur eine Spalte hat. 
> :::

### Das äussere Produkt {#sec-äusseres-produkt}

In Excel ist das äussere Produkt nur für Vektoren (bzw. `1,n`- oder `m,1`-Matrizen) definiert.  Dabei müssen die Vektoren unterschiedliche Orientierungen haben. Das Ergebnis ist dann eine $m \times n$-Matrix, wobei $m$ die Länge des Spaltenvektors und $n$ die Länge des Zeilenvektors ist. 

::: {#exm-äusseres-vektorprodukt}
## Multiplikationstabelle für das kleine Einmaleins erstellen

```
= SEQUENZ(10) * SEQUENZ(1;10)
```
:::

Das äusser Produkt ist nicht auf die Multiplikation beschränkt, sondern für beliebige Operationen, wobei die Operation einen *Skalar* zum Ergebnis haben muss. Dieser Wert wird am Kreuzungsindex der Ergebnismatrix eingesetzt.

Diese Eigenschaft wird dazu ausgenutzt, um Matrizen mit speziellen Eigenschaften zu konstruieren ([Abschnitt @sec-triangle-matrix]).

::: {.callout-warning}
## Achtung

Werden beliebige Matrizen auf die gleiche Weise verknüpft, führt Excel eine paarweise Verknüpfung aus, die für alle nicht exisiterenden Index-Paare den Fehlerwert `#NV` erzeugt ([Abschnitt @sec-paarweise-operationen]). 
:::

Wird ein Vergleich als Operator für das äussere Produkt verwendet, dann ist das Ergebnis der Operation ein Wahrheitswert. Um diesen Wahrheitswert in eine Zahl umzuwandeln, muss eine arithmetische Operation nachgereiht werden. Hierzu ist die Multiplikation mit `1` oder die Addition mit `0` üblich.

::: {#exm-äusseres-produkt-vergleich}
## Äusseres Produkt zum Erzeugen einer Dreiecksmatrix
```
= 1 * (SEQUENZ(4) <= SEQUENZ(1;4))
```
:::

### Paarweise Operationen {#sec-paarweise-operationen}

Werden beliebige Matrizen miteinander verknüpft, dann führt Excel eine paarweise Verknüpfung aus. D.h. ein Operator oder eine Funktion wird paarweise für die Werte mit den gleichen Indizes ausgeführt. Dabei handelt es sich um eine Verallgemeinerung der Vektoroperation ([Abschnitt @sec-vektoroperationen]), wobei wie auch bei den Vektoroperationen die Operation nur ausgeführt werden kann, wenn für beide Operanden in der jeweiligen Matrix ein Wert existiert.

Bei paarweisen Operationen mit zwei Matrizen müssen beide Matrizen die gleichen Dimensionen haben. Ist diese Bedingung nicht gegeben, führt Excel eine *partielle Verknüpfung* (@def-partielle-verknüpfung) aus. 

::: {.callout-note}
## Merke

Zwischen den paarweisen Operationen und dem äusseren Produkt besteht kein Zusammenhang. Für Vektoren bzw. $1 \times n$-Matrizen führt Excel immer das äussere Produkt aus, für alle anderen Matrizen paarweise Operationen.
::: 

## Mathematische Hilfsoperationen

Neben den bereits vorgestellten Operationen verfügt Excel über drei weitere Funktionen für ***quadratische Matrizen***.

- `MEINHEIT()`
- `MINV()`
- `MDET()`

### Identitätsmatrix erzeugen

Die Funktion `MEINHEIT()` erzeugt eine Identitätsmatrix mit der angegebenen Zeilen-/Spaltenanzahl. Die Identitätsmatrix ist eine quadratische Diagonalmatrix mit den Wert `1` entlang der Diagonalen und dem Wert `0` an allen anderen Positionen.

::: {#exm-einheitsmatrix}
## Einheitsmatrix der Grösse 5
```
= MEINHEIT(5)
```
:::

### Determinante

Eine wichtige Kennzahl für quadratische Matrizen ist die Determinante. Sie wird mit der Funktion  `MDET()` berechnet.

::: {#exm-determinante-seqmatrix}
## Bestimmung der Determinante einer Matrix

```
=MDET(SPALTENUMBRUCH(SEQUENZ))
```
:::

### Inverse Matrix

Für viele Berechnungen ist die Inverse $A^{-1}$ einer quadratischen Matrix $A$ notwendig. Falls eine Matrix invertierbar ist, gibt die Funktion `MINV()` die Inverse zurück. Diese Funktion löst die Gleichung $A \times A^{-1} = I$ und bestimmt die Inverse Matrix $A^{-1}$.

::: {#exm-inverse-matrix}
## Inverse einer $4 \times 4$-Matrix

```
=MINV(
    ZEILENUMBRUCH(
        SEQUENZ(16);
        4
    )
)
```
:::

Ist die Matrix nicht invertierbar, dann gibt die Funktion den Fehler `#ZAHL!` zurück. In diesem Fall ist die Determinante gleich `0`.

::: {#exm-inverse-matrix}
## Nicht-invertiertbare $4 \times 4$-Matrix

```
=MINV(
    SPALTENUMBRUCH(
        SEQUENZ(16);
        4
    )
)
```
:::

Wird der Funktion keine quadratische Matrix übergeben, dann hat diese Funktion einen `#WERT!` zum Ergebnis.

## Rezepte

Die folgenden Rezepte Nutzen das Kreuzprodukt und das äussere Produkt. 

### Zeilen- und Spaltensummen {#sec-zeilensummen}

Es sollen die Summen für jede Zeile einer Matrix (oder Tabelle) berechnet werden und das Ergebnis soll ein Vektor sein. 

::: {.callout-note}
Für die Excel-Formeln wird angenommen, dass eine Matrix an der Adresse `M1` vektorisiert vorliegt. In der Praxis muss  den entsprechenden Parametern die korrekte Adresse der Matrix übergeben werden.
:::

#### Lösung 

```Excel
= MMULT(M1#; SEQUENZ(SPALTEN(M1#);1;1;0))
``` 
::: {.callout-tip}
## Praxis
Diese Operation ist bei der Arbeit mit Excel wichtig, weil diese Operation in Excel effizienter ist, als zeilenweise Aggregationen über vektorisierte oder nicht-verktorisierte Daten.
:::

#### Erklärung

Um Zeilensummen für eine Matrix zu erstellen, nutzen wir die Eigenschaften des Kreuzprodukts aus und multiplizieren eine Matrix mit dem Einsvektor. Das Ergebnis dieser Operation ist ein Vektor, der in jeder Zeile die Summe der Werte aus der entsprechenden Zeile der Matrix enthält. 

Das Kreuzprodukt ist nur für Matrizen definiert, wenn die erste (linke) Matrix $A$ gleich viele Spalten hat, wie die Zeilenanzahl der zweiten (rechten) Matrix $B$. Die Ergebnismatrix des Kreuzprodukts hat gleich viele Zeilen, wie die erste Matrix und gleich viele Spalten wie die zweite. Für jede Position $c_{ij}$ der Ergebnismatrix $C$ gilt dann die folgende Formel:

$$
c_{ij} = \sum^n_{k=1}{a_{ik}b_{kj}}
$$

Um die Zeilensummen einer Matrix $A$ zu erhalten, müssen wir die Matrix $B$ entsprechend konstruieren. 

1. Matrix $B$ darf nur eine Spalte haben, damit die Ergebnismatrix nur eine Spalte hat. 
2. Matrix $B$ darf die Werte in Matrix $A$ nicht verändern.
3. Matrix $B$ muss gleich viele Zeilen haben, wie Matrix $A$ Spalten hat.

Diese Anforderungen 1 und 2 werden durch den Einsvektor mit `n`-Zeilen erfüllt. Dabei nutzen wir aus, dass ein Spaltenvektor das gleiche wie eine Matrix mit einer Spalte ist. 

Die Anforderungen 3 können wir über die Spaltenzahl der Matrix bestimmen und erstellen dann einen Einsvektor mit entsprechender Zeilenanzahl.

Daraus ergibt sich für den Einsvektor $v_e$ und der Matrix an Adresse `M1` die Formel:

```
=SEQUENZ(SPALTEN(M1#); 1; 1; 0)
```

Weil der Einsvektor an jeder Position das neutrale Element der Multiplikation enthält, vereinfacht sich die Formel für das Kreuzprodukt stark: 

$$
c_{i1} = \sum^n_{k=1}{a_{ik}}
$$

Bei dieser Formel ist zu beachten, dass die 1 in $c_{i1}$ für die einzige Spalte des Einsvektors steht und i für die Zeilen in der Matrix A. Daraus wird deutlich, dass wir nun die Zeilensummen für die Matrix A erhalten.

Der Einsvektor muss bei dieser Operation als die rechte Matrix eingesetzt werden, sodass gilt:

$$
A \times v_e
$$

Als Excel-Formel wird das wie folgt ausgedrückt: 

```
=MMULT(M1#; SEQUENZ(SPALTEN(M1#); 1; 1; 0))
```

Aus dieser Lösung lässt sich auch die Spaltensumme ableiten: Für die Spaltensumme muss das neutrale Element der Multiplikation in die erste Matrix wandern. Dazu wird ein *Zeilenvektor* erstellt und mit diesem das Kreuzprodukt mit der Matrix gebildet. Weil in diesem Fall die Spaltensumme gebildet werden soll, kommen die Werte für die Spalten aus der rechten Matrix. Deshalb müssen wir das Kreuzprodukt wie folgt bilden:

$$
v_e \times B
$$

Daraus ergibt sich die folgende Excel-Formel:

```Excel
= MMULT(SEQUENZ(1; ZEILEN(M1#); 1; 0); M1#)
```

::: {.callout-tip}
## Praxis
Bei der Zeilen- und Spaltensumme handelt es sich um ein sogenanntes *Muster*, dass an verschiedenen Stellen verwendet werden kann. Ein *Muster* ist im Kern eine *Funktion*, die *parametrisiert* werden kann.
::: 

Wir können dieses Muster mit der Funktion `LET()` ([zum Exkurs über die `LET()`-Funktion](https://moodle.zhaw.ch/mod/page/view.php?id=544755)) so anpassen, dass wir den Bereich für unsere Matrix nur einmal anpassen müssen.

Daraus ergeben sich die folgenden Excel-Formeln:

* Zeilensumme: `= LET(Matrix; M1#; MMULT(Matrix; SEQUENZ(SPALTEN(Matrix); 1; 1; 0)))`
* Spaltensumme: `= LET(Matrix; M1#; MMULT(SEQUENZ(1; ZEILEN(Matrix); 1; 0); Matrix))`

### Dreieckmatrizen erzeugen {#sec-triangle-matrix}

Es soll eine quadratische Dreiecksmatrix mit $n$-Zeilen erzeugt werden. 

#### Lösung

Die Anzahl der Zeilen befindet sich in diesem Beispiel an Adresse `A1`.

Obere Dreiecksmatrix

```
= 1 * (SEQUENZ(A#) <= SEQUENZ(1; A1#))
```

Untere Dreiecksmatrix

```
= 1 * (SEQUENZ(A#) >= SEQUENZ(1; A1#))
```

#### Erklärung

Bei einer Dreiecksmatrix steht unterhalb bzw. oberhalb der Diagonalen der Wert 1 und sonst der Wert `0`. Gelegentlich (wie in der obigen Lösung) wird die Diagonale zu den mit `1` belegten Positionen hinzugezählt. 

Die Lösung nutzt aus, dass Excel bei unterschiedlich orientierten Vektoren das äussere Produkt bildet und so eine Matrix erzeugt. Die Basis für diese Operation bilden zwei Sequenzen, die über kreuz verglichen werden. 

Die Sequenzen können dabei als Nummerierungen der Matrixpositionen verstanden werden. Der Vergleich ergibt jeweils bis zur Diagonalen `FALSCH` und ab der Diagonalen `WAHR`, weil die Nummerierung der Positionen ab der Diagonalen *gleich* ist. 

Die Multiplikation mit `1` ist notwendig, damit die Matrix Zahlen und keine Wahrheitswerte enthält.

### Kumulative Summe {#sec-cumsum}

Es soll die kumulative Summe eines Vektors gebildet werden. 

#### Lösung

Für Spaltenvektoren: 

```
=LET(
    VLAENGE; ZEILEN(A1#); 
    MMULT(
        A1#; 
        1 * (SEQUENZ(VLAENGE) >= SEQUENZ(1; VLAENGE))
    )
)
```

Für Zeilenvektoren: 

```
=LET(
    HLAENGE; SPALTEN(A1#); 
    MMULT( 
        1 * (SEQUENZ(HLAENGE) <= SEQUENZ(1; HLAENGE));
        A1#
    )
)
```

#### Erklärung

Die kumulative Summe dreht die Logik der Zeilen- bzw. Spaltensumme um. In diesem Fall wird eine Matrix erzeugt, die für jede Position im Vektor anzeigt, welche Vektorwerte summiert werden sollen. Entsprechend darf diese Matrix nur die Werte `0` oder `1` enthalten, da die Werte im Ausgangsvektor nicht verändert werden dürfen.

Für die kumulative Summe müssen alle Werte bis und mit der aktuellen Position summiert werden. Eine Dreiecksmatrix leistet genau diesen Zweck: Für Spaltenvektoren zeigt die untere Dreickesmatrix zeilenweise an, welche Positionen für die kumulative Summe berücksichtigt werden müssen.

Weil die Diagonale der Dreiecksmatrix die gleiche Länge hat wie der Ausgangsvektor, ist sichergestellt, dass der Ergebnisvektor die gleiche Länge wie der Ausgangsvektor hat. 

Dieser Trick funktioniert nur, wenn die das neutrale Element der Multiplikation in der Dreiecksmatrix verwendet wird.

### Co-Occurence Matrizen {#sec-table-matrix}

Es sollen die gemeinsam auftretenden Werte in zwei **diskretskalierten Vektoren** gezählt werden und in einer *Kreuztabelle* gegenübergestellt werden.

#### Lösung

Für Spaltenvektoren:

```
=MMULT(
    1 * (EINDEUTIG(A1#) = MTRANS(A1#)); 
    1 * (MTRANS(EINDEUTIG(B1#)) = B1#)
)
```

#### Erklärung

Im ersten Schritt werden für jeden Vektor separat die Positionen der eindeutigen Werte in einer Matrix markiert. Die eindeutigen Werte sind die Werte vorkommenden Werte des Wertebereichs. Diese Werte werden mit der Funktion `EINDEUTIG()` bestimmt. Das Ergebnis des ersten Schritts ist eine Matrix, die nur die Werte `1` und `0` enthält. Der Wert `1` ist an der Position gesetzt, an der ein Wert des Wertebeichs im Ausgangsvektor gefunden wurde.Dazu dient die folgende Formel: 

```
= 1 * (EINDEUTIG(A1#) = MTRANS(A1#))
```

Diese Formel lässt sich auf beide Ausgangsvektoren anwenden. Dadurch ergeben zwei Matrizen mit gleich vielen Spalten, die nur die Werte `1` und `0` enthalten. 

Damit die gemeinsamen Vorkommnisse gezählt werden, wird das Kreuzprodukt verwendet. Dabei wird ausgenutzt, dass das Kreuzprodukt die Produkte der Zeilen- und Spaltenwerte summiert. Weil beide Matrizen nur die Werte `0` und `1` enthalten, entspricht diese Operation dem *Zählen durch Summieren*. 

Diese Operation zählt nur das gemeinsame Auftreten, weil in beiden Matrizen sichergestellt ist, dass in jeder Spalte genau eine `1` vorkommt, werden nur die Werte an den gleichen Positionen in den Ausgangsvektoren gezählt.

Damit dieser Trick funktioniert, muss eine der beiden Matrizen transponiert werden, bevor das Kreuzprodukt gebildet werden kann. Daraus ergibt sich die folgende Formel.

```
= MMULT(
    1 * (EINDEUTIG(A1#) = MTRANS(A1#));
    MTRANS(1 * (EINDEUTIG(B1#) = MTRANS(B1#)))
)
```

An dieser Formel ist wenig elegant, dass für den zweiten Parameter zwei Mal transponiert wird. Dieser Teilterm lässt sich dadurch vereinfachen, indem die zweite Transponierung bereits bei der Erzeugung der Matrix vorweggenommen wird, denn es gilt: 

```
MTRANS(1 * (EINDEUTIG(B1#) = MTRANS(B1#)))
```

*ist equivalent mit* 

```
1 * (MTRANS(EINDEUTIG(B1#)) = B1#)
```

Wird diese Vereinfachung in die obige Formel eingesetzt, dann ergibt sich die Formel der Lösung. 

Das Ergebnis ist eine sog. Kontingenztabelle, die die Häufigkeiten der gemeinsam auftretenden Werte anzeigt. 
