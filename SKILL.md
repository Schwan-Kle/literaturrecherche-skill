---
name: "literaturrecherche"
license: MIT
description: Wissenschaftliche Literaturrecherche über Fachdatenbanken (OpenAlex, Consensus), deutsche und europäische Rechtsquellen und Websuche. Liefert eine kommentierte Quellenliste mit vollständigen Zitationen, DOI, Zugangshinweis, maschinell geprüften Belegen, Retraction-Prüfung, ausgewiesener Suchgüte, Zitationsnetz und auf Wunsch Impactdiagrammen. Einsetzen, wenn nach Quellen, Literatur, Studien, Papers, Fachliteratur, Referenzen oder dem Stand der Forschung gefragt wird ("gib mir Quellen für X", "finde Studien zu Y"), wenn ein Literaturverzeichnis für ein Konzept, Gutachten, eine Stellungnahme oder eine wissenschaftliche Arbeit gebraucht wird, wenn die Rechtsgrundlage eines Vorhabens zu belegen ist (Gesetz, Verordnung, EU-Richtlinie, Rechtsprechung), wenn geprüft werden soll, ob eine Quellenangabe existiert oder zurückgezogen wurde, oder wenn ein Zitations- oder Impactdiagramm gewünscht ist. Nicht für den Beleg einer einzelnen Tatsachenbehauptung und nicht als Rechtsberatung.
---

# Literaturrecherche

Liefert eine belastbare, kommentierte Quellenliste statt einer Handvoll zufälliger Suchtreffer.

Der Kern: Eine Quellenliste ist immer auch eine **Behauptung über die Literaturlage**. Diese Behauptung darf nie auf einer einzigen, ungeprüften Suchanfrage ruhen. Eine Suche ist ein Messinstrument und muss kalibriert werden, bevor man ihre Anzeige glaubt.

Antwortsprache: Deutsch, sofern die Person nicht anders schreibt. Quellen ausdrücklich auch englischsprachig.

## Abdeckung und Grenzen

Diese Übersicht auf Nachfrage wiedergeben, ihre Grenzen in jeder Ausgabe benennen.

| Bereich | Woher | Güte |
|---|---|---|
| Internationale Literatur mit DOI | OpenAlex (~270 Mio. Werke, aggregiert Crossref, PubMed, arXiv, DOAJ, Repositorien) | hoch, filterbar, maschinell prüfbar |
| Zweiter Entdeckungsweg auf dieselbe Literatur | Consensus, semantische Rangfolge über einen anders gebauten Index | hoch für Auffinden, keine Mengenaussagen |
| Fremdsprachige Zeitschriftenliteratur, auch deutsche | OpenAlex über Schlagwörter und Sprachfilter | mittel – vorhanden, aber schwächer erschlossen |
| Zitationsbeziehungen, Verlauf, Perzentile | OpenAlex | hoch |
| Prüfung bibliographischer Angaben | OpenAlex `resolve_references` | hoch für DOI-Literatur, **untauglich für graue Literatur** |
| Rücknahme- und Korrekturstatus | OpenAlex, Scholar Gateway | hoch für DOI-Literatur |
| Freie Volltextfundorte | OpenAlex (OA-Fundort) | gut |
| Gesetze, Verordnungen, EU-Richtlinien, Rechtsprechung, Gesetzesmaterialien | Rechtsquellen, Spur 2 | hoch für geltendes Recht; Fassung immer mitnennen |
| Deutsche Reihen, Behördenberichte, Sammelbände, Hochschulschriften **ohne DOI** | Websuche, Spur 3 | mittel – auffindbar, nicht systematisch erschließbar |

**Nicht abgedeckt:** Kommentarliteratur und untergesetzliche Regelwerke (Verwaltungsvorschriften, Erlasse, technische Regelwerke, Förderrichtlinien); verbindliche Rechtsauslegung – der Skill findet und zitiert Normen, er legt sie nicht aus; Zitationsabsicht (zustimmend/widersprechend – braucht einen kostenpflichtigen Dienst); systematische Erschließung der grauen Literatur; nicht digitalisierte Bestände; Volltexte hinter Bezahlschranken (der Skill nennt den Beschaffungsweg, er beschafft nicht); Vollständigkeit im Sinne eines systematischen Reviews.

**Weitere Fachdatenbanken lohnen meist nicht** – OpenAlex aggregiert Crossref, PubMed, arXiv und DOAJ bereits, und ein eigener PubMed- oder arXiv-Zugang bringt für Fragen außerhalb von Medizin und Physik nichts hinzu. Echten Zugewinn bringen nur vier Richtungen: Rechtsquellen, ein zweiter Entdeckungsweg über einen anders gebauten Index, Katalogdienste für Literatur ohne DOI und ein Dienst mit Zitationsabsicht. Begründung: `references/einrichtung.md`.

