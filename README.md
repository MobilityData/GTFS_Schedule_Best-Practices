# gtfs-best-practices

Best Practices for Structuring General Transit Feed Specification Data

# Editing GTFS Best Practices

The Best Practices data are written in YAML variables. More information about YAML syntax and structure may be found [here](https://learnxinyminutes.com/docs/yaml/). Each variable is defined as follows:

* `field_name`: The name of the GTFS field being described
* `recommendations`: An array of the recommendations provided for each field_name
  * `ID`: A unique identifying integer of the corresponding recommendation.
  * `tags`: An array of System Tags used to denote that the recommendation will assist with the described task. Values include 'human-readability', 'trip-planners', 'timetables', and 'accessibility'.
  * `text`: The text of the recommendation. This variable should begin with a vertical bar ( | ) followed by an indented newline. This will preserve any equally indented newlines in the text. Simple Markdown is allowed and any HTML should be avoided.
  * `example_table`: An optional variable, this allows for example tables (or any other HTML entity) to be placed immediately after the recommendation text. This variable should begin with a vertical bar ( | ) followed by an indented newline. This will preserve any equally indented newlines in the text. Markdown will not function in this variable and should be exclusively used for HTML elements.

Elements of Best Practices not in a table may be found below the YAML front matter and should be written in Markdown.

# License

Except as otherwise noted, the content of this repository is licensed under the [Creative Commons Attribution 3.0 License](https://creativecommons.org/licenses/by/3.0/), and code samples are licensed under the [Apache 2.0 License](http://www.apache.org/licenses/LICENSE-2.0).