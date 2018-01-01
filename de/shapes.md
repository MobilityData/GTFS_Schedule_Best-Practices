---
lang: de

table_data:
  - field_name: "All Fields"
    recommendations:
      - ID: 1
        tags: ['trip-planners','accessibility','arrival-predictions']
        text: |
          Ideally, for alignments that are shared (i.e. in a case where Routes 1 and 2 operate on the same segment of roadway or track) then the shared portion of alignment should match exactly. This helps to facilitate high-quality transit cartography. <!-- (77) -->
      - ID: 2
        tags: ['trip-planners','accessibility','arrival-predictions']
        text: |
          Alignments should follow the centerline of the right of way on which the vehicle travels. This could be either the centerline of the street if there are no designated lanes, or the centerline of the side of the roadway that travels in the direction the vehicle moves. <!-- (78) -->

          Alignments should not “jag” to a curb stop, platform, or boarding location.
  - field_name: shape_dist_traveled
    recommendations:
      - ID: 3
        tags: []
        text: |
          Must be provided in both `shapes.txt` and `stop_times.txt` if an alignment includes looping or inlining (the vehicle crosses or travels over the same portion of alignment in one trip). <!-- (79) -->
        example_table: |
          <figure id="inlining-fig">
            <img src="/best-practices/images/inlining.svg" alt="An Inlining Route">
            <figcaption>If a vehicle retraces or crosses the route alignment at points in the course of a trip, <code>shape_dist_traveled</code> is important to clarify how portions of the points in <code>shapes.txt</code> line up correspond with records in <code>stop_times.txt</code>.</figcaption>
          </figure>
      - ID: 4
        tags: []
        text: |
          The `shape_dist_traveled` field allows the agency to specify exactly how the stops in the `stop_times.txt` file fit into their respective shape. A common value to use for the `shape_dist_traveled` field is the distance from the beginning of the shape as traveled by the vehicle (think something like an odometer reading).

          * Route alignments (in `shapes.txt`) should be within 100 meters of stop locations which a trip serves.  <!-- (80) -->
          * Simplify alignments so that <code>shapes.txt</code> does not contain extraneous points (i.e. remove extra points on straight-line segments; see discussion of line simplification problem). <!-- (81) -->
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
