# Suchstrategie

Vertiefung zu den Schritten 2 bis 7. Lies diese Datei, wenn die ersten Abfragen dünne oder zufällige Treffer liefern, wenn das Thema fachlich eng ist, oder bevor du auf der vollen Stufe kalibrierst.

## Inhalt

- [Woher diese Methodik stammt](#woher-diese-methodik-stammt)
- [Komponentenmodell](#komponentenmodell)
- [Schreibvarianten](#schreibvarianten)
- [Anfrageformen je Werkzeug](#anfrageformen-je-werkzeug)
- [Kalibrieren](#kalibrieren)
- [Recall-Test mit bekannten Treffern](#recall-test-mit-bekannten-treffern)
- [Kontrolliertes Vokabular](#kontrolliertes-vokabular)
- [Brückenabfrage bei fachübergreifenden Fragen](#brückenabfrage-bei-fachübergreifenden-fragen)
- [Plattform-gezielte Websuche](#plattform-gezielte-websuche)
- [Wenn nichts kommt](#wenn-nichts-kommt)
- [Metadaten vervollständigen](#metadaten-vervollständigen)

## Woher diese Methodik stammt

Das Vorgehen folgt der etablierten Methodik der systematischen Literaturrecherche, auf das Nötige eingekürzt. Wer tiefer gehen will oder eine Recherche für eine wissenschaftliche Arbeit methodisch begründen muss, findet dort die Langfassung:

- **RefHunter** – Manual und zehn Rechercheschritte, deutschsprachig: Rechercheprinzip, Suchkomponenten, Datenbankauswahl, Stichwörter, Schlagwörter, Suchstring, Ausführung, Dokumentation, ergänzende Suchwege. https://refhunter.org
- **AWMF-Manual** zur systematischen Recherche für Evidenzsynthesen und Leitlinien – der deutschsprachige Standard für begründungspflichtige Recherchen.
- **Fragerahmen**: PICO und seine Verwandten (PICOS, PECO, SPICE, SPIDER, PICo, CoCoPop) strukturieren die Frage in Komponenten. Für Umwelt- und Planungsfragen passt PECO (Population, Exposure, Comparator, Outcome) oder eine freie Variante aus Gegenstand, Maßnahme, Standort besser als das medizinische PICO.
- **Relativer Recall** – Prüfung einer Suchstrategie daran, ob sie bekannte relevante Arbeiten findet; der etablierte Ersatz für einen echten Goldstandard.
- **PRESS** (Peer Review of Electronic Search Strategies) – Prüfschema für fremde Suchstrategien: Übersetzung der Frage, Operatoren, Schlagwörter, Freitext, Syntax, Filter.
- **PRISMA-S** – was eine Suche dokumentieren muss, damit sie nachvollziehbar ist.

Diese Rahmen sind für systematische Reviews gebaut. Für eine Fachrecherche sind sie zu schwer; übernommen sind daher nur die vier Elemente mit dem größten Nutzen pro Aufwand: Komponentenbildung, Freitext plus Schlagwörter, Kalibrierung, Recall-Test.

## Komponentenmodell

Eine Komponente ist ein Begriff der Frage, der sich in Synonyme auflösen lässt. Typische Komponententypen:

- **Gegenstand** – was untersucht wird (Art, Lebensraum, Stoff, Personengruppe)
- **Maßnahme oder Einwirkung** – was getan wird oder einwirkt (Radwegebau, Sanierung, Belastung, Förderung)
- **Standort oder Kontext** – wo (Stadtraum, Region, Rechtsraum, Betriebsart)
- **Methode** – wie (Erhebung, Fallstudie, Experiment, Modellierung)
- **Wirkung oder Ergebnis** – was gemessen wird (Diversität, Ertrag, Kosten, Zustand)

### Regel 1: Aufzählbarkeit

Eine Komponente taugt nur als Suchbedingung, wenn ihre Synonyme vollständig aufzählbar sind. Begriffe wie „interdisziplinär", „innovativ", „nachhaltig", „zukunftsfähig" sind nicht aufzählbar – jeder Autor schreibt es anders, oder gar nicht. Solche Komponenten **streichen** und erst bei der Durchsicht der Treffer anwenden.

### Regel 2: Wirkungskomponenten nicht erzwingen

Gegenstand, Maßnahme und Standort stehen in Titeln und Abstracts, weil sie beschreiben, *worüber* eine Arbeit ist. Wirkungen und Ergebnisse stehen dort oft nicht – sie stehen im Ergebnisteil. Eine Wirkungskomponente als Pflichtbedingung schneidet deshalb genau die anwendungsnahen Arbeiten ab, die ihre Ergebnisse anders benennen.

In Testläufen mit zwei unterschiedlichen Themen senkte die erzwungene Wirkungskomponente die Trefferzahl jeweils um ein Vielfaches (grob Faktor 6 bis 22). Verloren gingen methodische Grundlagenarbeiten und fremdsprachige Arbeiten, obwohl sie den Gegenstand im Titel führten. **Die Regel gilt damit fachübergreifend.**

**Praxisregel: zwei, höchstens drei Pflichtkomponenten.** Alles Weitere ist Filter (Jahr, Typ, Sprache, Zeitschrift) oder Sortierkriterium, nicht Suchbedingung.

Die Outcome-Begriffe sind damit nicht wertlos: Sie taugen als **Sortier- und Durchsichtshilfe** und als optionale Zusatzvariante beim Kalibrieren – nur nicht als Pflichtbedingung.

## Schreibvarianten

Phrasensuche ist wörtlich. Ein eingeschobenes Wort bricht sie: **„electric bike“ findet „electric cargo bike“ nicht.** Auf diese Weise gehen relevante Arbeiten verloren.

Für jeden Mehrwortbegriff systematisch durchgehen:

| Variantentyp | Beispiel |
|---|---|
| Bindestrich, Leerzeichen, zusammengeschrieben | e-bike · e bike · ebike |
| eingeschobenes Wort | electric bike → electric cargo bike, electric folding bike |
| Singular und Plural | bike lane · bike lanes – meist von der Stammformreduktion abgedeckt |
| Wortfamilien | cycle · cycling · cyclist – ebenfalls meist durch Stammformreduktion |
| Abkürzung und Vollform | ÖPNV · öffentlicher Personennahverkehr |
| ältere und neuere Terminologie | Pedelec · E-Bike · elektrisch unterstütztes Fahrrad |
| regionale Varianten | pavement (UK) · sidewalk (US) · footpath |
| Adjektiv- und Substantivform | commute · commuting · commuter |

Bei Arten die lateinischen Namen ergänzen, wo Trivialnamen mehrdeutig sind.

Besser als lange Phrasen: **mehrere kurze Phrasen nebeneinander**. Statt `"electric cargo bike"` lieber `"electric cargo"` und `"cargo bike"` – das fängt die Einschübe mit ab.

### Platzhalter: in der Regel nicht nötig und oft falsch

Zwei Grenzen, beide an der Datenbank geprüft:

1. **Das Standardsuchfeld ist stammformreduziert.** Ein Platzhalter wird dort **abgewiesen**, mit dem Hinweis, dass der Text vor dem Platzhalter beim Indexieren entfernt wird und die Suche falsche Ergebnisse liefern würde. Platzhalter gehören nur in das unstemmte Feld (`…search.exact`).
2. **Innerhalb einer mehrwortigen Phrase** wird ein Platzhalter grundsätzlich abgewiesen (`"bike lane*"`).

Praktische Folge: **Platzhalter weglassen.** Die Stammformreduktion deckt Beugung und Wortfamilien ohnehin ab – `establish` findet establishment und established, `commute` findet commuting. Was sie *nicht* abdeckt, sind echte Synonyme, Bindestrichvarianten, Zusammenschreibung und andere Sprachen; die werden ausgeschrieben. Nur wenn eine Wortfamilie nachweislich nicht greift, auf das unstemmte Feld mit Platzhalter wechseln – und dann die Mengen gegen die stammformreduzierte Variante vergleichen, weil das Feld anders indexiert ist.

## Anfrageformen je Werkzeug

Jedes Werkzeug will eine andere Form. Dieselbe Formulierung überall einzusetzen verschenkt die Stärken.

**Datenbank, Stichwortsuche.** Boolesch, je Komponente eine Klammer mit `OR`, Komponenten mit `AND`:

```
(cycling OR bicycle OR "bike lane" OR "bike lanes" OR "cycle track" OR "cycling infrastructure")
AND (urban OR "urban area" OR "city centre" OR "city center" OR municipality OR "inner city")
```

Dazu **Filter** statt weiterer Komponenten: Jahr von/bis, Werktyp (`review` findet die Übersichtsarbeiten, mit denen eine Einarbeitung beginnt), Sprache, Zeitschrift, Thema, Land, Open-Access-Status, Mindestzitationen.

**Datenbank, semantische Suche.** Vollständige Forschungsfrage als Satz, Abkürzungen ausgeschrieben, mehrdeutige Begriffe mit Fachkontext. Findet Arbeiten, auf die Stichwörter nicht führen; dafür keine Mengenaussagen.

**Datenbank, exakte Suche.** Ohne Wortstammreduktion – für Begriffe, die sonst verwässern.

**Datenbank, Abfragesprache.** Für alles, was die Felder nicht ausdrücken: verschachtelte Verknüpfungen, Ausschlüsse, Zitationsbedingungen (`it cites (…)`). Die Brückenabfrage unten braucht sie.

**Vorschaumodus.** Zuerst nur zählen lassen, nicht ausführen. Kostet fast nichts und zeigt, ob die Verknüpfung trägt. Immer so beginnen.

**Websuche.** Drei bis sechs Wörter, über Kreuz kombiniert, jede Anfrage muss sich von den vorigen unterscheiden. Ganze Fragesätze liefern schlechtere Treffer. Die Sprachquote ist hier die einzige Steuerung – es gibt keinen Sprachparameter.

## Kalibrieren

Ziel: wissen, wie empfindlich das Ergebnis von der Formulierung abhängt, **bevor** daraus eine Aussage wird.

1. **Enge Variante** im Vorschaumodus: Kernbegriffe, Pflichtkomponenten, keine Varianten.
2. **Weite Variante**: dieselben Komponenten, alle Schreibvarianten und Synonyme.
3. Optional **mit Vokabular**: zusätzlich Schlagwörter.

Dann lesen:

| Verhältnis weit zu eng | Bedeutung |
|---|---|
| bis etwa 1,5-fach | die Formulierung ist robust, enge Variante genügt |
| 1,5- bis 3-fach | normal; weite Variante nehmen, enge als Präzisionsreserve |
| über 3-fach | die enge Variante ist nachweislich kaputt – weite oder mittlere Variante nehmen und den Grund suchen |

In einem Testfall lag das Verhältnis über dem Sechsfachen. Das war kein Grenzfall, sondern ein Konstruktionsfehler.

Die Spanne gehört in die Ausgabe. Eine einzelne Trefferzahl ohne Spanne suggeriert Genauigkeit, die es nicht gibt.

**Präzision gegenprüfen.** Bei großen Mengen eine Zufallsstichprobe ansehen. Sind viele Treffer thematisch daneben, ist die weite Variante zu weit – eine Komponente schärfen, nicht die Wirkungskomponente wieder einführen. Zur Einordnung: In systematischen Reviews liegt die Präzision der Datenbanksuche typischerweise im einstelligen Prozentbereich. Viel Rauschen ist normal, nicht Zeichen eines Fehlers.

## Recall-Test mit bekannten Treffern

Der einzige Test, der einen systematischen Suchfehler auffliegen lässt, bevor er zum Befund wird.

1. Zwei bis drei Arbeiten nehmen, die bereits bekannt sind – aus der Vorab-Klärung, aus dem Gespräch, aus einem vorliegenden Literaturverzeichnis, aus einer früheren Recherche.
2. Prüfen, ob die gewählte Anfrage sie enthält. Am schnellsten über eine Abfrage, die auf die DOIs oder Titel einschränkt und gegen die Treffermenge geprüft wird.
3. Fehlt eine: **nicht weiterarbeiten.** Den Grund suchen – fehlendes Synonym, zu strenge Phrase, erzwungene Komponente, falscher Filter –, korrigieren, erneut prüfen.

Liegen keine bekannten Arbeiten vor, lässt sich der Test nicht fahren. Dann in der Suchgüte-Zeile ausdrücklich „nicht möglich" schreiben, statt die Zeile weglassen: Eine Recherche ohne Recall-Test ist schwächer belegt, und das soll sichtbar sein.

Umgekehrt nutzbar: Fällt bei der Durchsicht eine hochrelevante Arbeit auf, die die Anfrage **nicht** gefunden hatte, ist das ein Befund über die Anfrage. Dann nachsehen, welcher Begriff gefehlt hat, und die Anfrage nachziehen.

## Kontrolliertes Vokabular

Freitext findet, was Autoren geschrieben haben. Schlagwörter finden, was Indexierung oder Modell einer Arbeit zugeordnet hat – **auch bei anderer Wortwahl, anderer Sprache und fehlendem Abstract**. Die beiden ergänzen sich; keines ersetzt das andere.

Vorgehen:

1. Schlagwörter zum Thema vorschlagen lassen, mit Themenbeschreibung und den Hauptbegriffen je Komponente.
2. **Jeden Vorschlag an seinen meistzitierten Titeln prüfen.** Falschfreunde sind häufig: die Suche nach „bank“ liefert Schlagwörter zu Ufern wie zu Geldinstituten, die nach „cell“ solche zu Biologie wie zu Stromspeichern. Behalten, was die Komponente wirklich meint – das ist dasselbe wie das Lesen einer Scope Note im Thesaurus.
3. Facettensuche mit Freitext **und** Schlagwörtern je Komponente. Sie meldet, wie viel die Schlagwörter zusätzlich bringen, und liefert Stichproben der nur darüber gefundenen Arbeiten.
4. Die Zusatztreffer-Stichprobe ansehen. Bringen sie fachlich nichts, Schlagwörter weglassen.

In einem Testfall brachte das Vokabular nur wenige Prozent mehr Treffer, bei sichtbar schlechterer Präzision. Kein Automatismus – einsetzen beim sensitiven Prinzip und wenn fremdsprachige Literatur wichtig ist.

## Brückenabfrage bei fachübergreifenden Fragen

Berühren sich in einer Frage zwei Fachdiskussionen, liegt die beste Quelle meist genau dazwischen – und keine Stichwortsuche findet sie, weil sie die Begriffe beider Seiten nur teilweise führt.

Vorgehen:

1. Je Seite die **Leitarbeit** bestimmen: die am häufigsten zitierte Grundlagenarbeit, erkennbar aus den Referenzlisten der Ausgangsarbeiten oder über die Sortierung nach Zitationen.
2. Mit der Abfragesprache nach Arbeiten suchen, die die Leitarbeit der einen Seite **zitieren** und die **Begriffe der anderen Seite führen**. In beide Richtungen.
3. Die Treffer sind die Verbindungsarbeiten.

In einem Testfall fand die eine Richtung keine einzige Arbeit, die andere eine zweistellige Zahl – darunter die passendste Quelle der ganzen Recherche. Also immer beide Richtungen abfragen.

**Keine Aussage über getrennte oder verbundene Fachdiskussionen ohne diese Abfrage.** Die Referenzlisten der Ausgangsarbeiten allein belegen das nicht – sie zeigen nur, dass diese beiden Arbeiten einander nicht berühren.

## Plattform-gezielte Websuche

Zusätze, die wissenschaftliche Treffer hochholen:

| Zusatz | Holt |
|---|---|
| `springer` | Zeitschriftenartikel und Sammelbandbeiträge inkl. Literaturverzeichnis |
| `sciencedirect`, `wiley`, `taylor francis` | Verlagszeitschriften |
| `researchgate`, `core.ac.uk` | Volltexte, oft frei, oft graue Literatur |
| `doi` | Treffer mit sauberen Metadaten |
| `dissertation`, `Diplomarbeit`, `opus`, `edoc` | Hochschulschriften, häufig Open Access |
| `schriftenreihe`, `Berichte`, `Heft`, `Abschlussbericht` | deutsche Reihenwerke und Projektberichte |
| `pdf` | frei zugängliche Volltexte |

Verlags-Kapitelseiten sind besonders wertvoll: Sie zeigen das vollständige Literaturverzeichnis offen an, auch bei geschlossenem Volltext – die beste Quelle für den Rückwärts-Schneeball.

## Wenn nichts kommt

In dieser Reihenfolge:

1. **Komponente weglassen** – zuerst die Wirkungskomponente, falls sie trotz Regel 2 drin ist.
2. **Oberbegriff wählen** – statt `Fahrradstraße` → `Radverkehrsanlage`, `Verkehrsfläche`.
3. **Analogen Fall suchen** – vergleichbare Standorte oder Konstellationen aus Nachbarbereichen. Literatur zu vergleichbaren Fällen ist oft übertragbar und gehört dann in „Kontext- und Übertragungsquellen".
4. **Über die Institution gehen** – wer forscht dazu, dann Institution plus Thema.
5. **Über eine gefundene Person gehen** – ein Autorenname plus Thema bringt oft die ganze Arbeitsgruppe; über die Autorensuche auch deren weitere Arbeiten.
6. **Über die Zitationsbeziehungen gehen** – von einer passenden Arbeit vorwärts und rückwärts, statt weiter an Begriffen zu drehen.

Ist die Literaturlage wirklich dünn, das ausdrücklich sagen – mit der Zahl aus der Sondierung. Eine belegte Aussage „zu dieser Kombination gibt es weltweit rund 70 Arbeiten, davon eine aus Deutschland" ist wertvoller als eine aufgeblähte Liste halbpassender Treffer.

## Metadaten vervollständigen

Fehlen Band, Seiten oder DOI: Titel in Anführungszeichen plus Autorname plus `doi` suchen. Häufig liefert die Verlagsseite oder ein Repositorium die vollständigen Angaben. Führt das nicht zum Ziel: Angabe weglassen und den vorhandenen Link setzen. Nicht rekonstruieren, nicht schätzen, nicht aus dem Muster anderer DOIs ableiten.
