---
execute: 
  echo: false
---

# Kodieren und Gruppieren {#sec-chapter-kodieren-gruppieren}


::: {.callout-warning}
## Work in Progress
:::

## Indizieren

Es werden drei Arten von Indizes unterschieden: 

1. Der **Primärindex**, mit dem ein einzelner Datensatz eindeutig *identifiziert* werden kann. 
2. **Fremdschlüssel** sind Sekundärindizes für *Querverweise* auf eine zweite Datenstruktur (eine sog. *Indextabelle* oder engl. *Lookup-Table*).
3. **Gruppenindizes** sind Sekundärindizes zur Identifikation von Datensätzen mit *gemeinsamen Eigenschaften*.

Weil ein Index Werte über einen Datensatz enthält, gehört ein Index zum jeweiligen Datensatz und wird über einen *Indexvektor* in einer Stichprobe abgebildet.

### Hashing eines Primärindex

In Excel muss zum Durchnummerieren die `SEQUENZ()`-Funktion verwendet werden. Das erreichen wir mit der folgenden Operation: `=SEQUENZ(ZEILEN(DatenBereich))`, wobei `DatenBereich` eine Excel-Adresse sein muss. Weil mit Excel keine leeren Datenrahmen existieren, führt diese Sequenz in Excel zu keinen Fehlern. Wegen dieser Eigenschaft muss ein entsprechender Bereich mindestens einen Umfang von einem Datensatz haben. 

::: {.callout-note}
Diese Eigenschaft gilt auch für Tabellen, die nur aus Überschriften bestehen. Damit die Formel zum Nummerieren eingegeben werden kann, muss mindestens ein Datensatz existeren, weil sonst keine entsprechend zugeordnete Zelle existiert. 
::: 



## Gruppieren

Das Gruppieren ist in Excel auf die folgenden Funktionen beschränkt: 

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
:::

::: {.callout-note}
## Merke
Wenn für eine Funktion eine WENN und eine WENNS-Variante existieren, dann sollte für *gruppierte Aggregationen* **immer** die WENNS-Variante verwendet werden. 
:::

Die WENNS-Varianten sind  für alle Aggregationen bezüglich ihrer Parameter konsistent, so dass die Syntax leichter zu merken ist. Die beiden (neuen) Funktionen `MINWENNS()` und `MAXWENNS()` veranschaulichen, diese Empfehlung, weil für diese Funktionen keine WENN-Variante existiert.  