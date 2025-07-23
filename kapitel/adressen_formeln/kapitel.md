---
# bibliography: references.bib

abstract: |
    Dieses Kapitel stellt die wichtigsten Konzepte zur Arbeit mit Excel vor. Dazu gehören *Werte*, *Formeln* und *Adressen*. 

execute: 
  echo: false
---

# Formeln und Adressen {#sec-chapter-adressen-formeln}

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

Werden nur Werte in einer Formel verwendet, dann wird die Formel als *konstante Funktion* bezeichnet, weil die Formel unabhängig von ihrer Position immer den gleichen (konstanten) Wert liefert. Werte stehen meistens nicht allein, sondern  werden durch Operatoren oder Funktionen verknüpft. 

::: {.callout-tip}
## Praxis
Grundsätzlich sollte vermieden werden, Werte direkt in einer Formel zu verwenden. Stattdessen sollten Werte in Bereichen, Tabellen oder Arbeitsmappennamen definiert werden.
::: 

Operatoren entsprechen den bekannten mathematischen Operatoren. So kann eine Tabellenkalkulation als Taschenrechner verwendet werden. 

::: {#exm-formel-mit-operator}
## Eine Formel die zwei Werte addiert
```
= 1 + 2
```
::: 

Mehr zu Operatoren findet sich unter @sec-operatoren.

Funktionen sind die zweite Möglichkeit, um in Excel Berechnungen durchzuführen.

::: {#exm-formel-mit-funktion}
## Eine Formel die zwei Werte summiert
```
= SUMME(1; 2)
```
::: 

Excel verfügt über 450 Funktionen, die in Formeln eingesetzt werden können. Diese Funktionen sind über das Menuband `Formeln` erreichbar und in die folgenden Funktionsgruppen gegliedert: 

* Finanzmathematik
* Logisch
* Text
* Datum und Uhrzeit
* Nachschlagen und Verweisen
* Mathematik und Trigonometrie
* Statistik
* Technik
* Cube 
* Informationen

Daneben findet sich die Kategorie `Kompatibilität`. Diese Kategorie fasst veraltete Funktionen zusammen, die nicht mehr in neuen Arbeitsblättern verwendet werden sollten. Diese Funktionen dienen der Unterstützung alter Arbeitsmappen und unterstützen die moderne Arbeit mit Excel nicht und werden auch nicht mehr angepasst. Deshalb sollten diese Funktionen möglichst mit ihren aktualisierten Varianten ersetzt werden. 

Neben diesen veralteten Funktionen gibt es viele Funktionen, die bei der modernen Arbeit mit Excel nicht mehr eingesetzt werden und von geeigneteren Funktionen abgelöst wurden. Obwohl diese älteren Funktionen mit der modernen Arbeitsweise vereinbaren lassen, wird empfohlen, die entsprechende flexiblere Funktion zu verwednden. Eine Auswahl dieser Funktionen listet @tbl-alte-funktionen.

| alte Funktion | Ersatzfunktion | 
| :--- | :--- |
| ISTFEHL | ISTFEHLER | 
| VERWEIS | XVERWEIS | 
| SVERWEIS | XVERWEIS | 
| WVERWEIS | XVERWEIS |
| VERGLEICH | XVERGLEICH |  
| SVERGLEICH | XVERGLEICH | 
| WVERGLEICH | XVERGLEICH |
| WECHSELN | REGEXERSETZEN |

: Auswahl alte Funktionen und ihre flexibleren Nachfolger {#tbl-alte-funktionen}

Jede Excel-Funktion hat ein Ergebnis, das von einer anderen Funktion oder mit einem Operator verwendet werden kann. 

## Adressen {#sec-adressierung}

Um Werte und Berechnungen zu trennen, werden in Formeln die Adressen verwendet, an denen die gewünschten Werte stehen.

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

Ein Bereich ist im Excel Jargon ein rechteckiges Feld von Zellen. Der Bereichsbeginn verweist immer auf die linke obere Zelle des Bereichs. Der Bereichsende verweist immer auf die rechte untere Zelle des Bereichs. Eine Zelle wird immer durch den Spaltenindex (Buchstabe) und den Zeilenindex (Zahl) identifiziert. Werden die Koordinaten des Bereichsbeginns und des Bereichsendes bei der Eingabe vertauscht, dann wird der Bereich automatisch korrigiert.

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

Zusätzlich können ganze Zeilen oder ganze Spalten adressiert werden. In solchen Fällen wird jeweils die Start- und Endzeile bzw. -Spalte des Bereichs angegeben. Das @exm-bereichsadresse-mehrere-zeilen verweist auf den Bereich, der sich von der zweiten bis zur vierten Zeile auf dem Arbeitsblatt `Tabelle2` erstreckt.

::: {#exm-bereichsadresse-mehrere-zeilen}
## Adresse mehrerer Zeilen auf einem anderen Arbeitsblatt
```
Tabelle2!2:4
```
:::

Um eine einzelene Zeile zu adressieren, muss diese Zeile sowohl als Bereichsanfang als auch als Bereichsende angegebene werden. 

::: {#exm-bereichsadresse-eine-zeile}
## Adresse einer Zeile auf einem anderen Arbeitsblatt
```
Tabelle2!2:2
```
:::

Analog dazu werden ganze Spalten adressiert. 

::: {#exm-bereichsadresse-mehrere-Spalten}
## Adresse mehrerer Zeilen auf einem anderen Arbeitsblatt
```
Tabelle2!A:C
```
:::

::: {#exm-bereichsadresse-eine-Spalte}
## Adresse einer Spalte auf dem gleichen Arbeitsblatt
```
A:A
```
:::

### Adresserweiterungen

Weil Arbeitsblattadressen von vielen interaktiven Excelkommandos verwendet werden, gibt es zwei Arten von Arbeitsblattadressen:

- Relative Adressen
- Absolute Adressen

Die Art der Adresse legt fest, wie ein interaktives Kommando mit einer Adresse umgehen soll. Die populärste interaktive Funktionalität ist das *Autoauffüllen*. Dabei wird eine Zelle mit einer Formel interaktiv auf einen Bereich von Zellen übertragen.

::: {.callout-warning}
Das Autoauffüllen ist eine einfache und beliebte Methode, um Formeln in Excel auf verschiedene Werte wiederholt anzuwenden. Bis 2019 war das Autoauffüllen die einzige Möglichkeit für die Datentransformation.

Die relative und absolute Adressierung ist eine wichtige Voraussetzung für das Autoauffüllen.  Leider ist das Autoauffüllen auch die Ursache für viele Fehler beim Umgang mit Excel. Deshalb sollte das Autoauffüllen nur noch in Ausnahmefällen verwendet werden. 
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

### Dynamische Bereiche {#sec-dynamisches-feld}

::: {.callout-note}
Aktuell unterstützen nur Excel und Numbers dynamische Bereiche.
:::


Formeln können mehr als einen Wert verarbeiten und mehr als ein Ergebnis liefern. Solche Formeln müssen nur in die linke obere Ecke eines Zielbereichs eingetragen werden. Excel erkennt automatisch, dass die Formel auf einen Bereich angewendet werden soll und erzeugt die entsprechende Formel für alle Zellen des Bereichs. Das Ergebnis einer solchen Formel ist ein *dynamischer Bereich*.

::: {#def-vektorisieren}
**Vektorisieren** heisst das Erzeugen eines dynamischen Bereichs aus einem statischen Bereich.
:::

::: {#exm-vektorisieren}
## Vektorisieren eines statischen Bereichs

```
= A1:B10
```
:::

Im Gegensatz zu einem normalen Bereich, ist bei einem dynamischen Bereich nur die linke obere Zelle bekannt. Um trotzdem alle Zellen eines solchen Bereichs zu adressieren, wird die Gatter- (`#`) Notation verwendet.

Das @exm-vektorisieren erzeugt einen Bereich mit 10 Zellen. Die Formel wird in die linke obere Zelle des Bereichs eingetragen. Die Formel wird z.B. in die Zelle `B1` eingetragen. Anschliessend können die Werte im Bereich `B1:B10` über die Gatter-Notation adressiert werden: `B1#`.

Der Vorteil des Vektorisierens ist, dass der Bereich durch das Einfügen neuer Zeilen vergrössert werden kann, ohne dass die nachfolgenden vektorisierten Formeln angepasst werden müssen.

::: {#exm-adresse-dynbereich}
## Adresse eines dynamischen Bereichs
```
=D1#
```
:::

Manche Funtionen liefern immer dynamische Bereiche als Ergebnis zurück, selbst wenn dieser Bereich nur aus einer Zelle besteht. Dazu gehört z.B. die Funktion `FILTER`.

::: {.callout-important}
## Achtung

**Nicht alle Funktionen verhalten sich auf diese Weise.** Viele Funktionen haben nur dann dynamsiche Bereiche als Ergebnis, wenn mindestens eine Adresse verwendet wird, die einen Bereich mit mehr als einer Zelle umfasst. 

Deshalb ist es wichtig vorher zu prüfen, ob eine Formel tatsächlich einen dynamischen Bereich zum Ergebnis hat, bevor diese Adressierung verwendet werden kann.
::: 

#### Bereinigte Bereiche

In der Praxis werden häufig Werte adressiert, die in einem Bereich liegen, welcher sich über eine ganze Zeile oder eine ganze Spalte erstreckt wobei die eigentlichen Werte nur in einem kleinem Ausschnitt dieses Bereichs liegen und die restlichen Zellen in diesem Bereich sind leer. Excel erlaubt es alle leeren Zellen am Anfang und am Ende eines Bereichs bereits bei der Adressierung zu entfernen. Das Ergebnis ist ein dynamischer Bereich, welcher nur den verwertbare Werte umfasst.

::: {.callout-important}
Aktuell kann nur Excel Bereiche bereingen. Diese Funktion wird nicht von anderen Tabellenkalkulationen unterstützt. 
:::

Um einen Bereich zu bereinigen, wird ein Punkt auf der Seite des Bereichsoperators (`:`) angefügt, auf welcher leere Zellen entfernt werden sollen. Ein Punkt auf der linken Seite des Doppelpunkts bedeutet, dass die leeren Zeilen oder Spalten vor dem obersten-linken Wert entfernt werden. Ein Punkt auf der rechten Seite des Doppelpunkts bedeutet, dass alle leeren Zeilen oder Spalten nach dem untersten-rechten Wert entfernt werden. 

::: {#exm-bereinigterbereich}
## Beidseitig bereinigter Bereich 
```
A.:.B
```
:::

Die Punkadressierung ist eine Kurzform der Funktion `ABSCHNBEREICH()`

::: {.callout-note}
## Merke

Beim Bereinigen werden keine Zellen, Zeilen oder Spalten zwischen den Daten entfernt.
:::


### Tabellenadressen {#sec-tabellenadressen}

Beim Adressieren von Zellen auf Arbeitsblättern geht oft wichtige Information in den Formeln verloren. Damit diese Information erhalten bleibt, 

Spalten und einzelne Werte können über die Tabellenadressierung abgefragt werden [@microsoft_support_using_2023]. Das Ergebnis einer solchen Adressierung ist immer ein *dynamisches Feld* bzw. ein *dynamischer Bereich* (s. [Abschnitt @sec-dynamisches-feld]).

::: {.callout-note}
## Merke 

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

