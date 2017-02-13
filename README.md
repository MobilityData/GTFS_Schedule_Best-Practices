# gtfs-best-practices

Best Practices for Structuring General Transit Feed Specification Data

# Best Practices for Styling the GTFS Best Practices

### Section Headers

Main section headers (h2 tags) must be in HTML to preserve navigation functionality.

### Subsection Headers

Subsection headers will use three hash marks (###) in front of them.

* Example: `### Subsection Header`

### System Tags

System tags (Trip Planners, Human Readability, etc.) will use six hashes (######) in front.

* Example: `###### System Tag`

### File Names

File names (e.g. stops.txt, trips.txt) should be nested between backticks (` `), not apostrophes.

* Example: ``file_name.txt``

### Field Names

GTFS Field names (e.g. stop_lat, direction_id) should be bold, nested between double underscores.

* Example: `__field_name__`

### Hyperlinks

Hyperlinks will automatically format. Only the appropriate Markdown is needed.

* Example: `[Link Text Goes Here](link_address_goes_here.com)`
