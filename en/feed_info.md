---
lang: en

table_data:
  - field_name: feed_publisher_name
    recommendations:
      - ID: 1
        tags: ['trip-planners', 'human-readability']
        text: |
          Should be included <!--(21)-->
  - field_name: feed_publisher_url
    recommendations:
      - ID: 2
        tags: ['trip-planners', 'human-readability']
        text: |
          Should be included <!--(22)-->
  - field_name: feed_lang
    recommendations:
      - ID: 3
        tags: ['trip-planners', 'human-readability']
        text: |
          Should be included <!--(23)-->
  - field_name: feed_start_date & feed_end_date
    recommendations:
      - ID: 4
        tags: ['trip-planners', 'human-readability']
        text: |
          Should be included <!--(24)-->
  - field_name: feed_version
    recommendations:
      - ID: 5
        tags: ['trip-planners', 'human-readability']
        text: |
          Should be included <!--(25)-->
  - field_name: feed_contact_email & feed_contact_url
    recommendations:
      - ID: 6
        tags: ['trip-planners', 'human-readability']
        text: |
          Provide at least one <!--(26)-->
---

`feed_info.txt` should be included, with all fields below. <!-- (20) -->

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