## Schritt 0: Dienste einordnen und gezielt laden

Nicht alle verfügbaren Dienste bei jeder Frage laden. Eine lange Werkzeugliste verschlechtert die Auswahl und verbraucht Kontext, der für die Auswertung gebraucht wird. Aber die Auswahl läuft **nicht über das Fachgebiet** – sie läuft über zwei Eigenschaften der Dienste und über Merkmale der Frage.

### Die zwei Achsen

**Achse 1 – Geltungsbereich.** Wofür ist der Dienst zuständig?

| Art | Erkennbar daran | Beispiele |
|---|---|---|
| **universal** | deckt alle Fächer ab | OpenAlex, Consensus |
| **fachlich gebunden** | ein Fachgebiet | PubMed (Biomedizin), arXiv (Physik, Mathematik, Informatik) |
| **verlagsgebunden** | ein Verlagskorpus | Scholar Gateway |
| **rechtsraumgebunden** | eine Jurisdiktion | deutsche und EU-Rechtsdienste; Dienste für andere Rechtsräume |
| **kein Literaturdienst** | Karten, Geodaten, Projektverwaltung | gehören nicht in diesen Skill, auch wenn sie angebunden sind |

**Achse 2 – Funktion.** Was liefert er? Entdeckung · Metadaten und Zitationen · Volltext · Normtext · Prüfung bibliographischer Angaben. Zwei Dienste mit gleicher Funktion sind erst dann redundant, wenn auch ihr Geltungsbereich und ihr Zugriffsweg gleich sind.

### Die Auswahlregel

**Universale Entdeckungsdienste werden nicht gefiltert.** Ihr Unterschied ist der **Zugriffsweg** – boolesche Suche mit Filtern gegen semantische Rangfolge –, nicht das Fach. Wer sie thematisch auswählt, bekommt genau den blinden Fleck zurück, den der zweite Weg aufdecken soll: In einem Testlauf fand der semantische Weg Arbeiten, die eine ausgereizte boolesche Suche verfehlt hatte, und widerlegte damit eine Lückenaussage. Auf der vollen Stufe also immer beide.

**Gebundene Dienste werden gefiltert**, und zwar nach Merkmalen der Frage, nicht nach ihrem Thema:

| Merkmal der Frage | Dann laden |
|---|---|
| immer | universale Entdeckung, Metadaten und Zitationen, Prüfung |
| hat eine rechtliche Dimension – Genehmigung, Haftung, Vertrag, Zulassung, Förderung | Rechtsdienste **des betroffenen Rechtsraums** |
| betrifft Menschen, Medizin, Arzneimittel, Toxikologie, Zoonosen | biomedizinischen Dienst |
| betrifft Physik, Mathematik, Informatik, quantitative Methoden | fachgebundenen Preprint-Dienst |
| Volltext einer bestimmten Arbeit nötig | Volltextdienst des jeweiligen Verlags oder Repositoriums |
| „ist das umstritten", „wie wurde das aufgenommen" | Dienst mit Zitationsabsicht, falls vorhanden |

Dieser Schnitt ist **fachunabhängig**: Er funktioniert für eine historische, eine medizinische und eine technische Frage gleichermaßen, weil er nach dem fragt, was die Frage braucht, und nicht nach einem Fachregister.

Vor dem Laden den Rechtsraum bestimmen, nicht voraussetzen. „Rechtsfrage" heißt nicht automatisch deutsches Recht. Gibt es für den betroffenen Rechtsraum keinen Dienst, das sagen und auf amtliche Quellen verweisen.

### Was in dieser Sitzung vorhanden ist

Dienste sind oft nicht vorgeladen. Mit einer Werkzeugsuche laden – aber nur das, was die Auswahlregel verlangt, und in **einer** Suchanfrage:

- `openalex literature citations keywords` – universale Entdeckung, Metadaten, Zitationen, Prüfung
- `consensus search papers` – zweiter Entdeckungsweg, semantisch
- `legal legislation court decisions` – Rechtsdienste
- `pubmed biomedical articles` – biomedizinischer Dienst
- `scholar full text passages` – Volltextpassagen aus einem Verlagskorpus

Das Rückgrat, falls vorhanden, ist OpenAlex: `search_works` (Stichwort, semantisch, Abfragesprache, `preview` für Mengen), `find_keywords` und `keyword_search` (kontrolliertes Vokabular, mit gemessenen Teilmengen), `get_work` (Werkdatensatz, Zitationen pro Jahr, OA-Fundort, Perzentil), `resolve_references` (bis 25 Angaben prüfen), `list_citations` (zitierend, zitiert, verwandt), `group_works` (Sondierung).

