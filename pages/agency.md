---
table_data:
  - field_name: agency_id
    recommendations:
      - ID: 1
        tags: ['human-readability', 'trip-planners', 'timetables']
        text: |
          Should be included, even if there is only one agency in the feed. (See also recommendation to include `agency_id` in [`routes.txt`](/best-practices/#routes) and [`fare_attributes.txt`](/best-practices/#fare-attributes)) <!-- (15) -->
  - field_name: agency_lang
    recommendations:
      - ID: 2
        tags: ['human-readability', 'trip-planners', 'timetables']
        text: |
          Should be included. <!-- (16) -->
  - field_name: agency_phone
    recommendations:
      - ID: 3
        tags: ['human-readability', 'trip-planners', 'timetables']
        text: |
          Should be included unless no such customer service phone exists. <!-- (17) -->
  - field_name: agency_email
    recommendations:
      - ID: 4
        tags: ['human-readability', 'trip-planners', 'timetables']
        text: |
          Should be included unless no such customer service email exists. <!-- (18) -->
  - field_name: agency_fare_url
    recommendations:
      - ID: 5
        tags: ['human-readability', 'trip-planners', 'timetables']
        text: |
          Should be included unless the agency is fully fare-free. <!-- (19) -->
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
