---
---

<h2 id="by-file">Practice Recommendations Organized by File</h2>

This section shows practices organized by file and field, aligning with the [GTFS reference](https://github.com/google/transit/blob/master/gtfs/spec/en/reference.md).

### All Files

<table class="recommendation">
  <thead>
    <tr>
      <th>Topic</th>
      <th>Tags</th>
      <th>#</th>
      <th>Recommendation</th>
    </tr>
  </thead>
  <tbody>
    <tr id="all_files_1" class="anchor-row">
      <td><strong>Mixed Case</strong></td> <!-- (12) -->
      <td></td>
      <td>1</td>
      <td>All customer-facing text strings (including stop names, route names, and headsigns) should use Mixed Case (not ALL CAPS), following local conventions for capitalization of place names on displays capable of displaying lower case characters.
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
      </td>
    </tr>
    <tr id="all_files_2" class="anchor-row">
      <td><strong>Abbreviations</strong></td> <!-- (14) -->
      <td></td>
      <td>2</td>
      <td>Avoid use of abbreviations throughout the feed for names and other text (e.g. St. for Street) unless a location is called by its abbreviated name (e.g. “JFK Airport”). Abbreviations may be problematic for accessibility by screen reader software and voice user interfaces. Consuming software can be engineered to reliably convert full words to abbreviations for display, but converting from abbreviations to full words is prone to more risk of error.</td>
    </tr>
  </tbody>
</table>
