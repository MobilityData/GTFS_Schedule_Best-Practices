---
table_data:
  - field_name: trip_headsign
    recommendations:
      - ID: 1
        tags: ['trip-planners']
        text: |
          Do not provide route names (matching `route_short_name` and `route_long_name`) in the `trip_headsign` or `stop_headsign` fields. <!-- (98) -->
      - ID: 2
        tags: ['trip-planners']
        text: |
          Should contain destination, direction, and/or other trip designation text shown on the headsign of the vehicle which may be used to distinguish amongst trips in a route. Consistency with direction information shown on the vehicle is the primary and overriding goal for determining headsigns supplied in GTFS datasets. Other information should be included only if it does not compromise this primary goal. If headsigns change during a trip, override `trip_headsign` with `stop_times.stop_headsign`.

          Below are recommendations for some possible cases. <!-- (58) -->
        example_table: |
          <table class="example">
            <thead>
              <tr>
                <th>Route Description</th>
                <th>Recommendation</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>2A. Destination-only</td>
                <td>Provide the terminus destination. e.g. "Transit Center", “Portland City Center”, or “Jantzen Beach” <!-- (58A) --> </td>
              </tr>
              <tr>
                <td>2B. Destinations with waypoints</td>
                <td>&lt;destination&gt; via &lt;waypoint&gt; “Highgate via Charing Cross”. If waypoint(s) are removed from the headsign show to passengers after the vehicle passes those waypoints, use <code>stop_times.stop_headsign</code> to set an updated headsign. <!-- (58B) --> </td>
              </tr>
              <tr>
                <td>2C. Regional placename with local stops</td>
                <td>If there will be multiple stops inside the city or borough of destination, use <code>stop_times.stop_headsign</code> once reaching the destination city. <!-- (58C) --> </td>
              </tr>
              <tr>
                <td>2D. Direction-only</td>
                <td>Indicate using terms such as “Northbound”, “Inbound”, “Clockwise,” or similar directions. <!-- (58D) --></td>
              </tr>
              <tr>
                <td>2E. Direction with destination</td>
                <td>&lt;direction&gt; to &lt;terminus name&gt; e.g. “Southbound to San Jose” <!-- (58E) --></td>
              </tr>
              <tr>
                <td>2F. Direction with destination and waypoints</td>
                <td>&lt;direction&gt; via &lt;waypoint&gt; to &lt;destination&gt; (“Northbound via Charing Cross to Highgate”). <!-- (58F) --></td>
              </tr>
            </tbody>
          </table>
      - ID: 3
        tags: ['trip-planners']
        text: |
          Do not begin a headsign with the words “To” or “Towards”.
  - field_name: direction_id
    recommendations:
      - ID: 4
        tags: ['trip-planners','timetables','human-readability']
        text: |
          If trips on a route service opposite directions, distinguish these groups of trips with the `direction_id` field, using values 0 and 1. <!-- (64) -->
      - ID: 5
        tags: ['trip-planners','timetables','human-readability']
        text: |
          Use values 0 and 1 consistently throughout the dataset. i.e. <!-- (65) -->

          * If 1 = Outbound on the Red route, then 1 = Outbound on the Green route
          * If 1 = Northbound on Route X, then 1 = Northbound on Route Y
          * If 1 = clockwise on Route X then 1 = clockwise on Route Y
---

* __See special case for loop routes:__ Loop routes are cases where trips start and end at the same stop, as opposed to linear routes, which have two distinct termini. Loop routes must be described following specific practices. [See Loop route case.](/best-practices/#loop-routes)
* __See special case for lasso routes:__ Lasso routes are a hybrid of linear and loop geometries, in which vehicles travel on a loop for only a portion of the route. Lasso routes must be described following specific practices. [See Lasso route case.](/best-practices/#lasso-routes)

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
