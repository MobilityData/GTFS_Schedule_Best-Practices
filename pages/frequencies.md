---
table_data:
  - field_name: "All Fields"
    recommendations:
      - ID: 1
        tags: ['trip-planners','arrival-predictions','timetables','human-readability']
        text: "Actual stop times are ignored for trips referenced by `frequencies.txt`; only travel time intervals between stops are significant for frequency-based trips. For clarity/human readability, it is recommended that the first stop time of a trip referenced in `frequencies.txt` should begin at 00:00:00 (first `arrival_time` value of 00:00:00). <!-- (99) -->"
  - field_name: block_id
    recommendations:
      - ID: 2
        tags: []
        text: "Can be provided for frequency-based trips. <!-- (101) -->"
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
