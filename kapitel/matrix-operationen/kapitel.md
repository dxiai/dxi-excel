---
# bibliography: references.bib
abstract: ""

execute: 
  echo: false
---

# Matrix-Operationen {#sec-chapter-matrix-operationen}

::: {.callout-warning}
## Work in Progress
:::

::: {.callout-note}
## Merke
Alle Bereiche mit mehr als einer Zelle werden unabhängig von den vorliegenden Datentypen in Excel als *Matrix* bezeichnet. 
:::

Wie auch bei Vektoren übernimmt Excel keine Überprüfung der Bedinungen, ob tatsächlich eine Matrix in einem Bereich vorliegt.

## Matrizen erstellen

In Excel können Matrizen auf drei Arten erstellt werden.

1. Durch direkte Eingabe
2. Durch eine Operation mit einem Zeilen und einem Spaltenvektor.
3. Erzeugen durch eine Generatorfunktion

Bei der direkten Eingabe werden die Werte direkt in einen Bereich in Excel eingegeben. Am einfachsten wird dazu der Bereich der Matrix mit der Maus markiert und anschliessend werden die Werte eingegeben und mit der Eingabetaste oder der Tabulatortaste bestätigt. Excel bewegt die Markierung für die aktive Zelle im markierten Bereich automatisch an die nächste freie Position: Wird mit der Eingabetaste bestätigt, dann bewegt Excel die Eingabemarkierung *spaltensweise* durch den markierten Bereich. Wird die Eingabe mit der Tabulatortaste bestätigt, dann bewegt Excel die Eingabemarkierung *zeilenweise* durch den markierten Bereich.

Jede Transformation mit einem Spalten- und einem Zeilenvektor erzeugt in Excel eine Matrix. Dabei werden die Werte über Kreuz ausgewertet, so dass jede Position der Matrix einer paarweisen Operation entspricht. Die dimensionalität der so erzeugten Matrix ist immer die Zeilenanzahl des Spaltenvektors und die Spaltenanzahl des Zeilenvektors. 

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
2. Die Zeilennummer des gesuchten Werts
3. Die Spaltennummern der gesuchten Werts. 

Für die Zeilen- und die Spaltennummer können Vektoren angegeben werden, um mehrere Werte auf einmal zu referenzieren.

Um eine ganze Spalte- bzw. Zeile zu referezieren sollten die Funktionen `SPALTENWAHL()` bzw. `ZEILENWAHL()` eingesetzt werden.

## Vektorform

Die Vektorform einer Matrix wird in Excel durch die Funktionen `ZUSPALTE()` bzw. `ZUZEILE()` erzeugt. Die beiden Funktionen unterscheiden sich nur durch die Orientierung des Ergebnisvektors. Die zeilenweise Vektorform wird standardmässig von beiden Funktionen erzeugt. Um eine spaltenweise Vektorform zu erhalten, kann der dritte Parameter `scan_by_column` auf `WAHR` gesetzt werden. 

## Matrizen vergleichen

```
= UND(
    ZEILEN(Matrix1!A1#) = ZEILEN(Matrix2!A1#); 
    SPALTEN(Matrix1!A1#) = SPALTEN(Matrix2!A1#); 
    Matrix1!A1# = Matrix2!A1#
)
```

## Einheitsmatrix erzeugen

Die Funktion `MEINHEIT()` erzeugt immer eine quadratische Einheitsmatrix. 

::: {#exm-einheitsmatrix}
## Einheitsmatrix der Grösse 5
```
= MEINHEIT(5)
```
:::

## Matrizen Transponieren

Matrizen werden mit der Funktion `MTRANS()` transponiert. Dabei werden die Zeilen- und Spaltenindizes getauscht. 

::: {#exm-matrix-transponieren}
```
= MTRANS(Matrix1!A1#)
```
:::

## Paarweise Operationen

## Vektoraddition

## Skalarmultiplikation

## Matrixmultiplikation/Kreuzprodukt

`MMULT()`

### Inverse Matrix

`MINV()`

### Determinante

`MDET()`

### Zeilen- und Spaltensummen

### Dreieckmatrizen erzeugen

### Vorgänger- und Nachfolgersummen

## Co-Occurence Matrizen
