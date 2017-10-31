---
table_data:
  - field_name: agency_id
    recommendations:
      - number: 1
        tags: ['human-readability', 'trip-planners', 'timetables']
        text: "Should be included, even if there is only one agency in the feed. (See also: recommendation to include <code>agency_id</code> in <a href='/best-practices/#routes'><code>routes.txt</code></a> and <a href='/best-practices/#fare-attributes'><code>fare_attributes.txt</code></a>)"
  - field_name: agency_lang
    recommendations:
      - number: 2
        text: "Should be included."
  - field_name: agency_phone
    recommendations:
      - number: 3
        text: "Should be included unless no such customer service phone exists."
  - field_name: agency_email
    recommendations:
      - number: 4
        text: "Should be included unless no such customer service email exists."
  - field_name: agency_fare_url
    recommendations:
      - number: 5
        text: "Should be included unless the agency is fully fare-free."
---
### agency.txt {#agency}

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
    <tr id="{{ field.field_name }}_{{ recommendation.number }}" class="anchor-row {% for tag in recommendation.tags %}{{ tag }} {% endfor %}">
      <td>{% if forloop.first %}<code>{{ field.field_name }}</code>{% endif %}</td>
      <td>{{ recommendation.number }}</td>
      <td>{{ recommendation.text }}</td>
    </tr>
      {% endfor %}
    {% endfor %}
  </tbody>
</table>

<span class="tag trip-planners"></span>
<span class="tag human-readability"></span>
<span class="tag timetables"></span>

<table class="recommendation">
  <thead>
    <tr>
      <th>Field Name</th>
      <th>Tags</th>
      <th>#</th>
      <th>Recommendation</th>
    </tr>
  </thead>
  <tbody>
    <tr id="agency_1" class="anchor-row">
      <td><code>agency_id</code></td> <!-- (15) -->
      <td></td>
      <td>1</td>
      <td>Should be included, even if there is only one agency in the feed. (See also: recommendation to include <code>agency_id</code> in <a href="#routes"><code>routes.txt</code></a> and <a href="#fare-rules"><code>fare_attributes.txt</code></a>)</td>
    </tr>
    <tr id="agency_2" class="anchor-row">
      <td><code>agency_lang</code></td> <!-- (16) -->
      <td></td>
      <td>2</td>
      <td>Should be included</td>
    </tr>
    <tr id="agency_3" class="anchor-row">
      <td><code>agency_phone</code></td> <!-- (17) -->
      <td></td>
      <td>3</td>
      <td>Should be included unless no such customer service phone exists.</td>
    </tr>
    <tr id="agency_4" class="anchor-row">
      <td><code>agency_email</code></td> <!-- (18) -->
      <td></td>
      <td>4</td>
      <td>Should be included unless no such customer service email exists.</td>
    </tr>
    <tr id="agency_5" class="anchor-row">
      <td><code>agency_fare_url</code></td> <!-- (19) -->
      <td></td>
      <td>5</td>
      <td>Should be included unless the agency is fully fare-free.</td>
    </tr>
  </tbody>
</table>
