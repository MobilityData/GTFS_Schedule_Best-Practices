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

### Example Data

Example information will be displayed with Markdown blockquotes, which can be achieved by prepending each line with a (>) symbol.

* Example:

```
> Example one
> * Bulleted example
>   * Subbullet example
```

### Image additions

Images will be formatted automatically. Simply add the image to the images folder and reference it in Markdown in the following way.

* Example:

`![Image description goes here]( {{ "/best-practices/images/image_name.jpg" | prepend: site.baseurl }} )`

### Figure Captions

Image captions will help better explain the image and incorporate it into the document.

`<figcaption>My caption text</figcaption>`

### Hyperlinks

Hyperlinks will automatically format. Only the appropriate Markdown is needed.

* Example: `[Link Text Goes Here](link_address_goes_here.com)`
