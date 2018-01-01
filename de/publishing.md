---
lang: de

table_data:
  - field_name: allgemein
    recommendations:
      - ID: 1
        tags: []
        text: |
          Datasets sollten unter einer öffentlichen, permanenten URL einschließlich des ZIP-Dateinamens veröffentlicht werden. (zB www.agency.org/gtfs/gtfs.zip). Idealerweise sollte die URL direkt heruntergeladen werden können, ohne dass ein Login für den Zugriff auf die Datei erforderlich ist, um den Download durch den Konsum von Softwareanwendungen zu erleichtern.FORMAT_PLACEHOLDER_1 Während es empfohlen wird (und die gebräuchlichste Vorgehensweise), ein GTFS-Dataset offen herunterladbar zu machen, wird empfohlen, den Zugriff auf das GTFS-Dataset über API-Schlüssel zu steuern, wenn ein Datenanbieter den Zugriff auf GTFS aus Lizenzgründen oder aus anderen Gründen kontrollieren muss, die automatische Downloads erleichtern.
      - ID: 2
        tags: []
        text: |
          GTFS-Daten werden in Iterationen veröffentlicht, so dass eine einzelne Datei an einem stabilen Standort immer die neueste offizielle Beschreibung des Dienstes für eine Transitagentur (oder Agenturen) enthält.
      - ID: 3
        tags: []
        text: |
          Pflegen Sie nach stop_id persistente Identifikatoren (ID-Felder) für `stop_id`, `route_id` und `agency_id` über `agency_id` hinweg.
      - ID: 4
        tags: []
        text: |
          Ein GTFS-Dataset sollte den aktuellen und den nächsten Service enthalten (manchmal als "fusionierter" Dataset bezeichnet). Die [Merge-Funktion](https://github.com/google/transitfeed/wiki/Merge) des Google Transitfeed-Tools kann zum Erstellen eines zusammengeführten Datensatzes aus zwei verschiedenen GTFS-Feeds verwendet werden.

          * Der veröffentlichte GTFS-Datensatz sollte zu jedem Zeitpunkt mindestens für die nächsten 7 Tage gültig sein, und zwar idealerweise so lange, wie der Betreiber davon überzeugt ist, dass der Zeitplan weiterhin eingehalten wird.
          * Wenn möglich, sollte der GTFS-Datensatz mindestens die nächsten 30 Diensttage umfassen.

      - ID: 5
        tags: []
        text: |
          Entfernen Sie alte Dienste (abgelaufene Kalender) aus dem Feed.
      - ID: 6
        tags: []
        text: |
          Wenn eine Serviceänderung innerhalb von 7 Tagen oder weniger wirksam wird, sollten Sie diese Serviceänderung anstelle eines statischen GTFS-Datasets durch einen [GTFS-Realtime-Feed](https://developers.google.com/transit/gtfs-realtime/) (Service Advisories oder Trip Updates) ausdrücken.
      - ID: 7
        tags: []
        text: |
          Der Web-Server, der GTFS-Daten hostet, sollte so konfiguriert sein, dass er das Datum der Dateiänderung korrekt meldet (siehe [HTTP / 1.1 - Request for Comments 2616](https://tools.ietf.org/html/rfc2616#section-14.29), unter Abschnitt 14.29).
---

## Datensatzveröffentlichung und allgemeine Verfahren {#publishing}

<div class="table-wrapper">
  <table class="recommendation">
    <thead>
      <tr>
        <th>Field Name</th>
        <th>ID</th>
        <th>Recommendation</th>
      </tr>
    </thead>
    <tbody>
    {% for field in page.table_data %}
      {% for recommendation in field.recommendations %}
      <tr id="{{ page.slug }}_{{ recommendation.ID }}" class="anchor-row{% if forloop.first %} field-row{% endif %}{% for tag in recommendation.tags %} {{ tag }}{% endfor %}">
        <td>{% if forloop.first %}<code>{{ field.field_name }}</code>{% endif %}</td>
        <td><div class="anchor-node"><p>{{ recommendation.ID }}</p><a class="anchor-link" href="#{{ page.slug }}_{{ recommendation.ID }}"><i class="fa fa-link" aria-hidden="true"></i></a></div></td>
        <td>{{ recommendation.text | markdownify }}{% if recommendation.example_table %}<div class="table-wrapper">{{ recommendation.example_table }}</div>{% endif %}</td>
      </tr>
      {% endfor %}
    {% endfor %}
    </tbody>
  </table>
</div>
