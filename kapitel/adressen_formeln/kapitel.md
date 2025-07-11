---
# bibliography: references.bib

abstract: ""

execute: 
  echo: false
---

# Adressen und Formeln {#sec-chapter-adressen-formeln}

## Formeln

Excel-Arbeitsblätter sind in Zellen organisiert. Eine Zelle kann einen Wert oder einen Wert und eine *Formel* enthalten. Im letzteren Fall wird normalerweise der Wert angezeigt und erst beim Bearbeiten der Zelle wird die Formel sichtbar. 

::: {#def-excel-formel}
Eine **Formel** legt die Berechnung für den angezeigten Wert fest.
:::

In allen Tabellenkalkulationen werden Formeln immer mit einem Gleichheitszeichen eingeleitet (`=`). Dieses Gleicheheitszeichen wird auch *Formeldekorator* genannt, weil es nur anzeigt, dass nachfolgend eine Operation und kein Wert steht.

Formeln können Werte enthalten. In diesem Fall ist der angegebene Wert das Ergebnis der Formel.

::: {#exm-formel-mit-wert}
## Eine Formel mit einem Wert ohne Operator
```
= 1
```
::: 

Einzelne Werte machen wenig Sinn in einer Formel. Meist werden Werte durch Operatoren oder Funktionen verknüpft. 

Operatoren entsprechen den bekannten mathematischen Operatoren. So kann eine Tabellenkalkulation als Taschenrechner verwendet werden. 

::: {#exm-formel-mit-operator}
## Eine Formel die zwei Werte addiert
```
= 1 + 2
```
::: 

Mehr zu Operatoren findet sich unter @sec-operatoren. 



::: {#exm-formel-mit-funktion}
## Eine Formel die zwei Werte summiert
```
= SUMME(1; 2)
```
::: 



## Adressen {#sec-adressierung}


::: {#def-bezug}
Ein **Bezug** ist die Adresse eines Bereichs.
:::

In Excel gibt es zwei Arten von Bezügen:

- Arbeitsblattadressen
- Tabellenadressen

### Arbeitsblattadressen

::: {#def-arbeitsblattadresse}
Eine **Arbeitsblattadresse** enthält die Koordinaten eines Bereichs auf einem Arbeitsblatt.
:::

Arbeitsblattadressen besteht aus drei Teilen:

- Arbeitsblattname
- Bereichsbeginn
- Bereichsende

Der Bereichsbeginn verweist immer auf die linke obere Zelle des Bereichs. Der Bereichsende verweist immer auf die rechte untere Zelle des Bereichs. Eine Zelle wird immer durch den Spaltenindex (Buchstabe) und den Zeilenindex (Zahl) identifiziert. Werden die Koordinaten des Bereichsbeginns und des Bereichsendes bei der Eingabe vertauscht, dann wird der Bereich automatisch korrigiert. 

::: {#exm-bereichsadresse}
## Arbeitsblattadresse
```
Tabelle1!A1:C3
```
:::

@exm-bereichsadresse verweist auf den Bereich mit drei Spalten und drei Zeilen auf dem Arbeitsblatt `Tabelle1` beginnend mit der Zelle `A1` und endend mit der Zelle `C3`. 

Oft werden Arbeitsblattadressen nicht vollständig sondern gekürzt angegeben. Es gibt zwei Möglichkeiten, um Arbeitsblattadressen zu kürzen:

Werden Bereiche auf dem gleichen Arbeitsblatt adressiert, dann kann der Arbeitsblattname weggelassen werden. 

::: {#exm-bereichsadresse}
## Arbeitsblattadresse in Formeln auf dem Arbeitsblatt Tabelle1
```
A1:C3
```
:::

Wird ein Bereich mit nur einer Zelle adressiert, dann wird das Bereichsende weggelassen.

::: {#exm-bereichsadresse-eine-zelle-arbeitsblatt}
## Adresse einer Zelle auf dem gleichen Arbeitsblatt
```
B2
```
:::

::: {#exm-bereichsadresse-eine-zelle-anderes-arbeitsblatt}
## Adresse einer Zelle auf dem gleichen Arbeitsblatt
```
Tabelle2!B2
```
:::

Weil Arbeitsblattadressen von vielen interaktiven Excelkommandos verwendet werden, gibt es zwei Arten von Arbeitsblattadressen:

- Relative Adressen
- Absolute Adressen

Die Art der Adresse legt fest, wie ein interaktives Kommando mit einer Adresse umgehen soll. Die populärste interaktive Funktion ist das *Autoauffüllen*. Dabei wird eine Zelle mit einer Formel interaktiv auf einen Bereich von Zellen übertragen.

::: {.callout-warning}

Das Autoauffüllen ist eine einfache und beliebte Methode, um Formeln in Excel auf verschiedene Werte wiederholt anzuwenden. Bis 2019 war das Autoauffüllen die einzige Möglichkeit für die Datentransformation.

Die relative und absolute Adressierung ist eine wichtige Voraussetzung für das Autoauffüllen.  Leider ist das Autoauffüllen auch die Ursache für viele Fehler beim Umgang mit Excel.
:::

::: {.callout-tip}
## Praxis

In Excel365 kann das Autoauffüllen durch vektorisierte Funktionen fast vollständig ersetzt werden. Dadurch lassen sich viele Excel-typische Fehler vermeiden. Dadurch ist die Unterscheidung zwischen der relativen und absoluten Adressierung nicht mehr so wichtig.
:::
#### Relative Adressen

::: {#def-relative-adresse}
Eine **relative Adresse** ist eine Adresse eines Bereichs, die *veränderlich* ist.
:::

Relative Adressen werden in Excel von interaktiven Funktionen, wie dem *Autoauffüllen* verwendet, um die Adressen automatisch anzupassen. Eine relative Adresse wird relativ zur aktuellen Zelle angepasst. 

Ein Beispiel für eine relative Adresse ist `A1`. Diese Adresse bezeichnet die Zelle, die sich in der ersten Zeile und der ersten Spalte auf dem aktuellen Arbeitsblatt befindet. Wird die adressierte Zelle interaktiv nach unten aufgefüllt, dann wird die Adresse automatisch zu `A2`, `A3`, usw. angepasst. Wird die adressierte Zelle nach rechts aufgefüllt, dann wird die Adresse automatisch zu `B1`, `C1`, usw. angepasst.

#### Absolute Adressen

::: {#def-absolute-adresse}
Eine **absolute Adresse** ist eine Adresse eines Bereichs, die ganz oder teilweise *unveränderlich* ist.
:::

Der unveränderliche Teil einer Arbeitsblattadresse wird mit einem Dollarzeichen (`$`) markiert. Dieser Teil der Adresse wird bei der Anpassung der Adresse nicht verändert. So lassen sich Adressen angeben, die durch interaktive Kommandos nicht verändert werden.

Ein Beispiel für eine absolute Adresse ist `$A$1`. Diese Adresse bezeichnet die Zelle, die sich in der ersten Zeile und der ersten Spalte auf dem aktuellen Arbeitsblatt befindet. Wird die adressierte Zelle interaktiv horizontal oder vertikal aufgefüllt, dann wird die Adresse nicht angepasst.

Auf diese Weise lassen sich konstante Werte in Formeln einbauen.

### Tabellenadressen {#sec-tabellenadressen}

Spalten und einzelne Werte können über die Tabellenadressierung abgefragt werden [@microsoft_support_using_2023]. Das Ergebnis einer solchen Adressierung ist immer ein *dynamisches Feld* bzw. ein *dynamischer Bereich* (s. [Abschnitt @sec-dynamisches-feld]).

::: {.callout-note}
Jede Tabellenadresse kann auch als Arbeitsblattadresse dargestellt werden. Umgekehrt ist dies nicht möglich.
:::

Eine Tabellenadresse besteht aus zwei Teilen:

- Dem Tabellennamen
- Dem Spaltennamen

::: {#exm-tabellenadresse}
## Tabellenadresse
```
Tabelle1[Spalte1]
```
:::

Das @exm-tabellenadresse verweist auf die Spalte `Spalte1` der Tabelle `Tabelle1`. 

::: {.callout-important}
Die Namen von Tabellen sind *unabhängig* den Arbeitsblattnamen. In der gleichen Arbeitsmappe darf jeweils nur eine Tabelle und nur ein Arbeitsblatt mit dem gleichen Namen existieren. Es ist aber möglich, dass eine Tabelle und ein Arbeitsblatt den gleichen Namen haben. Das kann zu Verwirrungen führen, denn die Adresse `Tabelle1[Spalte1]` und die Adresse `Tabelle1!A:A` verweisen nicht zwingend auf die gleiche Spalte, denn eine Tabelle muss nicht auf einem Arbeitsblatt mit dem gleichen Namen stehen!
:::

Tabellenadressen können auch gekürzt werden: 

- Werden Spalten in der gleichen Tabelle angesprochen, dann kann der Tabellenname weggelassen werden.
- Soll die gesamte Tabelle angesprochen werden, dann kann der Spaltenname weggelassen werden.

#### Tabellenbereiche 

Um mehrere Spalten einer Tabelle anzusprechen kann der Bereichsoperator (`:`) wie bei der Arbeitsblattadressierung verwendet werden. Zusätzlich müssen die Spalten in ein weiteres Paar eckiger Klammern eingeschlossen werden. 

::: {#exm-tabellenbereich}
## Tabellenbereich

```
Tabelle1[[Spalte1]:[Spalte3]]
```
:::

@exm-tabellenbereich verweist auf alle Spalten zwischen `Spalte1` und `Spalte3` der Tabelle `Tabelle1`. 

::: {.callout-warning}
Werden zu einem späteren Zeitpunkt neue Spalten zwischen den adressierten Spalten hinzugefügt, dann werden die neuen Spalten automatisch in die Adressierung einbezogen.
:::

::: {.callout-important}
Es ist nicht möglich mehrere Spalten einer Tabellen *gleichzeitig* gezielt zu adressieren, wenn diese nicht unmittelbar nebeneinander stehen. Diese Adressierung ist unmöglich, weil Excel nur rechteckige Bereiche adressieren kann und solche Spalten keinen *rechteckigen Bereich* bilden.

Die Adressierung aus @exm-tabellenbereich kann nicht angepasst werden, so dass nur `Spalte1` und `Spalte3` adressiert werden, ausser die Spalten `Spalte1` und `Spalte3` stehen direkt nebeneinander.
:::

#### `Diese Zeile`-Operator

Einzelne Zeilen einer Tabelle können mit dem `Diese Zeile`-Operator adressiert werden. Der `Diese Zeile`-Operator wird mit dem Wert `[#Diese Zeile]` oder mit `@` angegeben. Dieser Operator reduziert die Tabelle auf eine einzelne Zeile und wählt anschliessend die gewünschte Spalte aus. `Diese Zeile` bedeutet für Excel die aktuelle Zeile des Arbeitsblatts. 

> ::: {#exm-diese-zeile}
> ## `Diese Zeile`-Operator für eine Tabellenzelle
> ```
> = Tabelle[@Spalte]
> ```
> oder 
> 
> ```
> = @Tabelle[Spalte]
> ```
> :::

Der Operator ist speziell für die Verwendung in Formeln in Tabellenzellen gedacht. Obwohl der Operator in allen Formeln eingesetzt werden kann, sollte der Einsatz auf Formeln beschränkt werden, die sich in einer Tabelle befinden.

::: {.callout-warning}
Der `Diese Zeile`-Operator kann nicht auf Tabellen angewendet werden, um eine ganze Zeile zu adressieren. Es darf immer nur eine einzelne Zelle adressiert werden. Die Adressierung `@Tabelle` ist also ungültig.
::: 

::: {.callout-warning}
Der `Diese Zeile`-Operator ist immer relativ zum Arbeitsblatt und nicht relativ zur aktuellen Tabelle. Es muss nur der Zeilenindex gleich sein, die Zielzelle kann sich auf einem anderen Arbeitsblatt befinden.
:::

Wird der `Diese Zeile`-Operator in Tabellen unterschiedlicher Länge verwendet, dann können zwei Fälle eintreten: 

1. Ist die adressierte Tabelle kürzer als die adressierende Tabelle, dann wird für die Zeilen, die keine Entsprechung in der adressierten Tabelle haben, der Fehler `#WERT!` zurückgegeben.
2. Ist die adressierte Tabelle länger als die adressierende Tabelle, dann werden alle überzähligen Zeilen *ignoriert*.

::: {.callout-tip}
## Praxis
Der `Diese Zeile`-Operator kann nur auf eine einzelne Zelle in der gleichen Zeile auf einem Arbeitsblatts angewendet werden. Wegen dieser Einschränkung des `Diese Zeile`-Operators sollten alle Tabellen so gestaltet werden, dass sie in der ersten Zeile des Arbeitsblatts beginnen. Dadurch kann der `Diese Zeile`-Operator in allen Tabellen verwendet werden.
:::

#### Überschriften adressieren

Eine Excel Tabelle hat immer Spaltenüberschriften. Diese Überschriften können ebenfalls über die Tabellenadressierung adressiert werden. Dazu wird als Spaltenname der Wert `#Kopfzeilen` verwendet. 

::: {#exm-kopfzeilen}
## Kopfzeilen einer Tabelle adressieren

```
Tabelle1[#Kopfzeilen]
```
:::

Um gezielt Kopfzeilen zu adressieren, kann die Adressierung aus @exm-kopfzeilen mit der Adressierung aus @exm-tabellenbereich kombiniert werden (@exm-kopfzeilen-bereich).

::: {#exm-kopfzeilen-bereich}
## Kopfzeilen einer Tabelle adressieren

```
Tabelle1[[#Kopfzeilen];[Spalte1]:[Spalte3]]
``` 
:::

#### Absolute Adressierung in Tabellen

Ein Tabellenbereich ist immer absolut adressiert. Wird aber nur eine einzelne Spalte einer Tabelle adressiert, dann wird die Adresse relativ adressiert. Damit beim Autoauffüllen diese Adresse nicht verändert wird, muss die Adresse als Bereich angegeben werden.

::: {#exm-absoluter-tabellenbereich-eine-spalte}
## Absolute Tabellenadressierung von einer Spalte

```
Tabelle1[[Spalte1]:[Spalte1]]
```
:::

Wird eine Formel mit dieser Adresse interaktiv aufgefüllt, dann wird die Adresse nicht verändert.


--- 
### Adressgrundstruktur



---
### Adressen und Auto-ausfüllen


### Bereichsadressen 

Eine Bereichsadresse verweis

::: {.callout-note}
Aktuell unterstützen nur Excel und Numbers Bereichsadressen ohne Funktionsaufrufe.
:::

#### Zeilen- und Spaltenadressen



#### Bereinigte Bereiche

`A.:.A`

::: {.callout-note}
Aktuell kann nur Excel Bereiche bereingen.
:::

Die Punkadressierung ist eine Kurzform

### Dynamische Bereiche {#sec-dynamisches-feld}

::: {.callout-note}
Aktuell unterstützen nur Excel und Numbers dynamische Bereiche.
:::


Formeln können mehr als einen Wert verarbeiten und mehr als einen Ergebnis liefern. Solche Formeln müssen nur in die linke obere Ecke eines Bereichs eingetragen werden. Excel erkennt automatisch, dass die Formel auf einen Bereich angewendet werden soll und erzeugt die entsprechende Formel für alle Zellen des Bereichs. Das Ergebnis einer solchen Formel ist ein *dynamischer Bereich*.

::: {#def-vektorisieren}
**Vektorisieren** heisst das Erzeugen eines dynamischen Bereichs aus einem statischen Bereich.
:::

::: {#exm-vektorisieren}
## Vektorisieren eines statischen Bereichs

```
=A1:A10
```
:::

Im Gegensatz zu einem normalen Bereich, ist bei einem dynamischen Bereich nur die linke obere Zelle bekannt. Um trotzdem alle Zellen eines solchen Bereichs zu adressieren, wird die Gatter- (`#`) Notation verwendet.

Das @exm-vektorisieren erzeugt einen Bereich mit 10 Zellen. Die Formel wird in die linke obere Zelle des Bereichs eingetragen. Die Formel wird z.B. in die Zelle `B1` eingetragen. Anschliessend können die Werte im Bereich `B1:B10` über die Gatter-Notation adressiert werden: `B1#`.

Der Vorteil des Vektorisierens ist, dass der Bereich durch das Einfügen neuer Zeilen vergrössert werden kann, ohne dass die nachfolgenden vektorisierten Formeln angepasst werden müssen.

::: {.callout-tip}
## Praxis

Weil Tabellen automatisch vektorisiert werden, ist es einfacher Werte in einer Tabelle zu erfassen bzw. als Tabelle zu importieren (s. @sec-chapter-daten-importieren) und anschliessend über die Tabellenadressierung auf die Werte zu verweisen.
:::

::: {.callout-note}
## Merke
Tabellenadressierungen auf eine Spalte oder einen Spaltenberech sind immer Vektorisiert.
:::

> ::: {#exm-tabellen-zu-vektoren}
> ## Vektorisieren von Tabellenspalten
> 
> ```
> = Tabelle1[Spalte1]
> ```
> 
> Diese Formel vektorisiert die Spalte mit dem Namen `Spalte1` aus der Tabelle `Tabelle1`. Angenommen, dass diese Formel in Zelle `A1` des aktuellen Arbeitsblattes steht, dann kann anschliessend auf den Vektor über die Gatter-Notation zugegriffen werden: 
> 
> ```
> =A1#
> ```
> ::: 


### Tabellenadressen 

#### Interne Adressierung mit `@`

#### Adressierung von Kopfzeilen

