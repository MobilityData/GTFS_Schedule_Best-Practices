---
lang: de

table_data:
  - field_name: "Gemischter Fall"
    recommendations:
      - ID: 1
        tags: []
        text: |
          Alle kundenspezifischen Textzeichenfolgen (einschließlich Stoppnamen, Routennamen und Kopfzeilen) sollten gemischte Groß- / Kleinschreibung (nicht ALLE GROSSBUCHSTABEN) verwenden und dabei lokale Konventionen für die Groß- / Kleinschreibung von Ortsnamen in Anzeigen verwenden, die Kleinbuchstaben anzeigen können.
        example_table: |
          <table class="example">
            <thead>
              <tr>
                <th>Beispiele</th>
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
  - field_name: "Abkürzungen"
    recommendations:
    - ID: 2
      tags: []
      text: |
        Vermeiden Sie die Verwendung von Abkürzungen im gesamten Feed für Namen und andere Texte (z. B. St. für Straße), es sei denn, ein Standort wird durch seinen abgekürzten Namen aufgerufen (z. B. "JFK Airport"). Abkürzungen können für die Zugänglichkeit durch Bildschirmlesesoftware und Sprachbenutzerschnittstellen problematisch sein. Konsumierende Software kann entwickelt werden, um vollständige Wörter zuverlässig in Abkürzungen für die Anzeige umzuwandeln, aber die Umwandlung von Abkürzungen in ganze Wörter neigt zu einem höheren Fehlerrisiko.
---

## Praxisempfehlungen organisiert nach Datei {#by-file}

Dieser Abschnitt zeigt Vorgehensweisen, die nach Datei und Feld sortiert sind und mit der [GTFS-Reference](https://github.com/google/transit/blob/master/gtfs/spec/en/reference.md) übereinstimmen .

### Alle Dateien {#all-files}

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
