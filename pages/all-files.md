---
table_data:
  - field_name: "Mixed Case"
    recommendations:
      - ID: 1
        tags: []
        text: "All customer-facing text strings (including stop names, route names, and headsigns) should use Mixed Case (not ALL CAPS), following local conventions for capitalization of place names on displays capable of displaying lower case characters. <!--(12)-->"
        example_table: |
          <table class="example">
            <thead>
              <tr>
                <th>Examples</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Brighton Churchill Square</td>
              </tr>
              <tr>
                <td>Villiers-sur-Marne</td>
              </tr>
              <tr>
                <td>Market Street</td>
              </tr>
            </tbody>
          </table>
  - field_name: "Abbreviations"
    recommendations:
    - ID: 2
      tags: []
      text: "Avoid use of abbreviations throughout the feed for names and other text (e.g. St. for Street) unless a location is called by its abbreviated name (e.g. “JFK Airport”). Abbreviations may be problematic for accessibility by screen reader software and voice user interfaces. Consuming software can be engineered to reliably convert full words to abbreviations for display, but converting from abbreviations to full words is prone to more risk of error.<!--(14)-->"
---

## Practice Recommendations Organized by File {#by-file}

This section shows practices organized by file and field, aligning with the [GTFS reference](https://github.com/google/transit/blob/master/gtfs/spec/en/reference.md).

### All Files

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
