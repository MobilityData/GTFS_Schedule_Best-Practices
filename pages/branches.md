---
table_data:
  - field_name: "All Fields"
    recommendations:
      - ID: 1
        tags: []
        text: "In naming branch routes, it is recommended to follow other passenger information materials. Below are descriptions and examples of two cases: <!-- (97) -->"
      - ID: 1A
        tags: []
        text: "If timetables and on-street signage represent two distinctly named routes (e.g. 1A and 1B), then present this as such in the GTFS, using the `route_short_name` and/or `route_long_name` fields. <!-- (97A) -->

        Example: [GoDurham Transit routes 2, 2A, and 2B](/best-practices/branch-example-godurham) demonstrate branched routes with deviations and extensions."
      - ID: 1B
        tags: []
        text: "If agency-provided information describes branches as the same named route, then utilize the `trips.trip_headsign`, `stop_times.stop_headsign`, and/or `trips.trip_short_name` fields. <!-- (97B) -->

        Example: GoTriangle [route 300](http://admin.gotransitnc.org/sites/default/files/maps-and-schedules/gotriangle/RoutesAndSchedules-1561.pdf) travels to different locations depending on the time of day. During peak commuter hours extra legs are added onto the standard route to accommodate workers entering and leaving the city."
---
### Branches

Some routes may include branches. Alignment and stops are shared amongst these branches, but each also serves distinct stops and alignment sections. The relationship among branches may be indicated by route name(s), headsigns, and trip short name using the further guidelines below.

<figure id="branching-fig">
<figcaption>Below: Three potential configurations of route branches. Primary alignment is in black. Branch is colored gold.</figcaption>
  <img src="{{ "/best-practices/images/branching.svg" | prepend: site.baseurl }}" alt="Configurations of Route Branches">
</figure>

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
      <td>{{ recommendation.ID }}</td>
      <td>{{ recommendation.text | markdownify }}{{ recommendation.example_table }}</td>
    </tr>
      {% endfor %}
    {% endfor %}
  </tbody>
</table>
