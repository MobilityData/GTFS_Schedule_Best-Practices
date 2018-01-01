---
lang: de

---
# GTFS Data Best Practices

## Einführung {#introduction}

Dies sind empfohlene Vorgehensweisen zur Beschreibung öffentlicher Verkehrsdienste in das [General Transit Feed Specification (GTFS)](http://gtfs.org) . Diese Praktiken wurden aus der Erfahrung der Mitglieder der [GTFS Best Practices Arbeitsgruppe](#working-group) und [anwendungsspezifischen GTFS-Praxisempfehlungen zusammengestellt](http://www.transitwiki.org/TransitWiki/index.php/Best_practices_for_creating_GTFS). Weitere Hintergrundinformationen finden Sie in den [häufig gestellten Fragen](/best-practices/faq) .

### Verknüpfung mit diesem Dokument {#linking}

Bitte verlinken Sie hier, um den Futtermittelproduzenten Hinweise für die korrekte Erstellung von GTFS-Daten zu geben. Jede einzelne Empfehlung hat einen Ankerlink. Klicken Sie auf die Empfehlung, um die URL für den In-Page-Ankerlink zu erhalten.

Wenn eine GTFS-konsumierende Anwendung Anforderungen oder Empfehlungen für GTFS-Datenpraktiken stellt, die hier nicht beschrieben werden, wird empfohlen, ein Dokument mit diesen Anforderungen oder Empfehlungen zu veröffentlichen, um diese gemeinsamen Best Practices zu ergänzen.

### Dokumentstruktur {#document-structure}

Empfohlene Praktiken sind in drei primäre Abschnitte unterteilt

* __[Datensatzveröffentlichung und allgemeine Vorgehensweise](#publishing):__ Diese Praktiken beziehen sich auf die Gesamtstruktur des GTFS-Datasets und auf die Art und Weise, in der GTFS-Datasets veröffentlicht werden.
* __[Praxisempfehlungen Organisiert nach Datei](#by-file):__ Empfehlungen werden nach Datei und Feld in der GTFS organisiert, um die Zuordnungspraxis zurück zur offiziellen GTFS-Referenz zu erleichtern.
* __[Praxisempfehlungen Organisiert von Case](#by-case):__ In bestimmten Fällen, wie Loop-Routen, müssen Praktiken möglicherweise über mehrere Dateien und Felder angewendet werden. Solche Empfehlungen werden in diesem Abschnitt zusammengefasst.

### System Tags {#system-tags}

Das System Tags-Menü enthält vier verschiedene Tags, die jeweils einer Beschreibung entsprechen. Wenn Sie eines dieser Tags auswählen, werden alle zutreffenden Empfehlungen hervorgehoben.

<hr/>

<button class="system-tag-button trip-planners" data-target="trip-planners">Trip Planners</button>

Diese Verfahren verbessern die Kundenerfahrung in Anwendungen wie Google Maps, die für die Reiseplanung verwendet werden.

<hr/>

<button class="system-tag-button human-readability" data-target="human-readability">Human Readability</button>

Diese Praktiken tragen dazu bei, dass ein menschlicher Leser die GIFS-Dateien entpacken und untersuchen kann.

<hr/>

<button class="system-tag-button arrival-predictions" data-target="arrival-predictions">Arrival Predictions</button>

Diese Verfahren ermöglichen es der Ankunftsvorhersage-Software, Echtzeit-Ankunftsschätzungen in Bezug auf die Zeitpläne in [`trips.txt`](#trips) und [`stop_times.txt`](#stop_times).

<hr/>

<button class="system-tag-button timetables" data-target="timetables">Timetables</button>

Diese Verfahren unterstützen die Erstellung von HTML-Zeitplänen auf der Grundlage von GTFS, z. B. mit der GTFS-to-HTML-Software.
