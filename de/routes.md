---
lang: de

table_data:
  - field_name: agency_id
    recommendations:
      - ID: 1
        tags: ['trip-planners', 'timetables']
        text: |
          Muss enthalten sein, wenn es in der `agency.txt` definiert.
  - field_name: route_short_name
    recommendations:
      - ID: 2
        tags: []
        text: |
          `route_short_name` wenn eine kurze Dienstbezeichnung vorhanden ist. Dies sollte der allgemein bekannte Passagiername des Dienstes sein, der nicht länger als 12 Zeichen sein darf.
  - field_name: route_long_name
    recommendations:
      - ID: 3
        tags: []
        text: |
          Die Definition aus der Spezifikationsreferenz:

          <q>Dieser Name ist in der Regel route_short_name als <code>route_short_name</code> und enthält häufig das Ziel oder den Stopp der Route. Mindestens einer von <code>route_short_name</code> oder <code>route_long_name</code> muss angegeben werden, oder möglicherweise beide, falls zutreffend. Wenn die Route keinen langen Namen hat, geben Sie einen <code>route_short_name</code> und verwenden Sie eine leere Zeichenfolge als Wert für dieses Feld</q>

          Beispiele für Typen von langen Namen finden Sie unten:
        example_table: |
          <table class='example'>
            <thead>
              <tr>
                <th colspan='3'>Primary Travel Path or Corridor</th>
              </tr>
              <tr>
                <th>Name der Route</th>
                <th>Form</th>
                <th>Agentur</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td><a href='https://www.sfmta.com/getting-around/transit/routes-stops/n-judah'>“N”/“Judah”</a></td>
                <td><code>route_short_name</code>/<br><code>route_long_name</code></td>
                <td><a href='https://www.sfmta.com/'>Muni</a>, in San Francisco</td>
              </tr>
              <tr>
                <td><a href='https://trimet.org/schedules/r006.htm'>“6“/“ML King Jr Blvd“</a></td>
                <td><code>route_short_name</code>/<br><code>route_long_name</code></td>
                <td><a href='https://trimet.org/'>TriMet</a>, in Portland, Or.</td>
              </tr>
              <tr>
                <td><a href='http://www.ratp.fr/informer/pdf/orienter/f_plan.php?nompdf=m6'>“6”/“Nation - Étoile”</a></td>
                <td><code>route_short_name</code>/<br><code>route_long_name</code></td>
                <td><a href='http://www.ratp.fr/'>RATP</a>, in Paris Frankreich.</td>
              </tr>
              <tr>
                <td><a href='http://www.bvg.de/images/content/linienverlaeufe/LinienverlaufU2.pdf'>“U2”-“Pankow – Ruhleben”</a></td>
                <td><code>route_short_name</code>-<br><code>route_long_name</code></td>
                <td><a href='http://www.bvg.de/'>BVG</a>, in Berlin, Deutschland</td>
              </tr>
            </tbody>
          </table>

          <table class='example'>
            <thead>
              <tr>
                <th>Beschreibung des Service</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td><a href='https://128bc.org/schedules/rev-bus-hartwell-area/'>“Hartwell Area Shuttle“</a></td>
              </tr>
            </tbody>
          </table>
      - ID: 4
        tags: []
        text: |
          `route_long_name` sollte den `route_short_name` nicht enthalten.
      - ID: 5
        tags: []
        text: |
          Fügen Sie beim Ausfüllen von `route_long_name` die vollständige Bezeichnung einschließlich einer Service-ID hinzu.
          Beispiele:
        example_table: |
          <table class='example'>
            <thead>
              <tr>
                <th>Service Identity</th>
                <th>Empfehlung</th>
                <th>Beispiele</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>"MAX Light Rail"<br>TriMet, in Portland, Oregon</td>
                <td>Der <code>route_long_name</code> sollte die Marke (MAX) und die spezifische Routenbezeichnung enthalten</td>
                <td>"MAX Red Line" "MAX Blue Line"</td>
              </tr>
              <tr>
                <td>"Rapid Ride"<br>ABQ Ride, in Albuquerque, New Mexico</td>
                <td>Der <code>route_long_name</code> sollte die Marke (Rapid Ride) und die spezifische Routenbezeichnung enthalten</td>
                <td>"Rapid Ride Red Line"<br>"Rapid Ride Blue Line"</td>
              </tr>
            </tbody>
          </table>
  - field_name: route_id
    recommendations:
      - ID: 6
        tags: []
        text: |
          Alle Reisen auf einer bestimmten benannten Route sollten auf dieselbe `route_id`.

          * Verschiedene Richtungen einer Route sollten nicht in verschiedene `route_id` Werte unterteilt werden.
          * Verschiedene Betriebsbereiche einer Route sollten nicht in verschiedene `route_id` Werte unterteilt werden. dh Erstellen Sie keine unterschiedlichen Datensätze in `routes.txt` für "Downtown AM" und "Downtown PM" -Dienste.

      - ID: 7
        tags: []
        text: |
          Wenn eine Route Gruppe deutlich benannte Zweige (zB 1A und 1B) enthält, folgen Empfehlungen in der Routen [Zweige](/best-practices/#branches) Fall zu bestimmen `route_short_name` und `route_long_name`.
  - field_name: route_color & route_text_color
    recommendations:
      - ID: 8
        tags: []
        text: |
          Sollte konsistent sein mit Beschilderung und gedruckten und Online-Kundeninformationen (und somit nicht enthalten, wenn sie an anderen Orten nicht existieren).
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
