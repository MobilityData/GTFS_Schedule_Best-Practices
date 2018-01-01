---
lang: de

table_data:
  - field_name: stop_id
    recommendations:
      - ID: 1
        tags: ['trip-planners', 'arrival-predictions']
        text: |
          Stopps, die sich an verschiedenen physischen Orten befinden (dh verschiedene festgelegte genaue Orte für Fahrzeuge auf ausgewiesenen Routen zum Anhalten, möglicherweise gekennzeichnet durch Schilder, Unterstände oder andere derartige öffentliche Informationen, an verschiedenen Straßenecken gelegen oder verschiedene Einsteigeeinrichtungen wie eine Plattform oder Bus Bay, auch wenn in der Nähe zueinander) sollte unterschiedliche `stop_id`.
      - ID: 2
        tags: ['trip-planners', 'arrival-predictions']
        text: |
          `stop_id` ist eine interne ID, die den Passagieren nicht angezeigt werden soll.
      - ID: 3
        tags: ['trip-planners', 'arrival-predictions']
        text: |
          Pflegen Sie konsistente `stop_id` für die gleichen Stopps über stop_id (siehe [Dataset Publishing & General Practices](#publishing)).
  - field_name: stop_name
    recommendations:
      - ID: 4
        tags: ['trip-planners','timetables','human-readability']
        text: |
          Der `stop_name` sollte mit dem öffentlichen Namen der Agentur für die Haltestelle, den Bahnhof oder das Internat übereinstimmen, z. B. was in einem Stundenplan gedruckt, online veröffentlicht und / oder am Standort präsentiert wird.
      - ID: 5
        tags: ['trip-planners','timetables','human-readability']
        text: |
          Wenn kein veröffentlichter Stoppname vorhanden ist, befolgen Sie im gesamten Feed konsistente Stoppbenennungskonventionen.
      - ID: 6
        tags: ['trip-planners','timetables','human-readability']
        text: |
          Vermeiden Sie die Verwendung von Abkürzungen außer für Orte, die am häufigsten mit einem abgekürzten Namen bezeichnet werden. Siehe Abkürzungen (# 2) unter [Alle Dateien](#all-files).
      - ID: 7
        tags: ['trip-planners','timetables','human-readability']
        text: |
          Geben Sie Stoppnamen in gemischter Groß- / Kleinschreibung gemäß lokaler Konventionen gemäß der Empfehlung für alle kundenorientierten Textfelder an.
      - ID: 8
        tags: ['trip-planners','timetables','human-readability']
        text: |
          Standardmäßig sollte `stop_name` keine generischen oder redundanten Wörter wie "Station" oder "Stop" enthalten, aber einige stop_name sind zulässig.

          * Wenn es tatsächlich Teil des Namens ist (Union Station, Central Station)
          * Wenn der `stop_name` zu allgemein ist (z. B. wenn es der Name der Stadt ist). "Station", "Terminal" oder andere Wörter machen die Bedeutung klar.
  - field_name: stop_lat & stop_lon
    recommendations:
      - ID: 9
        tags: ['trip-planners']
        text: |
          Stopporte sollten so genau wie möglich sein. Stopporte sollten einen Fehler von __nicht mehr__ als vier Metern im Vergleich zur tatsächlichen Stopposition haben.
      - ID: 10
        tags: ['trip-planners']
        text: |
          Halteorte sollten sehr nahe an der Fußgänger-Vorfahrtsstraße platziert werden, an der ein Fahrgast einsteigen wird (dh die richtige Straßenseite).
      - ID: 11
        tags: ['trip-planners']
        text: |
          Wenn ein Stopp-Ort über separate Daten-Feeds verteilt ist (dh zwei Agenturen verwenden genau die gleiche Stopp- / Einstiegs-Einrichtung), geben Sie an, dass der Stopp geteilt wird, indem für beide Stopps genau die selbe `stop_lat` und `stop_lon`.
  - field_name: stop_code
    recommendations:
      - ID: 12
        tags: []
        text: |
          `stop_code` sollte in GTFS enthalten sein, wenn Fahrgast-Stopp-Nummern oder kurze Kennungen vorhanden sind.
  - field_name: parent_station & location_type
    recommendations:
      - ID: 13
        tags: ['trip-planners','arrival-predictions','timetables']
        text: |
          Viele Bahnhöfe oder Terminals verfügen über mehrere Einsteigeeinrichtungen (je nach Modus können sie Busbahn, Bahnsteig, Werft, Tor oder eine andere Bezeichnung genannt werden). In solchen Fällen sollten Futtermittelproduzenten Stationen, Einstiegseinrichtungen (auch als Kinderstopps bezeichnet) und ihre Beziehung beschreiben.

          * Die Station oder das Terminal sollte in `stops.txt` mit `location_type = 1` als Datensatz definiert werden.
          * Jede Verschachtelung sollte als Haltestelle mit `location_type = 0`. Das Feld `parent_station` sollte auf die `stop_id` der Station `stop_id` in der sich die Einsteigeeinrichtung befindet.
      - ID: 14
        tags: ['trip-planners','arrival-predictions','timetables']
        text: |
          Wenn Sie die Station und das Kind benennen, geben Sie die Namen an, die von den Fahrern gut erkannt werden, und können den Fahrern helfen, den Bahnhof und das Boarding (Bus, Plattform, Kai, Tor usw.) zu identifizieren. 
        example_table: |
          <table class='example'>
            <thead>
              <tr>
                <th>Parent Station Name</th>
                <th>Child Stop Name</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Chicago Union Station</td>
                <td>Chicago Union Station Platform 19</td>
              </tr>
              <tr>
                <td>San Francisco Ferry Building Terminal</td>
                <td>San Francisco Ferry Building Terminal Gate E</td>
              </tr>
              <tr>
                <td>Downtown Transit Center</td>
                <td>Downtown Transit Center Bay B</td>
              </tr>
            </tbody>
          </table>

---
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