---
execute: 
  echo: false
---

# Indizieren und Gruppieren {#sec-chapter-kodieren-gruppieren}

## Indizieren

Es werden drei Arten von Indizes unterschieden: 

1. Der **Primärindex**, mit dem ein einzelner Datensatz eindeutig *identifiziert* werden kann. 
2. **Fremdschlüssel** sind Sekundärindizes für *Querverweise* auf eine zweite Datenstruktur (eine sog. *Indextabelle* oder engl. *Lookup-Table*).
3. **Gruppenindizes** sind Sekundärindizes zur Identifikation von Datensätzen mit *gemeinsamen Eigenschaften*.

Weil ein Index Werte über einen Datensatz enthält, gehört ein Index zum jeweiligen Datensatz und wird über einen *Indexvektor* in einer Stichprobe abgebildet.

### Hashing eines Primärindex

In Excel muss zum Durchnummerieren die `SEQUENZ()`-Funktion verwendet werden. Das erreichen wir mit der folgenden Operation: `=SEQUENZ(ZEILEN(DatenBereich))`, wobei `DatenBereich` eine Excel-Adresse sein muss. Weil mit Excel keine leeren Tabellen existieren, führt diese Sequenz in Excel zu keinen Fehlern. Wegen dieser Eigenschaft muss ein entsprechender Bereich mindestens einen Umfang von einem Datensatz haben. 

::: {.callout-note}
Diese Eigenschaft gilt auch für Tabellen, die nur aus Überschriften bestehen. Damit die Formel zum Nummerieren eingegeben werden kann, muss mindestens ein Datensatz existeren, weil sonst keine Zelle für die Formel *in* der Tabelle existiert. 
::: 

### Hashing eines Sekundärindex

Ein Sekundärindex kennzeichnet mehrere Datensätze mit gleichen Eigenschaften. Die einfachste Hashing-Funktion für Sekundärindizes ist `WENNS()`. Diese Funktion stellt über die Bedingungen sicher, dass alle Hashes einen Datensatz die Merkmale eindeutig auswerten.

Soll ein Sekundärindex über Zahlen gebildet werden, werden die Ganzzahldivision und der Modulo-Operator häufig als Hashing-Funktion eingesetzt. Die Ganzzahldivision fasst aufeinanderfolgende Werte zu einem Wert zusammen. Der Modulo-Operator weist aufeinanderfolgenden Werte unterschiedlichen Werten zu. 

::: {.callout-tip}
## Praxis

Excels Funktion für die Ganzzahldivision ist eigentlich die Funktion `QUOTIENT()`. Diese Funktion kann leider nur mit einzelnen Werten und nicht mit Vektoren oder Matrizen verwendet werden. Deshalb ist die Funktion `QUOTIENT()` für die Praxis nur bedingt tauglich. Stattdessen muss die Ganzzahldivision in Excel wie folgt *simuliert* werden.

```excel
= GANZZAHL( A1:A9 / 3 )
```
:::

