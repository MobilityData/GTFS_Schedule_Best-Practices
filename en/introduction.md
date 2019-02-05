---
lang: en

---
# GTFS Data Best Practices

## Introduction

These are recommended practices for describing public transportation services in the [General Transit Feed Specification (GTFS)](http://gtfs.org). These practices have been synthesized from the experience of the [GTFS Best Practices working group](#gtfs-best-practices-working-group) members and [application-specific GTFS practice recommendations](http://www.transitwiki.org/TransitWiki/index.php/Best_practices_for_creating_GTFS). For further background, see the [Frequently Asked Questions](#frequently-asked-questions-faq).

### Document Structure

Recommended practices are organized into three primary sections

* __[Dataset Publishing & General Practices](#dataset-publishing--general-practices):__ These practices relate to the overall structure of the GTFS dataset and to the manner in which GTFS datasets are published.
* __[Practice Recommendations Organized by File](#practice-recommendations-organized-by-file):__ Recommendations are organized by file and field in the GTFS to facilitate mapping practices back to the official GTFS reference.
* __[Practice Recommendations Organized by Case](#practice-recommendations-organized-by-case):__ With particular cases, such as loop routes, practices may need to be applied across several files and fields. Such recommendations are consolidated in this section.

<div hidden> remove this
### System Tags

The System Tags menu includes four different tags, each corresponding to a description below. Selecting one of these tags will highlight all applicable recommendations.

<hr/>

<button class="system-tag-button trip-planners" data-target="trip-planners">Trip Planners</button>

These practices improve customer experience in applications like Google Maps that are used for trip planning.

<hr/>

<button class="system-tag-button human-readability" data-target="human-readability">Human Readability</button>

These practices help maintain the ability for a human reader to unzip and examine GTFS files.

<hr/>

<button class="system-tag-button arrival-predictions" data-target="arrival-predictions">Arrival Predictions</button>

These practices allow arrival prediction software to create real-time arrival estimates related to the schedules in [`trips.txt`](#trips) and [`stop_times.txt`](#stop_times).

<hr/>

<button class="system-tag-button timetables" data-target="timetables">Timetables</button>

These practices support the creation of HTML timetables based on GTFS, such as with the GTFS-to-HTML software.

remove this</div>
