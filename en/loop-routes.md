---
lang: en

table_data:
  - field_name: trips.trip_id
    recommendations:
      - ID: 1
        tags: []
        text: |
          Model the complete round-trip for the loop with a single trip.  <!-- (102) -->
  - field_name: stop_times.stop_id
    recommendations:
      - ID: 2
        tags: []
        text: |
          Include the first/last stop twice in `stop_times.txt` for the trip that is a loop. Example below. <!-- (87) -->

          Often, a loop route may include first and last trips that do not travel the entire loop. Include these trips as well.
        example_table: |
          <table class="example">
            <thead>
              <tr>
                <th><code>trip_id</code></th>
                <th><code>stop_id</code></th>
                <th><code>stop_sequence</code></th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>9000</td>
                <td>101</td>
                <td>1</td>
              </tr>
              <tr>
                <td>9000</td>
                <td>102</td>
                <td>2</td>
              </tr>
              <tr>
                <td>9000</td>
                <td>103</td>
                <td>3</td>
              </tr>
              <tr>
                <td>9000</td>
                <td>101</td>
                <td>4</td>
              </tr>
            </tbody>
          </table>
  - field_name: trips.direction_id
    recommendations:
      - ID: 3
        tags: []
        text: |
          If loop operates in opposite directions (i.e. clockwise and counterclockwise), then designate `direction_id` as `0` or `1`. <!-- (89) -->
  - field_name: trips.block_id
    recommendations:
      - ID: 4
        tags: []
        text: |
          Indicate continuous loop trips with the same `block_id`. <!-- (90) -->
---

## Practice Recommendations Organized by Case {#by-case}

This section covers particular cases with implications across files and fields.

### Loop Routes

On loop routes, vehicles’ trips begin and end at the same location (sometimes a transit or transfer center). Vehicles usually operate continuously and allow passengers to stay onboard as the vehicle continues its loop.

<figure id="loop-route-fig">
  <figcaption>Below: Loop route. The vehicle returns to the starting point in one trip. Some loop routes offer travel in one direction, and others in two directions.</figcaption>
  <img src="{{ "/best-practices/images/loop-route.svg" | prepend: site.baseurl }}" alt="A Loop Route">
</figure>

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
