---
table_data:
  - field_name: agency_id
    recommendations:
      - number: 1
        tags: ['trip-planners', 'timetables']
        text: "Must be included if it is defined in <code>agency.txt</code>. <!-- (68) -->"
  - field_name: route_short_name
    recommendations:
      - number: 2
        tags: []
        text: "Include <code>route_short_name</code> if there is a brief service designation. This should be the commonly-known passenger name of the service, no longer than 12 characters. <!-- (71) -->"
  - field_name: route_long_name
    recommendations:
      - number: 3
        tags: []
        text: "The definition from Specification reference:

        <q>This name is generally more descriptive than the <code>route_short_name</code> and will often include the route's destination or stop. At least one of <code>route_short_name</code> or <code>route_long_name</code> must be specified, or potentially both if appropriate. If the route does not have a long name, please specify a <code>route_short_name</code> and use an empty string as the value for this field.</q>

        Examples of types of long names are below:  <!-- (73) -->

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
                <td><a href='http://128bc.org/rev-hartwell-area-shuttle/'>“Hartwell Area Shuttle“</a></td>
              </tr>
            </tbody>
          </table>"
---
### routes.txt {#routes}

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
    <tr id="{{ field.field_name }}_{{ recommendation.number }}" class="anchor-row {% for tag in recommendation.tags %}{{ tag }} {% endfor %}">
      <td>{% if forloop.first %}<code>{{ field.field_name }}</code>{% endif %}</td>
      <td>{{ recommendation.number }}</td>
      <td>{{ recommendation.text }}</td>
    </tr>
      {% endfor %}
    {% endfor %}
  </tbody>
</table>

<table class="recommendation">
  <thead>
    <tr>
      <th>Field Name</th>
      <th>Tags</th>
      <th>#</th>
      <th>Recommendation</th>
    </tr>
  </thead>
  <tbody>
    <tr id="routes_1" class="anchor-row">
      <td><code>agency_id</code></td>
      <td>
        <span class="tag trip-planners"></span>
        <span class="tag timetables"></span>
      </td>
      <td>1</td>
      <td>Must be included if it is defined in <code>agency.txt</code>. <!-- (68) --></td>
    </tr>
    <tr id="routes_2" class="anchor-row field-row">
      <td><code>route_short_name</code></td>
      <td></td>
      <td>2</td>
      <td>Include <code>route_short_name</code> if there is a brief service designation. This should be the commonly-known passenger name of the service, no longer than 12 characters. <!-- (71) --></td>
    </tr>
    <tr id="routes_3" class="anchor-row field-row">
      <td rowspan="3"><code>route_long_name</code></td>
      <td></td>
      <td>3</td>
      <td>The definition from Specification reference:

      <q>This name is generally more descriptive than the <code>route_short_name</code> and will often include the route's destination or stop. At least one of <code>route_short_name</code> or <code>route_long_name</code> must be specified, or potentially both if appropriate. If the route does not have a long name, please specify a <code>route_short_name</code> and use an empty string as the value for this field.</q>

      Examples of types of long names are below:  <!-- (73) -->

        <table class="example">
          <thead>
            <tr>
              <th colspan="3">Primary Travel Path or Corridor</th>
            </tr>
            <tr>
              <th>Route Name</th>
              <th>Form</th>
              <th>Agency</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><a href="https://www.sfmta.com/getting-around/transit/routes-stops/n-judah">“N”/“Judah”</a></td>
              <td><code>route_short_name</code>/<br><code>route_long_name</code></td>
              <td><a href="https://www.sfmta.com/">Muni</a>, in San Francisco</td>
            </tr>
            <tr>
              <td><a href="https://trimet.org/schedules/r006.htm">"6"/"ML King Jr Blvd"</a></td>
              <td><code>route_short_name</code>/<br><code>route_long_name</code></td>
              <td><a href="https://trimet.org/">TriMet</a>, in Portland, Or.</td>
            </tr>
            <tr>
              <td><a href="http://www.ratp.fr/informer/pdf/orienter/f_plan.php?nompdf=m6">“6”/“Nation - Étoile”</a></td>
              <td><code>route_short_name</code>/<br><code>route_long_name</code></td>
              <td><a href="http://www.ratp.fr/">RATP</a>, in Paris France.</td>
            </tr>
            <tr>
              <td><a href="http://www.bvg.de/images/content/linienverlaeufe/LinienverlaufU2.pdf">“U2”-“Pankow – Ruhleben”</a></td>
              <td><code>route_short_name</code>-<br><code>route_long_name</code></td>
              <td><a href="http://www.bvg.de/">BVG</a>, in Berlin, Germany</td>
            </tr>
          </tbody>
        </table>

        <table class="example">
          <thead>
            <tr>
              <th>Description of the Service</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><a href="http://128bc.org/rev-hartwell-area-shuttle/">"Hartwell Area Shuttle"</a></td>
            </tr>
          </tbody>
        </table>
      </td>
    </tr>
    <tr id="routes_4" class="anchor-row">
      <td></td>
      <td>4</td>
      <td><code>route_long_name</code> should not contain the <code>route_short_name</code>. <!-- (72) --></td>
    </tr>
    <tr id="routes_5" class="anchor-row">
      <td></td>
      <td>5</td>
      <td>
      Include the full designation including a service identity when populating <code>route_long_name</code>. <!-- (69) -->

      Examples:

        <table class="example">
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
              <td>"MAX Red Line"<br>"MAX Blue Line"</td>
            </tr>
            <tr>
              <td>"Rapid Ride"<br>ABQ Ride, in Albuquerque, New Mexico</td>
              <td>The <code>route_long_name</code> should include the brand (Rapid Ride) and the specific route designation</td>
              <td>"Rapid Ride Red Line"<br>"Rapid Ride Blue Line"</td>
            </tr>
          </tbody>
        </table>

      </td>      
    </tr>
    <tr id="routes_6" class="anchor-row field-row">
      <td rowspan="2"><code>route_id</code></td>
      <td></td>
      <td>6</td>
      <td>All trips on a given named route should reference the same <code>route_id</code>. <!-- (74) -->
        <ul>
          <li>Different directions of a route should not be separated into different <code>route_id</code> values.</li>
          <li>Different spans of operation of a route should not be separated into different <code>route_id</code> values. i.e. do not create different records in <code>routes.txt</code> for “Downtown AM” and “Downtown PM” services).</li>
        </ul>
      </td>
    </tr>
    <tr id="routes_7" class="anchor-row">
      <td></td>
      <td>7</td>
      <td>If a route group includes distinctly named branches (e.g. 1A and 1B), follow recommendations in the route <a href="#branches">branches</a> case to determine <code>route_short_name</code> and <code>route_long_name</code>. <!-- (70) --></td>
    </tr>
    <tr id="routes_8" class="anchor-row field-row">
      <td><code>route_color</code> & <code>route_text_color</code></td>
      <td></td>
      <td>8</td>
      <td>Should be consistent with signage and printed and online customer information (and thus not included if they do not exist in other places).  <!-- (76) --></td>
    </tr>
  </tbody>
</table>
