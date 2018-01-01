---
lang: de

table_data:
  - field_name: pickup_type & drop_off_type
    recommendations:
      - ID: 1
        tags: []
        text: |
          Non-revenue (deadhead) trips that do not provide passenger service should be marked with `pickup_type` and `drop_off_type` value of `1` for all `stop_times` rows.<!-- (13) -->
      - ID: 2
        tags: []
        text: |
          On revenue trips, internal “timing points” for monitoring operational performance and other places such as garages that a passenger cannot board should be marked with `pickup_type = 1` (no pickup available) and `drop_off_type = 1` (no drop off available). <!-- (46) -->
  - field_name: timepoint
    recommendations:
      - ID: 3
        tags: []
        text: |
          The `timepoint` field should be provided. It specifies which `stop_times` the operator will attempt to strictly adhere to (`timepoint=1`), and that other stop times are estimates (`timepoint=0`).<!-- (44) -->
  - field_name: arrival_time & departure_time
    recommendations:
      - ID: 4
        tags: ['trip-planners','arrival-predictions']
        text: |
          `arrival_time` and `departure_time` fields should specify time values whenever possible, including non-binding estimated or interpolated times between timepoints. <!-- (45) -->
  - field_name: stop_headsign
    recommendations:
      - ID: 5
        tags: ['trip-planners']
        text: |
          `stop_headsign` values override the `trip_headsign` (in `trips.txt`). `stop_headsign` values should be provided when the text displayed on the headsign changes during a trip. `stop_headsign` values do not “carry down” to subsequent stops, and therefore values must be repeated if the stop headsign remains the same. In general, headsign values should also correspond to signs in the stations. <!-- (47) -->

          In the cases below, “Southbound” would mislead customers because it is not used in the station signs.
        example_table: |
          <table class="example">
            <thead>
              <tr>
                <th colspan="2">In NYC, for the 2 going Southbound:</th>
              </tr>
              <tr>
                <th>For <code>stop_times.txt</code> rows:</th>
                <th>Use <code>stop_headsign</code> value:</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Until Manhattan is Reached</td>
                <td><code>Manhattan & Brooklyn</code></td>
              </tr>
              <tr>
                <td>Until Downtown is Reached</td>
                <td><code>Downtown & Brooklyn</code></td>
              </tr>
              <tr>
                <td>Until Brooklyn is Reached</td>
                <td><code>Brooklyn</code></td>
              </tr>
              <tr>
                <td>Once Brooklyn is Reached</td>
                <td><code>Brooklyn (New Lots Av)</code></td>
              </tr>
            </tbody>
          </table>

          <table class="example">
            <thead>
              <tr>
                <th colspan="2">In Boston, for the Red Line going Southbound, for the Braintree branch:</th>
              </tr>
              <tr>
                <th>For <code>stop_times.txt</code> rows:</th>
                <th>Use <code>stop_headsign</code> value:</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Until Downtown is Reached</td>
                <td><code>Inbound to Braintree</code></td>
              </tr>
              <tr>
                <td>Once Downtown is Reached</td>
                <td><code>Braintree</code></td>
              </tr>
              <tr>
                <td>After Downtown</td>
                <td><code>Outbound to Braintree</code></td>
              </tr>
            </tbody>
          </table>

  - field_name: shape_dist_traveled
    recommendations:
      - ID: 6
        tags: []
        text: |
          `shape_dist_traveled` must be provided for routes that have looping or inlining (the vehicle crosses or travels over the same portion of alignment in one trip). See the [`shapes.shape_dist_traveled`](#shapes_3) recommendation.<!-- (48) -->
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

Loop routes: Loop routes require special `stop_times` considerations. (See: [Loop route case](/best-practices/#loop-routes))