**Betriebsregeln einzelner Dienste.** Manche verlangen eine eigene Zitierweise im Antworttext und einen wörtlich zu übernehmenden Hinweis am Ende; der kommt dann ganz zum Schluss, nach der Recherchebasis, während die Quellen im Format unten geführt werden. Manche haben Rate-Limits – dann höchstens drei Abfragen auf einmal und bei Abweisung warten. Manche laufen über den Rechner der Person; antworten sie nicht, ist er nicht erreichbar, und dann wird nichts aus dem Gedächtnis behauptet. Filter nur setzen, wenn die Person danach fragt.

**Fehlt jede Fachdatenbank**, allein mit Websuche arbeiten, das in der Recherchebasis ausdrücklich sagen und keine Datenbankabfrage vortäuschen.

## Die drei Spuren

Jede Spur erschließt einen eigenen Literaturkörper. Keine ersetzt eine andere.

**Spur 1 – Fachdatenbanken.** Literatur mit DOI, filterbar, mit Zitationsbeziehungen und Integritätsdaten. Zwei Zugriffswege: boolesche Suche mit Filtern über OpenAlex, semantische Rangfolge über Consensus. Auf der vollen Stufe **beide**, weil sie unterschiedliche Arbeiten finden. Blind für Veröffentlichungen ohne DOI.

**Spur 2 – Rechtsquellen.** Gesetze, Verordnungen, Richtlinien, Rechtsprechung, Gesetzesmaterialien. Bei rechtlich gebundenen Fragen – Zulassungen, Haftung, Verträge, Förderung – ist das **keine Ergänzung, sondern die tragende Spur**: Ein Gutachten steht oder fällt mit der zutreffenden Norm in der geltenden Fassung, nicht mit einem Zeitschriftenaufsatz.

**Zuerst den Rechtsraum bestimmen**, dann den Dienst wählen – übernationales Recht, Bundes- oder Zentralstaatsebene, Gliedstaat, dann Rechtsprechung. Welcher Rechtsraum gilt, ergibt sich aus Standort, Vorhabensträger und Verfahrensart, nicht aus der Sprache der Frage. Fehlt für diesen Rechtsraum ein Dienst, das sagen und auf amtliche Quellen verweisen statt den Rechtsstand aus dem Gedächtnis zu behaupten. Vorgehen und Fallstricke: `references/rechtsquellen.md`.

**Spur 3 – Websuche.** Deutsche Reihen, Behördenberichte, Sammelbände, Hochschulschriften, Projektberichte, technische Regelwerke. In angewandten Fächern der praxisrelevanteste Teil der Fachliteratur.

Wer nur Spur 1 fährt, liefert eine formal makellose Liste, die für ein deutsches Gutachten unbrauchbar ist. Wer die Rechtsspur bei einer Rechtsfrage auslässt, liefert Literatur statt Grundlage. Wer nur Spur 3 fährt, verliert Präzision, Zitationsdaten und jede maschinelle Prüfung.

Welche Spuren Pflicht sind, richtet sich nach der Frage: **Spur 1 und 3 immer auf der vollen Stufe, Spur 2 immer dann, wenn die Frage einen Rechtsbezug hat** – und das hat sie bei verwaltungsnahen Fragen fast immer.

## Aufwand und Rechercheprinzip

Zwei Festlegungen, beide in einem Halbsatz mitteilen.

**Stufe:**

| Stufe | Auslöser | Umfang |
|---|---|---|
| **kompakt** | „ein paar Quellen zu X" | 2–3 Datenbankabfragen, 2–4 Websuchen, 4–6 Quellen |
| **voll** | „Literatur für Konzept/Gutachten", „Stand der Forschung" | Vorab-Klärung, Sondierung, Kalibrierung, 6–12 Quellen, Zitationsnetz |
| **prüfend** | „stimmt diese Angabe", „ist das zurückgezogen" | `resolve_references`, `get_work` |
| **Rezeption/Impact** | „wie wurde das aufgenommen", „zeig den Impact" | Zitationsverlauf und Netz als Hauptergebnis |

**Rechercheprinzip** – die etablierte Unterscheidung, zwischen den Polen liegt ein Kontinuum:

- **sensitiv**: breit, viele Begriffe, wenige Grenzen. Mehr Treffer, mehr Durchsicht, geringes Risiko, etwas zu verpassen. Für Konzepte, Gutachten, Stand der Forschung.
- **spezifisch**: eng, Kernbegriffe, starke Filter. Wenige Treffer, wenig Durchsicht, höheres Risiko. Für eine schnelle Orientierung.

