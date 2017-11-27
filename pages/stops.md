---
table_data:
  - field_name: stop_id
    recommendations:
      - ID: 1
        tags: ['trip-planners', 'arrival-predictions']
        text: "Stops that are in different physical locations (i.e., different designated precise locations for vehicles on designated routes to stop, potentially distinguished by signs, shelters, or other such public information, located on different street corners or representing different boarding facility such as a platform or bus bay, even if nearby each other) should have different `stop_id`. <!-- (27) -->"
      - ID: 2
        tags: []
        text: "`stop_id` is an internal ID, not intended to be shown to passengers. <!-- (38) -->"
      - ID: 3
        tags: []
        text: "Maintain consistent `stop_id` for the same stops across data iterations (see [Dataset Publishing & General Practices](#publishing)). <!-- (28) -->"
  - field_name: stop_name
    recommendations:
      - ID: 4
        tags: ['trip-planners','timetables','human-readability']
        text: "The `stop_name` should match the agency's public name for the stop, station, or boarding facility, e.g. what is printed on a timetable, published online, and/or presented at the location. <!-- (29) -->"
      - ID: 5
        tags: []
        text: "When there is not a published stop name, follow consistent stop naming conventions throughout the feed. <!-- (30) -->"
      - ID: 6
        tags: []
        text: "Avoid use of abbreviations other than for places that are most commonly called by an abbreviated name. See Abbreviations (#2) under [All Files](#all-files). <!-- (31) -->"
      - ID: 7
        tags: []
        text: "Provide stop names in mixed case, following local conventions, as per recommendation for all customer-facing text fields. <!-- (32) -->"
      - ID: 8
        tags: []
        text: |
          By default, `stop_name` should not contain generic or redundant words like “Station” or “Stop”, but some edge cases are allowed.

          * When it is actually part of the name (Union Station, Central Station)
          * When the `stop_name` is too generic (such as if it is the name of the city). “Station”, “Terminal”, or other words make the meaning clear.
  - field_name: stop_lat & stop_lon
    recommendations:
      - ID: 9
        tags: ['trip-planners']
        text: "Stop locations should be as accurate possible. Stop locations should have an error of __no more__ than four meters when compared to the actual stop position.<!-- (34) -->"
      - ID: 10
        tags: []
        text: "Stop locations should be placed very near to the pedestrian right of way where a passenger will board (i.e. correct side of the street).<!-- (35) -->"
      - ID: 11
        tags: []
        text: "If a stop location is shared across separate data feeds (i.e. two agencies use exactly the same stop / boarding facility), indicate the stop is shared by using the exact same `stop_lat` and `stop_lon` for both stops.<!-- (36) -->"
  - field_name: stop_code
    recommendations:
      - ID: 12
        tags: []
        text: "`stop_code` should be included in GTFS if there are passenger-facing stop numbers or short identifiers.<!-- (37) -->"
  - field_name: parent_station & location_type
    recommendations:
      - ID: 13
        tags: ['trip-planners','arrival-predictions','timetables']
        text: |
          Many stations or terminals have multiple boarding facilities (depending on mode, they might be called a bus bay, platform, wharf, gate, or another term). In such cases, feed producers should describe stations, boarding facilities (also called child stops), and their relation. <!-- (40) -->

          * The station or terminal should be defined as a record in `stops.txt` with `location_type = 1`.
          * Each boarding facility should be defined as a stop with `location_type = 0`. The `parent_station` field should reference the `stop_id` of the station the boarding facility is in.
      - ID: 14
        tags: []
        text: "When naming the station and child stops, set names that are well-recognized by riders, and can help riders to identify the station and boarding facility (bus bay, platform, wharf, gate, etc.). <!-- (41) -->"
        example_table: "
                <table class='example'>
                  <thead>
                    <tr>
                      <th>Parent Station Name</th>
                      <th>Child Stop Name</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr>
                      <td><a href='/images/chicago-union'>Chicago Union Station</a></td>
                      <td>Chicago Union Station Platform 19</td>
                    </tr>
                    <tr>
                      <td><a href='/images/sf-ferry'>San Francisco Ferry Building Terminal</a></td>
                      <td>San Francisco Ferry Building Terminal Gate E</td>
                    </tr>
                    <tr>
                      <td><a href='/images/transit-center'>Downtown Transit Center</a></td>
                      <td>Downtown Transit Center Bay B</td>
                    </tr>
                  </tbody>
                </table>"

---

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