> ::: {#exm-tage-wochen}
> ## Tage und Wochen bestimmen
>
> Gegegeben ist eine Sequenz in `A1` Startend bei `1`. Diese Sequenz bildet die *Werktage* eines Projekts ab. Der erste Tag ist ein Montag. Feiertage werden nicht berücksichtigt. Aus dieser Sequenz sollen Wochentage und Wochen ermittelt werden. 
>
> Die Wochennummern im Projekt wird mithilfe der Ganzzahldivision ermittelt. 
>
> ```excel
> = GANZZAHL(A1# / 5)
> ```
>
> Die Wochentage werden mit dem Modulo-Operator bestimmt. 
>
> ```excel
> =  REST(A1#; 5)
> ```
> ::: 

### Indizieren mit einer Referenztabelle

Oft müssen Werte in andere Werte übersetzt werden, wobei die Kodierung keiner mathematischen Logik folgt. In diesem Fall werden sog. Referenz- oder Kodierungstabellen für das Indizieren verwendet. Sehr oft werden diese Tabellen unabhängig von der Datenerhebung erstellt.

Eine Referenztabelle hat mindestens zwei Spalten, wobei per Konvention die erste Spalte die möglichen Werte vor dem Indizieren. Diese Werte können in den Daten auftreten. Alle folgenden Spalten enthalten Kodierungen des ursprünglichen Werts.


::: {.callout-warning}
Enthält eine Referenztabelle mehr als eine Kodierung, dann müssen die Werte spaltenweise kodiert werden.
:::

> ::: {#exm-code-likert}
> ## Likert-Skala kodieren
>
> Eine Liker-Skala ist ein Messinstrument zur Meinungs- oder Empfindungserhebung. Eine Likert Skala wird in der Regel zwischen zwei Extremfeststellungen erfasst, die später als Zahlen kodiert ausgewertet werden. 
> 
> Solche Skalen erfordern eine Referenztabelle, weil die Ordnung der Werte sich nicht aus der alphabetischen Reihenfolge der Zeichenketten ergibt. Für die Auswertung müssen die Zeichenketten in Zahlen kodiert werden. Es ist üblich die Kodierung von Likert-Skalen in Referenztabellen zu dokumentieren. Die folgende Tabelle zeigt eine fünfstufige Liker-Skala mit den entsprechenden Zahlenwerten für die Auswertung.
> 
> | Wert | Zahl |
> | :---: | ---: |
> | Trifft gar nicht zu | -2 |
> | Trifft eher nicht zu | 1 |
> | Unentschieden | 0 |
> | Trifft eher zu | 1 |
> | Trifft voll und ganz zu | 2 |
>
> Die Kodierung erfolgt mit der Funktion  `XVERWEIS()`.
>
> ```excel
> = XVERWEIS(Tabelle1[Aussage_Likert]; 
>            KodierungLikert[Wert]; 
>            KodierungLikert[Zahl])
> ```
> :::

## Gruppieren

Das Gruppieren war in Excel auf die folgenden Funktionen beschränkt: 

- `ZÄHLENWENN()`
- `ZÄHLENWENNS()`
- `SUMMEWENN()`
- `SUMMEWENNS()`
- `MINWENNS()`
- `MAXWENNS()`
- `MITTELWERTWENN()`
- `MITTELWERTWENNS()`

::: {.callout-important}
Die Funktionen `ZÄHLENWENN()`, `ZÄHLENWENNS()`, `SUMMEWENN()` und `SUMMEWENNS()` wurden bis 2019 zum Erzeugen von bedingten Aggregationen verwendet. Mit der Einführung dynamischer Felder und der `FILTER()`-Funktion lassen sich bedingte Aggregationen einfacher und flexibler durch Funktionsverkettungen von FILTER() mit einer beliebigen Aggregationsfunktion erreichen. 

**Seit dieser Version hat sich die Bedeutung der Funktionen geändert.** Die Funktionen werden neu als Gruppierungsfunktionen verwendet. 

Mit der Einführung der `GRUPPIERENNACH()` Funktion wurden gruppierte Operation flexibler gestaltet (siehe dazu @sec-groupby). 
:::

::: {.callout-note}
## Merke
Wenn für eine Funktion eine WENN und eine WENNS-Variante existieren, dann sollte für *gruppierte Aggregationen* **immer** die WENNS-Variante verwendet werden. 
:::

::: {.callout-important}
## Achtung
Die beiden Funktionen `WENN()` und `WENNS()` sind **keine** Gruppierungsfunktionen, sondern Unterscheidungen. Trotz ähnlicher Namen, dürfen sie nicht mit den Gruppierungsfunktionen verwechselt werden. 
:::

Die WENNS-Varianten sind  für alle Aggregationen bezüglich ihrer Parameter konsistent, so dass die Syntax leichter zu merken ist. Die beiden Funktionen `MINWENNS()` und `MAXWENNS()` veranschaulichen diese Empfehlung, weil für diese Funktionen keine WENN-Variante existiert.  

Eine Gruppierungsoperation erfolgt in drei Schritten: 

1. Erzeugen der Gruppierungsindizes.
2. Ermitteln der Gruppierungen
3. Ausführen der Gruppierungsfunktion für alle Gruppierungen

@exm-gruppieren-zaehlen zeigt diese drei Schritte. Gegeben sind Werte zwischen 1 und 25, die in drei Bereiche organisiert werden sollen. Es soll die Anzahl der Werte in den einzelnen Bereichen ermittelt werden. Die Werte liegen in einer Tabellenstruktur vor. 

Der Gruppierungsindex ist ein Merkmal und sollte gemeinsam mit den Daten gespeichert und versioniert werden. Dieser Sekundärindex strukturiert die Daten in einer Tabelle oder einem Bereich. 

> ::: {#exm-gruppieren-zaehlen}
> ## Gruppiertes Zählen
> Die Reihenfolge der Schritte muss eingehalten werden!
> 
> **Schritt 1: Sekundärindex erstellen (in `A1`)**
> 
> ```excel
> = WENNS( Tabelle1[Werte] > 18; "gross";
>          Tabelle1[Werte] > 10; "mittel"; 
>          WAHR; "klein" )
> ```
> 
> Dieser Schritt kann entfallen, wenn ein Sekundärindex bereits vorhanden ist.
> 
> **Schritt 2: Gruppierungen ermitteln (in `C1`)**
> 
> ```excel
> = EINDEUTIG(A1#)
> ```
> 
> **Schritt 3: Zählen (in `D1`)**
> 
> ```excel
> = ZÄHLENWENNS( A1#; C1# )
> ```
> :::

Beim Zählen wird der Gruppierungsindex direkt verwendet. Die anderen Gruppierungsfunktionen haben einen zusätzlichen Parameter für den Vektor über den die Operation ausgeführt werden soll.

### Mehrere Sekundärindizes

::: {.callout-important}
Die WENNS-Varianten können mehrere Sekundärindizes verknüpfen. Dabei werden die vorkommenden *Permutationen* der Hash-Werte als Index verwendet. Alle Kriterienvektoren müssen dafür **gleich lang** sein und die Permutationen abbilden.
::: 

Um alle *vorkommenden* Permutationen mehrerer Sekundärindizes zu ermitteln, müssen die Vektoren einen Bereich bilden. Für diese Bereich ermittelt die Funktion `EINDEUTIG()` dann jede vorkommende Zeile. Dieser Trick funktioniert jedoch nur wenn alle Sekundärindizes nebeneinander stehen, was oft nicht der Fall ist. Die Funktion `HSTAPELN()` löst dieses Problem, weil sie mehrere Vektoren zu einem Bereich zusammenfügen kann. @exm-sekundaerindizes-verknüpfen-eindeutig zeigt die Vorgehensweise für drei Vektoren.

::: {#exm-sekundaerindizes-verknüpfen-eindeutig}
## Vorkommende Permutationen mehrerer Sekundärindizes ermitteln in `A1`
```excel
= LET(bereich; HSTAPELN(
                Tabelle1[Name]; 
                Tabelle1[Durchlauf]; 
                Tabelle1[Gruppe] );
      EINDEUTIG(bereich)
)
```
::: 

Diese Permutationstabelle kann nun mit den Gruppierungsfunktionen verwendet werden. @exm-gruppieren-mit-permutationen zeigt die Verwendeung der Gruppierungen aus @exm-sekundaerindizes-verknüpfen-eindeutig. 

::: {#exm-gruppieren-mit-permutationen}
## Gruppieren mit mehreren Indizes
```excel
= MITTELWERTWENNS(
    Tabelle1[Zeit]; 
    Tabelle1[Name];      SPALTENWAHL(A1#; 1);
    Tabelle1[Durchlauf]; SPALTENWAHL(A1#; 2); 
    Tabelle1[Gruppe];    SPALTENWAHL(A1#; 3)
)
```
::: 

## Die `GRUPPIERENNACH()`-Funktion {#sec-groupby}

Mit der Einführung der Funktion `GRUPPIERENNACH()` erlaubt Excel beliebige Gruppierungen, wodurch gruppierte Aggregationen weiter vereinfacht wurden. Die `GRUPPIERENNACH()`-Funktion fasst den Schritt der Eindeutigen Werte im Indexvektor und die nachfolgende gruppierte Aggregation zusammen. Das Ergebnis liefert immer die eindeutigen Werte des Gruppierungsindex zusammen mit den jeweiligen Aggregationen als Ergebnis zurück. 

::: {.callout-tip}
## Praxis
Die Syntax der Funktion `GRUPPIERENNACH()` ist deutlich einfacher als die älteren Gruppierungsfunktionen.
:::

Der erste Parameter die `GRUPPIERENNACH()`-Funktion ist immer der Indexvektor, der zweite Parameter ist immer der Wertevektor, über welchen aggregiert werden soll. Der dritte Parameter ist eine Aggregationsfunktion, die als *Funktionsreferenz* übergeben werden muss. Das bedeutet, dass hinter dem Funktionsnamen ***keine*** Klammern und auch keine Parameterliste stehen darf. 

Die `GRUPPIERENNACH()` Funktion fügt unter den gruppierten Ergebnissen normalerweise eine `Total`-Zeile für ein Gesamtergebnis ein. Diese zusätzliche Zeile kann durch den Wert `0` als fünften Parameter unterdrückt werden. Der vierte Parameter übernimmt die Überschiften in das Ergebnis, falls diese ebenfalls übergeben wurden. Dieser Parameter hat in vielen Fällen keine Bedeutung und wird deshalb meist ausgelassen. 

@tbl-gruppierungsfunktionen stellt die Syntax der älteren und neueren Gruppierungsfunktionen gegenüber. 

| Alte Syntax | Neue Syntax mit `GRUPPIERENNACH()` | 
| :--- | :--- | 
| `=ZÄHLENWENNS(daten[index]; EINDEUTIG(daten[index]))` | `GRUPPIERENNACH(daten[index]; daten[werte]; ZEILEN;; 0)` | 
| `=SUMMEWENNS(daten[werte]; daten[index]; EINDEUTIG(daten[index]))` | `GRUPPIERENNACH(daten[index]; daten[werte]; SUMME;; 0)` |
| `=MINWENNS(daten[werte]; daten[index]; EINDEUTIG(daten[index]))` | `GRUPPIERENNACH(daten[index]; daten[werte]; MIN;; 0)` |
| `=MAXWENNS(daten[werte]; daten[index]; EINDEUTIG(daten[index]))` | `GRUPPIERENNACH(daten[index]; daten[werte]; MAX;; 0)` |
| `=MITTELWERTWENNS(daten[werte]; daten[index]; EINDEUTIG(daten[index]))` | `GRUPPIERENNACH(daten[index]; daten[werte]; MITTELWERT;; 0)` |

: Gegenüberstellung alte und neue Gruppierungsstrategien {#tbl-gruppierungsfunktionen} 

::: {.callout-note}
## Merke

Damit eine Gruppierung durchgeführt werden kann, muss auch mit `GRUPPIERENNACH()` ein oder mehrere Indexvektoren erzeugt werden, falls noch keine Indexvektoren für die Daten existieren. 
::: 

Die Gruppierungsstrategie mit `GRUPPIERENNACH()` hat den Vorteil, dass auch nicht vorgegebene Aggregationen durchgeführt werden können. Das  @exm-gruppierter-median zeigt die gruppierte Aggregation des Medians, die ohne `GRUPPIERENNACH()` nur umständlich umgesetzt werden kann.

::: {#exm-gruppierter-median}
## Gruppierter Median 

``` excel
= GRUPPIERENNACH(data_ab[Angebot]; data_ab[Interesse]; MEDIAN;; 0)
```
:::

::: {.callout-note}
## Merke

Anders als andere Excel-Funktionen führen Fehlerwerte nicht zu einem einzelnen Fehlerwert im Ergebnis. Im Index-Vektor werden Fehlerwerte als eigene Gruppe behandelt. Erst innerhalb einer Gruppe führen Fehlerwerte im Wertevektor zu einem Fehler. 
::: 

### Gruppieren über mehrere Indizes

Um über mehrere Indizes gleichzeitig zu indizieren, müssen diese in den Daten einen Bereich bilden. Alle Indexvektoren müssen also unmittelbar nebeneinander liegen. Anschliessend wird dieser Bereich als Index der Funktion `GRUPPIERENNACH()` übergeben. In diesem Fall werden alle vorhandenen Permutationen der Indexvektoren als Index für die Gruppierungen verwendet. 

Das @exm-gruppierungen-mehrere-indizes zeigt die Anwendung über mehrere aufeinanderfolgende Indizes in einer Tabelle. 

::: {#exm-gruppierungen-mehrere-indizes}
## Gruppieren über mehrere Indizes

``` excel
= GRUPPIERENNACH(data_ab[[Interesse]:[Bedeutung]]; data_ab[Punkte]; SUMME;; 0)
```
::: 
