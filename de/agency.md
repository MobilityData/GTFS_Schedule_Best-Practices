---
lang: de

table_data:
  - field_name: agency_id
    recommendations:
      - ID: 1
        tags: ['human-readability', 'trip-planners', 'timetables']
        text: |
          Sollte eingeschlossen werden, auch wenn nur eine Agentur im Feed vorhanden ist. (Siehe auch Empfehlung, `agency_id` in [`routes.txt`](#routes) und [`fare_attributes.txt`](#fare_attributes))
  - field_name: agency_lang
    recommendations:
      - ID: 2
        tags: ['human-readability', 'trip-planners', 'timetables']
        text: |
          Das sollte dabei sein.
  - field_name: agency_phone
    recommendations:
      - ID: 3
        tags: ['human-readability', 'trip-planners', 'timetables']
        text: |
          Sollte enthalten sein, es sei denn, ein solches Kundendiensttelefon existiert nicht.
  - field_name: agency_email
    recommendations:
      - ID: 4
        tags: ['human-readability', 'trip-planners', 'timetables']
        text: |
          Sollte enthalten sein, sofern keine solche Kundendienst-E-Mail existiert.
  - field_name: agency_fare_url
    recommendations:
      - ID: 5
        tags: ['human-readability', 'trip-planners', 'timetables']
        text: |
          Sollte enthalten sein, es sei denn, die Agentur ist vollständig frei von Fahrkarten.
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
