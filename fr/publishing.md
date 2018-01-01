---
lang: fr

table_data:
  - field_name: General
    recommendations:
      - ID: 1
        tags: []
        text: |
          Datasets should be published at a public, permanent URL, including the zip file name. (e.g., www.agency.org/gtfs/gtfs.zip). Ideally, the URL should be directly downloadable without requiring login to access the file, to facilitate download by consuming software applications.<!-- (1) --> While it is recommended (and the most common practice) to make a GTFS dataset openly downloadable, if a data provider does need to control access to GTFS for licensing or other reasons, it is recommended to control access to the GTFS dataset using API keys, which will facilitate automatic downloads. <!-- (2) -->
      - ID: 2
        tags: []
        text: |
          GTFS data is published in iterations so that a single file at a stable location always contains the latest official description of service for a transit agency (or agencies). <!-- (3) -->
      - ID: 3
        tags: []
        text: |
          Maintain persistent identifiers (id fields) for `stop_id`, `route_id`, and `agency_id` across data iterations whenever possible. <!-- (4) -->
      - ID: 4
        tags: []
        text: |
          One GTFS dataset should contain current and upcoming service (sometimes called a “merged” dataset). Google transitfeed tool's [merge function](https://github.com/google/transitfeed/wiki/Merge) can be used to create a merged dataset from two different GTFS feeds.<!-- (5) -->

          * At any time, the published GTFS dataset should be valid for at least the next 7 days, and ideally for as long as the operator is confident that the schedule will continue to be operated.
          * If possible, the GTFS dataset should cover at least the next 30 days of service.

      - ID: 5
        tags: []
        text: |
          Remove old services (expired calendars) from the feed. <!-- (10) -->
      - ID: 6
        tags: []
        text: |
          If a service modification will go into effect in 7 days or fewer, express this service change through a [GTFS-realtime](https://developers.google.com/transit/gtfs-realtime/) feed (service advisories or trip updates) rather than static GTFS dataset. <!-- (8) -->
      - ID: 7
        tags: []
        text: |
          The web-server hosting GTFS data should be configured to correctly report the file modification date (see [HTTP/1.1 - Request for Comments 2616](https://tools.ietf.org/html/rfc2616#section-14.29), under Section 14.29). <!-- (9) -->
---

## Dataset Publishing & General Practices {#publishing}

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
