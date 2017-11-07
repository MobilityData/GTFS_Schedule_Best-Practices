---
table_data:
  - field_name: "All Fields"
    recommendations:
      - ID: 1
        tags: ['human-readability','timetables']
        text: "`calendar_dates.txt` should only contain a limited number of exceptions to the schedule. Regularly-scheduled service should be configured using `calendar.txt`."
      - ID: 2
        tags: []
        text: "Including a `calendar.service_name` field can also increase the human readability of GTFS, although this is not adopted in the spec."

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