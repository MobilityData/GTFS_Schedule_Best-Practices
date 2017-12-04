---
table_data:
  - field_name: trips.trip_id
    recommendations:
      - ID: 1
        tags: []
        text: |
          The full extent of a “vehicle round-trip” (see illustration [above](#lasso-route-fig)) consists of travel from A to B to B and back to A. An entire vehicle round-trip may be expressed by: <!-- (103) -->

          * A __single__ `trip_id` value/record in `trips.txt`
          * __Multiple__ `trip_id` values/records in `trips.txt`, with continuous travel indicated by `block_id`.
  - field_name: stop_times.stop_headsign
    recommendations:
      - ID: 2
        tags: []
        text: |
          The stops along the A-B section will be passed through in both directions. `stop_headsign` facilitates distinguishing travel direction. Therefore, providing `stop_headsign` is recommended for these trips. <!-- (94) -->
        example_table: |
          <table class="example">
            <thead>
              <tr>
                <th>Examples:</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>"A via B"</td>
              </tr>
              <tr>
                <td>"A"</td>
              </tr>
            </tbody>
          </table>

          <table class="example">
            <thead>
              <tr>
                <th>Chicago Transit Authority's <a href="http://www.transitchicago.com/purpleline/">Purple Line</a></th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>"Southbound to Loop"</td>
              </tr>
              <tr>
                <td>"Northbound via Loop"</td>
              </tr>
              <tr>
                <td>"Northbound to Linden"</td>
              </tr>
            </tbody>
          </table>

          <table class="example">
            <thead>
              <tr>
                <th>Edmonton Transit Service Bus Lines, here <a href="http://webdocs.edmonton.ca/transit/route_schedules_and_maps/future/RT039.pdf">the 39</a></th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>"Rutherford"</td>
              </tr>
              <tr>
                <td>"Century Park"</td>
              </tr>
            </tbody>
          </table>
  - field_name: trip.trip_headsign
    recommendations:
      - ID: 3
        tags: []
        text: |
          The trip headsign should be a global description of the trip, like displayed in the schedules. Could be “Linden to Linden via Loop” (Chicago example), or “A to A via B” (generic example). <!-- (95) -->
---

### Lasso Routes

Lasso routes combine aspects of a loop route and directional route.

<figure id="lasso-route-fig">
  <figcaption>Below: Lasso routes are loop-routes from A to A via B with three sections:<br>
    <ul>
      <li>straight section from A to B;</li>
      <li>loop from and to B;</li>
      <li>straight section from B to A.</li>
    </ul>
  </figcaption>
  <img style="max-width: 30%" src="{{ "/best-practices/images/lasso-route.svg" | prepend: site.baseurl }}" alt="A Lasso Route">
</figure>

| Examples: |
| -------- |
| Subway Routes ([Chicago](http://www.transitchicago.com/assets/1/maps/L_Map_March_2016_s_lite.pdf)) |
| Bus Suburb to Downtown Routes ([St. Albert](https://stalbert.ca/uploads/PDF-infosheets/201_207_Fall_2016.pdf) or [Edmonton](http://webdocs.edmonton.ca/transit/route_schedules_and_maps/future/RT039.pdf)) |
| CTA Brown Line ([CTA Website](http://www.transitchicago.com/brownline/) and [TransitFeeds](https://transitfeeds.com/p/chicago-transit-authority/165/latest/route/Brn)) |

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
