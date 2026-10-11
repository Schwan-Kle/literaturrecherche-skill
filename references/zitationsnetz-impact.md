# Zitationsnetz und Impactdiagramme

Lies diese Datei, bevor du ein Zitationsnetz ausgibst oder ein Diagramm zeichnest.

## Inhalt

- [Wozu](#wozu)
- [Daten beschaffen](#daten-beschaffen)
- [Auswertungen](#auswertungen)
- [Die vier Diagrammformen](#die-vier-diagrammformen)
- [Darstellung des Netzes als Text](#darstellung-des-netzes-als-text)
- [Ehrlichkeitsgrenzen](#ehrlichkeitsgrenzen)
- [Wann Netz und Diagramm entfallen](#wann-netz-und-diagramm-entfallen)

## Wozu

Eine Quellenliste sagt, *was* es gibt. Das Netz sagt, *wie es zusammenhängt* – welche Arbeiten die Knotenpunkte sind, welche Stränge nebeneinander laufen, woher die Literatur kommt. Für jemanden, der sich neu in ein Feld einarbeitet, ist das oft wertvoller als drei zusätzliche Treffer.

Ein Diagramm lohnt nur, wenn es eine Frage beantwortet, die der Text nicht knapper beantworten könnte. Bei zwei Arbeiten genügt ein Satz. Bei acht Arbeiten über dreißig Jahre zeigt eine Kurve mehr als jede Aufzählung.

## Daten beschaffen

Drei Abfragen, eng gehalten:

1. **Zitationsverlauf** – `get_work` für zwei bis sechs Schlüsselarbeiten. Der Datensatz enthält die Zitationen pro Jahr; daraus entsteht jede Zeitreihe.
2. **Netzkanten** – `list_citations` je Startwerk. Richtung rückwärts (zitierte Werke) bringt die Fundamente, vorwärts (zitierende Werke) die Rezeption. Eine Ebene reicht fast immer.
3. **Einordnung** – `group_works` für Perzentile (Anteil Top 1 % / Top 10 %) und Mengenverteilung über die Jahre.

Nicht mehr als sechs Startwerke, sonst wird das Netz unlesbar und die Antwort erstickt an Daten. Vor jeder Aussage prüfen, ob für ein Werk überhaupt Zitationsdaten vorliegen – fehlende Daten bedeuten **fehlende Erfassung, nicht fehlende Bedeutung**. Das gilt besonders für deutschsprachige Literatur und für Arbeiten ohne DOI, die im Netz gar nicht vorkommen können.

**Die Jahresreihe reicht nicht beliebig zurück.** Geprüft: Für eine Arbeit von 2008 mit 434 Zitationen enthielt die Jahresreihe nur 389 davon, erst ab 2012; eine Arbeit von 2000 mit 10 Zitationen hatte überhaupt nur einen Jahreswert. Zwei Folgen: Die Summe der Jahreswerte ist nicht die Gesamtzahl, und ein **altersbereinigter Vergleich über die Jahresreihe ist für Arbeiten von vor etwa 2012 unzulässig** – die ersten Jahre fehlen genau dort, wo sie gebraucht würden. Für solche Arbeiten nur die Gesamtzahl und den feldnormierten Index verwenden und das Fehlen der frühen Jahre unter dem Diagramm benennen.

## Auswertungen

Aus den Kanten direkt berechenbar, ohne weitere Abfragen:

| Frage | Vorgehen |
|---|---|
| Gemeinsame Fundamente mehrerer Arbeiten | rückwärts; Werke nehmen, die bei **allen** Startwerken auftauchen |
| Wer fasst das Feld zusammen (Übersichtsarbeiten) | vorwärts; Werke, die bei allen Startwerken zitieren |
| Arbeiten, die einer Schlüsselarbeit ähneln | rückwärts; nach Zahl gemeinsamer Referenzen sortieren |
| Klassiker des Feldes | nach Eingangsgrad sortieren – wie oft ein Werk zitiert wird |
| Ist das Thema aktiv oder abgeschlossen | Mengenverteilung über die Jahre aus der Sondierung |

Für eine normale Recherche sind die ersten beiden Zeilen die nützlichsten: gemeinsame Fundamente liefern die Standardwerke, gemeinsame Zitierende die aktuellen Übersichtsarbeiten.

## Die vier Diagrammformen

Wähle **eine**, nicht alle. Mehr als zwei Diagramme in einer Antwort erschlagen den Text.

**1. Zitationsverlauf (Linien- oder Balkendiagramm)**
Zitationen pro Jahr, eine Linie je Schlüsselarbeit. Beantwortet: Wird die Arbeit noch genutzt, oder war sie ein kurzes Aufflackern? Die nützlichste und am leichtesten zu lesende Form. Bei stark unterschiedlichen Größenordnungen eine logarithmische Achse erwägen und das kennzeichnen.

**2. Altersbereinigter Vergleich**
Zitationen gegen die Jahre seit Erscheinen, nicht gegen das Kalenderjahr. Macht eine Arbeit von 1998 mit einer von 2021 vergleichbar, was das Kalenderjahr nicht leistet. Immer die Form wählen, wenn Arbeiten verschiedener Jahrzehnte verglichen werden – sonst erzeugt das Diagramm einen Vorteil, der nur Alter ist.

**3. Netzgrafik**
Knoten als Arbeiten, Kanten als Zitationen, Knotengröße nach Zitationszahl. Nur sinnvoll bis etwa zwölf Knoten; darüber wird es ein Wollknäuel ohne Aussage. Bei größeren Mengen stattdessen auf die Knotenpunkte beschränken oder zu Strängen gruppieren.

**4. Einordnungsbalken**
Perzentilstellung der Schlüsselarbeiten im Feld. Beantwortet knapp: Ist das eine tragende Arbeit oder eine Randnotiz? Als schmaler Balken neben der Quellenliste gut lesbar.

Zum Zeichnen: Vor dem ersten Diagramm die vorhandene Darstellungsanleitung für Diagramme lesen, sofern eine verfügbar ist. Bei mehr als einem Diagramm oder wenn die Person das Ergebnis weiterverwenden will, eine eigene Seite dafür anlegen statt mehrere Bilder in die Antwort zu streuen. Deutsche Achsenbeschriftung, Jahreszahlen vierstellig, Datenstand und Quelle unter das Diagramm.

Jedes Diagramm braucht **einen Satz darunter, der die Aussage benennt**. Ein Diagramm, das sich selbst erklären soll, erklärt nichts.

## Darstellung des Netzes als Text

Kompakte Karte, keine Kantenliste.

```markdown
## Zitationsnetz

*Aus den Zitationsbeziehungen der Datenbank. Startwerke: Nr. [x], [y], [z]; [n] Kanten ausgewertet.
Zitationsabsicht nicht verfügbar – zustimmende und widersprechende Zitierungen sind nicht unterscheidbar.*

**Knotenpunkte**

- **[Kurzzitat]** – von [n] Arbeiten im Netz zitiert, [n] Zitationen gesamt. Referenzwerk für [Aspekt].
- **[Kurzzitat]** – [n] Zitationen, Schwerpunkt [Jahre]. [Rolle im Feld]

**Stränge**

1. **[Bezeichnung]** – [Kurzzitat] → [Kurzzitat] → [Kurzzitat]
   [ein Satz: was den Strang verbindet, wie er sich entwickelt hat]

**Nicht verbunden**

[Quellen ohne Kante zum übrigen Netz – meist die deutschsprachige graue Literatur, die ohne DOI
in den Zitationsdaten gar nicht vorkommen kann. Das ist keine Aussage über ihren Wert, sondern
eine Grenze des Verfahrens, und muss als solche benannt werden.]
```

Der Abschnitt „Nicht verbunden" ist wichtiger, als er aussieht. Er verhindert den Fehlschluss, eine nicht im Netz auftauchende Quelle sei unbedeutend – und macht sichtbar, dass die beiden Recherchespuren nebeneinander her laufen.

## Ehrlichkeitsgrenzen

- **Keine Zitationsabsicht.** Ohne einen Dienst, der sie liefert, ist jede Aussage über Zustimmung oder Widerspruch unzulässig. Der Abschnitt „Umstritten" entfällt dann – und sein Fehlen wird benannt, nicht verschwiegen.
- **Keine Zahlen ohne Datensatz.** „Vielzitiert" ohne Beleg ist eine erfundene Angabe wie jede andere.
- **Zitationszahlen sind kein Qualitätsmaß.** Sie messen Aufmerksamkeit, nicht Richtigkeit, und sind zwischen Fächern nicht vergleichbar. Ein angewandter Beitrag in einer deutschen Fachzeitschrift kann für ein Gutachten wertvoller sein als ein hundertfach zitierter Grundlagenartikel. Wo ein Diagramm das Gegenteil suggeriert, gehört der Hinweis darunter.
- **Ein konstruiertes Netz ist schlimmer als keines**, weil es Sicherheit vortäuscht. Lieber dünn und ehrlich.

## Wann Netz und Diagramm entfallen

- Kompakte Stufe.
- Weniger als fünf Quellen mit DOI.
- Keine zwei Startwerke mit Zitationsdaten.
- Die Frage ist mit einem Satz beantwortet.

Diagramme werden angeboten, nicht ungefragt erzeugt – es sei denn, die Person hat ausdrücklich danach gefragt.