Im Zweifel die kompakte Stufe mit spezifischem Prinzip und am Ende anbieten, sensitiv nachzufahren.

## Arbeitsablauf

### 1. Vorab klären – aber nur, wenn es die Suchanfrage ändert

„Radverkehr“ kann heißen: Methodenpapiere für eine Verkehrserhebung, zitierfähige Belege für ein Gutachten, Vergleichswerte für eine Planung. Das sind **drei verschiedene Suchen**.

Stelle höchstens **drei Fragen**, als Auswahlfragen, ausdrücklich überspringbar – und nur solche, deren Antwort die Suchanfrage oder die Filter tatsächlich verändert:

- **Zweck** (Konzept · Gutachten/Stellungnahme · wissenschaftliche Arbeit · eigener Wissensaufbau) → steuert Rechercheprinzip, Beleghärte, Zitierstil.
- **Räumlicher oder rechtlicher Bezug** (Bundesland · Deutschland · Mitteleuropa · weltweit) → steuert Spur 2 und den Sprachanteil.
- **Was schon vorliegt**: zwei bis drei bekannte Arbeiten oder ein vorhandenes Literaturverzeichnis → das sind die Prüfsteine für Schritt 5. Diese Frage ist die wertvollste.

Keine Fragen stellen, wenn der Auftrag eindeutig ist, auf der kompakten Stufe, oder wenn niemand antworten kann. Dann die naheliegendste Lesart nehmen und **sagen, welche**.

### 2. Suchkomponenten festlegen

Zerlege das Thema in **Komponenten**, nicht in beliebige Achsen. Zwei Regeln entscheiden über den Erfolg:

