## Practice Recommendations Organized by File

This section shows practices organized by file and field, aligning with the [GTFS reference](/reference).

### All Files

| Field Name | Recommendation |
| --- | --- |
| Mixed Case | All customer-facing text strings (including stop names, route names, and headsigns) should use Mixed Case (not ALL CAPS), following local conventions for capitalization of place names on displays capable of displaying lower case characters. |
| | Examples: |
| | Brighton Churchill Square |
| | Villiers-sur-Marne |
| | Market Street |
| Abbreviations | Avoid use of abbreviations throughout the feed for names and other text (e.g. St. for Street) unless a location is called by its abbreviated name (e.g. “JFK Airport”). Abbreviations may be problematic for accessibility by screen reader software and voice user interfaces. Consuming software can be engineered to reliably convert full words to abbreviations for display, but converting from abbreviations to full words is prone to more risk of error. |
