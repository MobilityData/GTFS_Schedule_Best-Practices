---
lang: en

table_data:
  - field_name: agency_id
    recommendations:
      - ID: 1
        tags: ['trip-planners', 'timetables']
        text: |
          Must be included if it is defined in `agency.txt`. <!-- (68) -->
  - field_name: route_short_name
    recommendations:
      - ID: 2
        tags: []
        text: |
          Include `route_short_name` if there is a brief service designation. This should be the commonly-known passenger name of the service, no longer than 12 characters. <!-- (71) -->
  - field_name: route_long_name
    recommendations:
      - ID: 3
        tags: []
        text: |
          The definition from Specification reference:

          <q>This name is generally more descriptive than the <code>route_short_name</code> and will often include the route's destination or stop. At least one of <code>route_short_name</code> or <code>route_long_name</code> must be specified, or potentially both if appropriate. If the route does not have a long name, please specify a <code>route_short_name</code> and use an empty string as the value for this field.</q>

          Examples of types of long names are below:  <!-- (73) -->
        example_table: |
          <table class='example'>
            <thead>
              <tr>
                <th colspan='3'>Primary Travel Path or Corridor</th>
              </tr>
              <tr>
                <th>Route Name</th>
                <th>Form</th>
                <th>Agency</th>
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
                <td><a href='http://www.ratp.fr/'>RATP</a>, in Paris France.</td>
              </tr>
              <tr>
                <td><a href='http://www.bvg.de/images/content/linienverlaeufe/LinienverlaufU2.pdf'>“U2”-“Pankow – Ruhleben”</a></td>
                <td><code>route_short_name</code>-<br><code>route_long_name</code></td>
                <td><a href='http://www.bvg.de/'>BVG</a>, in Berlin, Germany</td>
              </tr>
            </tbody>
          </table>

          <table class='example'>
            <thead>
              <tr>
                <th>Description of the Service</th>
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
          `route_long_name` should not contain the `route_short_name`. <!-- (72) -->
      - ID: 5
        tags: []
        text: |
          Include the full designation including a service identity when populating `route_long_name`. <!-- (69) -->
          Examples:
        example_table: |
          <table class='example'>
            <thead>
              <tr>
                <th>Service Identity</th>
                <th>Recommendation</th>
                <th>Examples</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>"MAX Light Rail"<br>TriMet, in Portland, Oregon</td>
                <td>The <code>route_long_name</code> should include the brand (MAX) and the specific route designation</td>
                <td>"MAX Red Line" "MAX Blue Line"</td>
              </tr>
              <tr>
                <td>"Rapid Ride"<br>ABQ Ride, in Albuquerque, New Mexico</td>
                <td>The <code>route_long_name</code> should include the brand (Rapid Ride) and the specific route designation</td>
                <td>"Rapid Ride Red Line"<br>"Rapid Ride Blue Line"</td>
              </tr>
            </tbody>
          </table>
  - field_name: route_id
    recommendations:
      - ID: 6
        tags: []
        text: |
          All trips on a given named route should reference the same `route_id`. <!-- (74) -->

          * Different directions of a route should not be separated into different `route_id` values.
          * Different spans of operation of a route should not be separated into different `route_id` values. i.e. do not create different records in `routes.txt` for “Downtown AM” and “Downtown PM” services).
      - ID: 7
        tags: []
        text: |
          If a route group includes distinctly named branches (e.g. 1A and 1B), follow recommendations in the route [branches](/best-practices/#branches) case to determine `route_short_name` and `route_long_name`. <!-- (70) -->
  - field_name: route_color & route_text_color
    recommendations:
      - ID: 8
        tags: []
        text: |
          Should be consistent with signage and printed and online customer information (and thus not included if they do not exist in other places).  <!-- (76) -->
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