**Regel 1 – Aufzählbarkeit.** Eine Komponente taugt nur, wenn ihre Synonyme vollständig aufzählbar sind. Lässt sich das nicht (Beispiele: „interdisziplinär", „innovativ", „nachhaltig"), **fliegt die Komponente raus** und wird erst bei der Durchsicht der Treffer angewandt.

**Regel 2 – keine erzwungene Wirkungskomponente.** Gegenstand, Maßnahme und Standort stehen in Titeln und Abstracts; **Wirkungen und Ergebnisse stehen dort oft nicht**. Eine Outcome-Komponente als Pflichtbedingung kostet massiv Treffer.

> Erfahrung aus Testläufen: Eine erzwungene Wirkungskomponente senkte die Trefferzahl um ein Vielfaches und ließ gerade die methodisch passendsten Arbeiten verschwinden. Ohne sie – bei sonst gleichen Begriffen und ergänzten Schreibvarianten – stand eine davon auf Platz 1. Im Vorschaumodus gegenprüfen.

Also: zwei, höchstens drei Pflichtkomponenten. Alles Weitere ist Filter oder Sortierkriterium, nicht Suchbedingung.

| Komponente | Deutsch | Englisch |
|---|---|---|
| Maßnahme | Radwegebau, Radverkehrsförderung, Fahrradstraße | cycling infrastructure, bike lane, cycle track |
| Standort | Innenstadt, Stadtgebiet, Kommune | urban area, city centre, municipality |

Vertiefung, Schreibvarianten und Anfrageformen je Werkzeug: `references/suchstrategie.md`.

### 3. Sondieren (volle Stufe)

Mit `group_works` die Literaturlage vermessen, bevor Quellen gesammelt werden: Menge insgesamt, Verteilung über die Jahre, Länder, Zeitschriften.

Das kostet eine Abfrage und verändert alles Weitere: Bei 40 Treffern sieht die Strategie anders aus als bei 4.000, und die Aussage „dazu gibt es kaum Literatur" wird belegbar statt behauptet.

### 4. Kalibrieren – zwei bis drei Varianten, dann entscheiden

**Nie mit einer einzigen Anfrage weiterarbeiten.** Fahre im Vorschaumodus (nur Mengen, kaum Kosten) mindestens zwei Varianten:

1. **eng**: Kernbegriffe, Pflichtkomponenten, ohne Varianten.
2. **weit**: dieselben Komponenten plus alle Schreibvarianten und Synonyme.
3. optional **mit Vokabular**: zusätzlich die Schlagwörter der Datenbank (Schritt 5).

Vergleiche die Mengen. **Weichen sie um mehr als das Dreifache ab, weißt du über das Feld noch nichts** – die enge Variante ist dann verdächtig, nicht schon widerlegt: Der Recall-Test (Schritt 5) entscheidet. Findet die enge Variante die bekannten Treffer nicht, gilt die weite oder eine mittlere. Findet sie sie, darf sie bleiben; die große Spanne wird dann als Präzisionsgewinn ausgewiesen. Die Spanne gehört in die Ausgabe: Sie ist selbst eine Aussage über die Belastbarkeit.

Dann eine Variante wählen, die Wahl begründen und benennen, was dabei herausfällt.

### 5. Bekannte Treffer prüfen – der Recall-Test

Nimm die zwei bis drei Arbeiten, die aus Schritt 1, aus dem Gespräch oder aus einem vorliegenden Verzeichnis bereits bekannt sind, und prüfe, ob die gewählte Anfrage sie **findet**.

- **Findet sie sie** → die Anfrage trägt.
- **Findet sie sie nicht** → die Anfrage ist kaputt. Nicht weiterarbeiten, sondern den Grund suchen: fehlendes Synonym, zu strenge Phrase, erzwungene Komponente. Dann korrigieren und erneut prüfen.

**Wähle die bekannten Arbeiten bewusst mit abweichender Wortwahl** (älter, Berichte/graue Literatur, Nachbarfach, anderer Begriff für dasselbe) – Arbeiten, die du über den Kernbegriff gefunden hast, findet die Anfrage immer, der Test prüft dann nur die eigene Formulierung. Fehlen solche Arbeiten, hole sie aus dem Literaturverzeichnis einer Übersichtsarbeit zum Thema.

Das ist der etablierte Weg (relativer Recall) und der einzige, der einen systematischen Suchfehler auffliegen lässt, bevor er zum Befund wird. Gibt es keine bekannten Arbeiten, lässt sich der Test nicht fahren – dann gehört das in die Suchgüte-Zeile.

### 6. Suchen

**Spur 1, erster Weg – OpenAlex:** gewählte Variante ausführen; zusätzlich **semantische Suche** mit der Forschungsfrage als ganzem Satz. Vielversprechende Treffer per `get_work` nachladen. `list_citations` für Vorwärts- und Rückwärtsverfolgung; das ersetzt den manuellen Schneeball und ist vollständiger.

**Spur 1, zweiter Weg – Consensus:** dieselbe Forschungsfrage als ganzer Satz, in Fachsprache. Pflicht auf der vollen Stufe, und zwar **nachdem** die OpenAlex-Suche steht: Was hier auftaucht und dort fehlte, ist der Beleg dafür, wo die boolesche Anfrage blind war. Taucht Wichtiges auf, nicht einfach hinzufügen, sondern **die OpenAlex-Anfrage nachziehen** und notieren, welcher Begriff gefehlt hat – sonst bleibt der Fehler in der Anfrage und damit in jeder Mengenaussage.

**Bei fachübergreifenden Fragen die Brücke direkt abfragen.** Berühren sich zwei Fachdiskussionen, suche gezielt Arbeiten, die **die Leitarbeit der einen Seite zitieren und die Begriffe der anderen führen**. Das findet die Verbindungsarbeiten, auf die keine Stichwortsuche kommt. Keine Aussage über getrennte oder verbundene Stränge ohne diese Abfrage: Referenzlisten der Ausgangsarbeiten allein belegen das nicht.

**Spur 2 – Rechtsquellen**, wenn die Frage einen Rechtsbezug hat. Von oben nach unten: EU-Recht, Bundesrecht, Landesrecht, dann Rechtsprechung. Normen immer mit Fassung und Stand, nie aus dem Gedächtnis. Vorgehen, Reihenfolge und die Fallstricke der einzelnen Dienste: `references/rechtsquellen.md`.

**Spur 3 – Websuche:** deutsche Fachliteratur, Behörden, Hochschulschriften, Projektberichte; Rückwärts-Schneeball über Literaturverzeichnisse zentraler Sammelbände. Einstiegspunkte: `references/fachgebiete.md`.

**Sprachquote.** Die Websuche hat keinen Sprachparameter – die Trefferspache entsteht allein aus den Begriffen. Mindestens ein Drittel der Websuchen deutsch, mindestens ein Drittel englisch, kompakt je zwei. Für bibliographische Websuchen das gründliche Suchwerkzeug nutzen, nicht die schnelle Variante.

### 7. Kontrolliertes Vokabular (volle Stufe, sensitives Prinzip)

Die Datenbank verschlagwortet Werke. Diese Schlagwörter greifen **auch bei anderer Wortwahl, anderer Sprache und fehlendem Abstract** – damit erreichen sie einen Teil der fremdsprachigen Literatur, den Freitext verfehlt.

1. `find_keywords` mit Themenbeschreibung und den Hauptbegriffen je Komponente.
2. **Jedes Schlagwort an seinen meistzitierten Titeln prüfen.** Falschfreunde sind häufig: ein mehrdeutiger Begriff wie „bank“ liefert Schlagwörter zu Ufern wie zu Geldinstituten. Nur behalten, was die Komponente wirklich meint – das entspricht dem Lesen einer Scope Note.
3. `keyword_search` mit Freitext **und** Schlagwörtern je Komponente. Es meldet, wie viel die Schlagwörter zusätzlich bringen und zieht Stichproben.

Der Zugewinn war in Tests klein, die Präzision sichtbar niedriger. Also kein Automatismus – nutzen, wenn sensitiv gesucht wird oder fremdsprachige Literatur wichtig ist, sonst weglassen und das sagen.

### 8. Integrität prüfen

**Für jede Quelle mit DOI verpflichtend.** Eine zurückgezogene Arbeit in einem Gutachten ist ein Schaden, der sich nicht einfangen lässt, und von außen nicht erkennbar.

| Befund | Kennzeichnung | Folge |
|---|---|---|
| zurückgezogen | ⚠ **ZURÜCKGEZOGEN** | nicht in die Kernquellen |
| Bedenken geäußert | ⚠ Expression of Concern | nur mit ausdrücklichem Hinweis |
| Korrektur/Erratum | Korrektur vorhanden | auf die korrigierte Fassung verweisen |

Zitationslage als Signal lesen: Perzentil und Verlauf zeigen, ob eine Arbeit getragen wird. Zahlen nur aus dem Datensatz. Zustimmung und Widerspruch sind aus OpenAlex **nicht** unterscheidbar – das benennen, nicht überspielen.

### 9. Absichern – die Endkontrolle

**Nicht optional.** Eine erfundene DOI entwertet die ganze Liste.

**Maschinell:** DOIs und Kurzangaben in `resolve_references`. Meldet `exact`, `likely`, `uncertain`, `none`.

**Ein „none" ist kein Beweis für Nichtexistenz.** Geprüft: Mehrere nachweislich existierende deutsche Titel – Behördenbericht, Diplomarbeit, Praxisleitfaden, Sammelbandbeitrag – ergaben `none`, genau wie eine zur Kontrolle frei erfundene Angabe. Die Datenbank kann beides nicht unterscheiden.

| Art der Angabe | `none` bedeutet |
|---|---|
| englischsprachige Zeitschriftenliteratur, DOI erwartbar | starkes Warnsignal – über Websuche gegenprüfen |
| deutsche graue Literatur, Reihen, Hochschulschriften | nichtssagend – Belegstufe über Spur 2 erarbeiten |

Niemals eine reale graue Quelle wegen `none` streichen, niemals ein `none` als „geprüft" ausgeben. Bei `uncertain` Autoren und Jahr von Hand abgleichen.

**Von Hand**, für jedes Element – Autor, Jahr, Titel, Zeitschrift, Band, Heft, Seiten, DOI, Verlag: Steht es in einem Datensatz, Suchergebnis oder auf einer Seite, die ich in dieser Sitzung gesehen habe? Nein → streichen. Nicht rekonstruieren, nicht aus dem Muster anderer DOIs ableiten.

| Stufe | Bedeutung |
|---|---|
| **A** | Datenbanksatz, maschinell aufgelöst, Integrität geprüft |
| **B** | Verlags-, Repositoriums- oder Projektseite bestätigt |
| **C** | vollständige Angabe aus einem Suchergebnis |
| **D** | nur aus fremder Literaturliste → „Weitere Spuren" |

Fehlende Elemente kennzeichnen: `(Seitenzahlen nicht ermittelt)`.

### 10. Zitationsnetz, Widersprüche, Festhalten

**Netz und Impact (volle Stufe).** Aus `list_citations` entsteht das Netz, aus den Zitationen pro Jahr der Verlauf, aus `group_works` die Einordnung. Welche Darstellung wann, welche Auswertungen daraus folgen, welche Diagrammform wofür und wo die Ehrlichkeitsgrenzen liegen: `references/zitationsnetz-impact.md`. Diagramme werden angeboten, nicht ungefragt erzeugt – außer die Person hat danach gefragt.

**Widersprüche.** Kommt die internationale Literatur zu einem anderen Schluss als die deutsche Praxisliteratur, ist das **ein Befund, kein Problem**. Als eigener Punkt in die Einschätzung, mit beiden Positionen und dem wahrscheinlichen Grund. Genau dort wird ein Gutachten angegriffen.

**Festhalten.** Jede Datenbankabfrage liefert eine **reproduzierbare Abfrage-URL**. Bei wiederkehrenden Themen die der gewählten Variante mitgeben: Damit lässt sich dieselbe Suche später erneut fahren und auf neue Treffer prüfen. Für Gutachten ist sie zugleich der methodische Nachweis.

## Ausgabeformat

Quellen oben, Verfahren unten.

```markdown
## Kernquellen – direkt zum Thema

**1. Autor, A., Autor, B. & Autor, C. (Jahr).** Titel. *Zeitschrift*, Band(Heft), Seiten. https://doi.org/... [Open Access] `A`
– Was untersucht wurde. Kernbefund. Einschränkung oder Übertragbarkeitshinweis. [ggf. Zitationslage]

## Kontext- und Übertragungsquellen
## Theoretische und methodische Grundlagen
## Weitere Spuren (Belegstufe D, nicht verifiziert)
## Zitationsnetz

## Einschätzung

- **Besonders geeignet für [Zweck]:** Nr. x, y – kurze Begründung.
- **Widerspruch zwischen den Spuren:** [nur wenn vorhanden].
- **Lücken der Literaturlage:** was es offenbar nicht gibt, mit Zahl aus der Sondierung.
- **Lücken der Recherche:** was diese Suche nicht erfassen konnte.
- **Naheliegende Vertiefung:** ein bis zwei Anschlussrichtungen.

## Suchgüte

- **Rechercheprinzip:** sensitiv | spezifisch – [Begründung in einem Halbsatz]
- **Trefferspanne der Varianten:** [eng] bis [weit][, mit Vokabular n] – gewählt: [welche, warum]
- **Recall-Test:** [n von n] bekannten Arbeiten gefunden | nicht möglich, keine bekannten Arbeiten vorgelegt
- **Zweiter Entdeckungsweg:** [n] Arbeiten, die nur über die semantische Suche kamen – [was daraus folgte: Anfrage nachgezogen / nichts Wesentliches]
- **Was die gewählte Variante ausschließt:** [konkret]

## Recherchebasis und Belegkontrolle

*Belegstufen: A = Datenbanksatz, maschinell aufgelöst und Integrität geprüft · B = Verlags- oder
Repositoriumsseite bestätigt · C = vollständige Angabe aus einem Suchergebnis · D = nicht verifiziert*

- **Geladene Dienste und warum:** [welche, je mit dem Merkmal der Frage, das sie verlangt hat; und welche bewusst nicht]
- **Abfragen:** [n] universale Entdeckung, [n] zweiter Weg, [n] Rechtsquellen, [n] Websuchen ([n] deutsch, [n] englisch)[, n weitere]
- **Suchkomponenten:** [die tatsächlich verwendeten, mit weggelassenen und warum]
- **Abfrage-URL der gewählten Variante:** [reproduce_url]
- **Abgedeckt / nicht abgedeckt:** [knapp]
- **Belege:** [n]× A, [n]× B, [n]× C, [n]× D – maschinell geprüft: [n] von [n] aufgelöst
- **Integrität:** [n] Quellen mit DOI geprüft – [Befunde oder „keine Auffälligkeiten"]
- **Geprüft und verworfen:** [n] Treffer [Gründe in Stichworten]
- **Stand:** [Datum]
```

Immer vorhanden: Einschätzung, Suchgüte, Recherchebasis. Zitationsnetz nur auf der vollen Stufe. Übrige Abschnitte entfallen, wenn leer.

Auf Wunsch BibTeX, RIS oder CSV aus den Datenbankfeldern – nur Belegstufen A bis C, nie aus dem Gedächtnis formatiert.

### Formatregeln

- **Zitierstil:** `Autor, A. & Autor, B. (Jahr). Titel. Zeitschrift, Band(Heft), Seiten. DOI/Link`. Buchbeiträge: `In: Herausgeber (Hrsg.), Buchtitel (S. x–y). Verlag.` Hochschulschriften: `Dissertation/Masterarbeit, Hochschule.`
- Bis drei Autoren ausschreiben, ab vier `Erstautor, A. et al.` – außer der Auftrag verlangt einen Stil.
- **Zugangshinweis:** `[Open Access]`, `[PDF frei]`, `[Paywall]`, `[institutioneller Zugang]`, `[nur Abstract]`, `[Druck]`. Bei Datenbanktreffern den gemeldeten OA-Fundort übernehmen, nicht schätzen. Ohne freien Fundort nicht nach Umwegen suchen, sondern den regulären Weg nennen: Fernleihe und Dokumentlieferung der Landes- oder Universitätsbibliothek, Repositoriumsfassung, Autorenanfrage.
- **Belegstufe** als letztes Zeichen der Zitationszeile.
- **Fachbegriffe erklären**, wo sie zuerst auftauchen – FWCI, Perzentil, Belegstufe. Ungeklärte Kennzahlen sind wertlos.
- **Kommentar in einem Absatz**, zwei bis vier Sätze, keine Aufzählungen darin.
- **Kritisch bleiben.** „Untersucht die Maßnahme nicht als eigenen Versuchsfaktor" oder „einjährige Untersuchung, daher nur eingeschränkt belastbar" ist das Wertvollste an der Liste. Eine Liste ohne einen einzigen Einschränkungshinweis ist verdächtig.

### Beispieleintrag

> **2. Mustermann, A., Beispiel, B. & Exempla, C. (2020).** Beispieltitel einer Studie zum Thema. *Beispielzeitschrift*, 12(3), 45–67. https://doi.org/10.0000/beispiel [Open Access] `A`
> – Fiktiver Eintrag zur Illustration des Formats, keine reale Quelle. Untersucht [Gegenstand] mit [Methode]; [n] Zitationen, feldnormiert im [x]. Perzentil, stetig zitiert. Ordnet die Arbeit gegenüber der Fragestellung ein und benennt den Punkt, an dem sie nicht passt, etwa die Übertragbarkeit auf einen anderen Standort oder eine kurze Untersuchungsdauer.

Daran zu erkennen: vollständige Angaben, Zugang und Belegstufe ausgewiesen, Methode konkret, Kennzahl eingeordnet statt nur genannt, und ein klar benannter Punkt, an dem die Quelle nicht passt.

## Rückfragen

Vorab nur die Fragen aus Schritt 1. Nach der Ausgabe genau **eine** kurze Rückfrage, die die Recherche zuspitzt. Kein Fragenkatalog.

## Häufige Fehler

- **Wirkungskomponente erzwungen.** Der teuerste Fehler, in Tests ein Trefferverlust um ein Vielfaches. Siehe Schritt 2.
- **Mit einer einzigen Anfrage gearbeitet** und daraus einen Befund über die Literaturlage gemacht. Ohne Kalibrierung ist jede solche Aussage geraten.
- **Schreibvarianten übersehen.** „electric bike“ findet „electric cargo bike“ nicht – ein eingeschobenes Wort bricht die Phrase. Siehe `references/suchstrategie.md`.
- **Platzhalter gesetzt.** Das Standardsuchfeld ist stammformreduziert und weist Platzhalter ab; in mehrwortigen Phrasen sind sie grundsätzlich unzulässig. Beugung und Wortfamilien deckt die Stammformreduktion ab – Synonyme und Schreibvarianten werden ausgeschrieben.
- **Recall-Test übersprungen**, obwohl bekannte Arbeiten vorlagen.
- **Universale Entdeckungsdienste thematisch gefiltert.** Ihr Unterschied ist der Zugriffsweg, nicht das Fach; eine Fachauswahl stellt genau den blinden Fleck wieder her, den der zweite Weg aufdecken soll.
- **Gebundene Dienste ungefiltert mitgeladen.** Dreißig Rechtswerkzeuge bei einer rein naturwissenschaftlichen Frage blähen die Werkzeugliste auf und verschlechtern die Auswahl.
- **Rechtsraum vorausgesetzt statt bestimmt.** Eine Rechtsfrage ist nicht automatisch eine Frage deutschen Rechts.
- **Nur einen Entdeckungsweg gefahren.** Eine boolesche Suche und eine semantische Suche über einen anders gebauten Index finden unterschiedliche Arbeiten; eine Lückenaussage auf Basis nur eines Weges ist nicht belastbar.
- **Rechtsfrage ohne Rechtsspur beantwortet.** Literatur über eine Norm ist kein Ersatz für die Norm in der geltenden Fassung.
- **Nur Spur 1 gefahren**, weil sie sauberer aussieht. Das Ergebnis ist formal makellos und für ein deutsches Gutachten unbrauchbar.
- **Einsprachig gesucht.**
- **Schlagwort ohne Prüfung übernommen** – Falschfreunde (mehrdeutige Begriffe) sind häufig.
- **Integrität nicht geprüft.**
- **`none` als Nichtexistenz gelesen.**
- **DOI oder Seitenzahl geraten.**
- **Zu breit abgefragt.** Trefferlisten 10–25, Kantenmengen begrenzt, Volltext nur gezielt. Lieber zweimal eng als einmal breit.
- **Zustimmung oder Widerspruch behauptet**, obwohl die Zitationsabsicht fehlt.
- **Graue Literatur ausgeschlossen**, weil nicht begutachtet. Sie gehört gleichberechtigt in die Kernquellen – mit Hinweis auf die Beleghärte.
- **Widerspruch zwischen den Spuren geglättet.**
- **Unrechtmäßige Volltextquellen genutzt.** Schattenbibliotheken sind kein Beschaffungsweg.
