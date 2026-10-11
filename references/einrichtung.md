# Einrichtung und Auswahl der Datenbankdienste

Lies diese Datei, wenn gefragt wird, welche Dienste eingebunden werden sollten, wie das geht, oder ob ein weiterer Dienst lohnt.

## Inhalt

- [Grundregel: wenige, gute Dienste](#grundregel-wenige-gute-dienste)
- [Pflicht: OpenAlex](#pflicht-openalex)
- [Was echten Zugewinn bringt](#was-echten-zugewinn-bringt)
- [Was vor allem Redundanz bringt](#was-vor-allem-redundanz-bringt)
- [Was nicht genutzt wird](#was-nicht-genutzt-wird)
- [Einbindungswege](#einbindungswege)

## Grundregel: nach Geltungsbereich und Funktion, nicht nach Fach

Jeder eingebundene Dienst verlängert die Werkzeugliste. Eine lange Liste verschlechtert die Auswahl des richtigen Werkzeugs und verbraucht Kontext, der für die Auswertung gebraucht wird. **Drei gut gewählte Dienste liefern bessere Ergebnisse als zehn.**

Die Frage bei jedem zusätzlichen Dienst lautet daher nicht „bringt er Treffer?“, sondern „erschließt er einen Literaturkörper oder einen Zugriffsweg, den die vorhandenen Dienste nicht haben?“. Zwei Dienste sind erst dann redundant, wenn Geltungsbereich, Funktion **und** Zugriffsweg übereinstimmen.

Daraus folgt die Einordnung – und sie ist bewusst **nicht** fachlich:

| Art | Auswahl |
|---|---|
| universale Entdeckung | **nie thematisch filtern**; mehrere Zugriffswege nebeneinander nutzen |
| fachlich gebunden | nur laden, wenn die Frage in das Fach fällt |
| verlagsgebunden | nur laden, wenn ein Volltext gebraucht wird |
| rechtsraumgebunden | nur laden, wenn die Frage eine rechtliche Dimension hat – und nur für den betroffenen Rechtsraum |
| kein Literaturdienst | nie in dieser Recherche verwenden, auch wenn angebunden |

Der letzte Punkt ist kein Formalismus: Karten-, Geodaten- und Projektdienste sind für andere Aufgaben angebunden. Sie in eine Literaturrecherche zu ziehen, liefert nichts und kostet Kontext.

Zweite Grundregel: Jeder Dienst sieht die Suchanfragen. Bei Suchanfragen mit vertraulichem Bezug ist das bei jedem neuen Anbieter neu zu bewerten, nicht einmal pauschal.

## Pflicht: OpenAlex

Der offizielle OpenAlex-Server von OurResearch ist das Rückgrat. Kostenlos, kein Kontingent, als entfernter Dienst auch ohne lokale Installation nutzbar – er funktioniert damit in einer reinen Chat-Sitzung genauso wie in einer Arbeitsumgebung.

Endpunkt: `https://mcp.openalex.org/mcp` (Streamable HTTP). Einbindung über die Connector-Einstellungen als eigener Connector; in einer Kommandozeilenumgebung als HTTP-Transport.

Zur Anmeldung gibt es widersprüchliche Angaben: Die Installationsnotiz nennt keine Anmeldung, der Abschnitt zur Anmeldung beschreibt ein OAuth-Verfahren, bei dem Abfragen über einen eigenen OpenAlex-Schlüssel laufen. Beides ist kostenfrei. Wenn eine Anmeldung verlangt wird, ist das kein Fehler.

Deckt ab: Suche (stichwortbasiert, semantisch, mit Filtern), Werkdatensätze mit Zitationen pro Jahr und OA-Fundort, Prüfung bibliographischer Angaben, Zitationsnetz vorwärts und rückwärts, Entitäten (Autoren, Institutionen, Zeitschriften, Themen, Förderer), Mengenauswertungen mit Perzentilen.

## Was echten Zugewinn bringt

**1. Rechtsquellen** – der größte Zugewinn für verwaltungsnahe Arbeit, und ein Literaturkörper, den keine Fachdatenbank führt. Deutsche Gesetze von Bund und Ländern, deutsche Rechtsprechung, EU-Recht, Rechtsprechung des Europäischen Gerichtshofs, Bundestagsmaterialien. Bei rechtlich gebundenen Fragen die tragende Spur, nicht eine Ergänzung. Einzelheiten und Fallstricke: `references/rechtsquellen.md`.

**2. Ein zweiter Entdeckungsweg über einen anders gebauten Index** – etwa ein Dienst mit semantischer Rangfolge über Semantic Scholar, OpenAlex und PubMed. Das klingt nach Redundanz und ist keine: In einem Testlauf fand der zweite Weg Arbeiten, die eine ausgereizte boolesche Suche nicht gefunden hatte, und widerlegte damit eine Lückenaussage. Zusätzlich Filter für Studiendesign, Stichprobengröße und Zeitschriftenquartil, die OpenAlex nicht hat.

Zu beachten: Rate-Limits, und manche Dienste verlangen eine eigene Zitierweise und einen wörtlich zu übernehmenden Hinweistext. Das kollidiert mit dem Ausgabeformat und ist bewusst zu handhaben, nicht zu übergehen.

**3. Katalog- und Repositoriumsdienste für Literatur ohne DOI** – die größte verbleibende Lücke in der Fachliteratur.

- **BASE** erschließt Hunderte Millionen Dokumente aus Repositorien, darunter viel deutschsprachige graue Literatur ohne DOI.
- **Verbundkataloge über das SRU-Protokoll**: K10plus (Bibliotheken aus zehn Bundesländern, rund 80 Mio. Datensätze) und die Deutsche Nationalbibliothek. Erschließt Monographien, Sammelbände, Schriftenreihen und Hochschulschriften.
- Ertrag: Einträge, die heute auf Belegstufe C oder D hängen, erreichen geprüfte Metadaten. **Verifikationsgewinn, kein Entdeckungsgewinn** – Katalogsuche ist Titel-, Schlagwort- und Personensuche ohne thematische Relevanzsortierung und ohne Abstracts.

**4. Ein Dienst mit Zitationsabsicht** – die einzige fachlich nicht ersetzbare Lücke in den Zitationsdaten. Die Unterscheidung, ob eine Arbeit zustimmend, widersprechend oder nur erwähnend zitiert wird, bietet derzeit praktisch nur ein kostenpflichtiger Anbieter. Ohne ihn bleibt der Abschnitt „Umstritten" im Zitationsnetz leer, und Aussagen über Zustimmung oder Widerspruch sind unzulässig.

**5. Ein Literaturspeicher** – kein Suchdienst, aber nützlich bei wiederkehrenden Themen. Zotero kann Einträge **ohne DOI** aufnehmen und ist damit der einzige sinnvolle Ort, um die deutschsprachige graue Literatur dauerhaft zu sammeln. Für eine Chat-Sitzung muss der Zugang über die Web-Schnittstelle laufen.

## Was vor allem Redundanz bringt

OpenAlex aggregiert diese Quellen bereits. Einbinden lohnt nur bei einem besonderen Bedarf:

| Dienst | Warum meist verzichtbar |
|---|---|
| Crossref | von OpenAlex aggregiert; eigener Nutzen fast nur bei sehr frischen DOI-Registrierungen |
| Unpaywall | OpenAlex liefert den OA-Fundort schon mit (gleicher Betreiber) |
| OpenCitations | Zitationsbeziehungen kommen aus OpenAlex |
| PubMed, Europe PMC | fachlich eng (Medizin, Biologie); für andere Fächer ohne Gewinn |
| arXiv | Preprints weniger Fächer |
| Semantic Scholar | als eigener Dienst überschneidend; wertvoll nur als Teil eines semantischen Zweitwegs |
| arXiv | von OpenAlex mitindexiert und fachlich eng – für Umwelt-, Rechts- und Planungsfragen ohne Wert |
| PubMed als eigener Dienst | für Entdeckung durch einen semantischen Zweitweg mitabgedeckt; eigener Wert nur bei medizin-, toxikologie- oder zoonosennahen Fragen |

Ein Verlagskorpus wie Scholar Gateway ist kein Ersatz für OpenAlex: er liefert Volltextpassagen und einen Rücknahmehinweis, aber keine Zitationsdaten und keine Vollabdeckung. Als Ergänzung für Volltextlesen sinnvoll, als Grundlage nicht.

## Was nicht genutzt wird

Dienste, die Volltexte aus Schattenbibliotheken beziehen oder solche Spiegel als Rückfallebene verwenden, werden nicht eingebunden und nicht abgefragt – auch dann nicht, wenn sie daneben legale Quellen anbieten. Begründung: Verbreitung ohne Lizenz, und in einem Gutachten ist die Herkunft einer so beschafften Quelle nicht darstellbar.

Statt dessen der reguläre Weg: freier Fundort über OpenAlex, Repositoriumsfassung, Fernleihe und Dokumentlieferung der zuständigen Landes- oder Universitätsbibliothek, oder eine Anfrage bei den Autoren.

## Einbindungswege

Welcher Weg möglich ist, hängt davon ab, wie ein Server betrieben wird:

| Betriebsart | In einer Chat-Sitzung nutzbar? |
|---|---|
| entfernter Dienst mit HTTPS-Endpunkt | ja – als eigener Connector mit der URL eintragen |
| lokal gestarteter Server (Standardeingabe/-ausgabe) | nein – braucht einen entfernt erreichbaren Betrieb |
| über einen Hosting- oder Gateway-Dienst bereitgestellt | ja – der Dienst stellt einen HTTPS-Endpunkt bereit |

Daraus folgt die Reihenfolge beim Ausbau: zuerst Dienste nehmen, die schon einen Endpunkt haben; erst danach solche, die erst betrieben werden müssen.

Ein Hinweis zu Katalogservern: Die mitgelieferten Serverlisten enthalten häufig die Deutsche Nationalbibliothek, aber nicht die regionalen Verbundkataloge. Den fachlich wichtigeren Verbundkatalog nachzutragen setzt Zugriff auf die Konfiguration voraus – also eigenen Betrieb, nicht eine Ein-Klick-Installation. Das ist beim Abwägen des Aufwands zu berücksichtigen.
