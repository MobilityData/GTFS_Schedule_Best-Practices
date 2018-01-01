---
lang: fr

table_data:
  - field_name: "All Fields"
    recommendations:
      - ID: 1
        tags: ['trip-planners','accessibility']
        text: |
          `agency_id` should be included in `fare_attributes.txt` if it the field is included in `agency.txt`. <!-- (84) -->
      - ID: 2
        tags: ['trip-planners','accessibility']
        text: |
          If a fare system cannot be accurately modeled, avoid further confusion and leave it blank. <!-- (85) -->
      - ID: 3
        tags: ['trip-planners','accessibility']
        text: |
          Include fares (`fare_attributes.txt` and `fare_rules.txt`) and model them as accurately as possible. In edge cases where fares cannot be accurately modeled, the fare should be represented as more expensive rather than less expensive so customers will not attempt to board with insufficient fare. If the vast majority of fares cannot be modeled correctly, do not include fare information in the feed. <!-- (86) -->
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
