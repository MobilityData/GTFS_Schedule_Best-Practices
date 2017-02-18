---
layout: best-practices
---

# GTFS Data Best Practices

<h2 id="introduction">Introduction</h2>

These are recommended practices for describing public transportation services in the [General Transit Feed Specification (GTFS)](https://gtfs.org). These practices have been synthesized from the experience of the [GTFS Best Practices working group](#working-group) members and [application-specific GTFS practice recommendations](http://www.transitwiki.org/TransitWiki/index.php/Best_practices_for_creating_GTFS).

### Document Structure

Recommended practices are organized into three primary sections

* __[Dataset Publishing & General Practices](#publishing):__ These practices relate to the overall structure of the GTFS dataset and to the manner in which GTFS datasets are published.
* __[Practice Recommendations Organized by File](#by-file):__ Recommendations are organized by file and field in the GTFS to facilitate mapping practices back to the official GTFS reference.
* __[Practice Recommendations Organized by Case](#by-case):__ With particular cases, such as loop routes, practices may need to be applied across several files and fields. Such recommendations are consolidated in this section.

### System Tags

Five different tags are included throughout the list of practices. These tags indicate the type of systems that require the practice being described.

###### Trip Planners

These practices improve customer experience in applications like Google Maps that are used for trip planning.

###### Human Readability

These practices help maintain the ability for a human reader to unzip and examine GTFS files.

###### Arrival Predictions
These practices allow arrival prediction software to create real-time arrival estimates related to the schedules in [`trips.txt`](#trips) and [`stop_times.txt`](#stop-times).

###### Timetables
These practices support the creation of HTML timetables based on GTFS, such as with the GTFS-to-HTML software.

<h1 id="practices">Practices</h1>

<h2 id="publishing">Dataset Publishing & General Practices</h2>

__1.__ Datasets should be published at a public, permanent URL, including the zip file name. (e.g., [www.agency.org/gtfs/gtfs.zip](http://www.agency.org/gtfs/gtfs.zip)).  Ideally, the URL should be directly downloadable without requiring login to access the file, to facilitate download by consuming software applications.<!-- (1) --> While it is recommended (and the most common practice) to make a GTFS dataset openly downloadable, if a data provider does need to control access to GTFS for licensing or other reasons, it is recommended to control access to the GTFS dataset using API keys, which will facilitate automatic downloads. <!-- (2) -->

__2.__ GTFS data is published in iterations so that a single file at a stable location always contains the latest official description of service for a transit agency (or agencies). <!-- (3) -->

__3.__ Maintain persistent identifiers (id fields) for `stop_id`, `route_id`, and `agency_id` across data iterations whenever possible. <!-- (4) -->

__4.__ One GTFS dataset should contain current and upcoming service (sometimes called a “merged” dataset). <!-- (5) -->

  * At any time, the published GTFS dataset should be valid for for at least the next 7 days, and ideally for as long as the operator is confident that the schedule will continue to be operated.
  * If possible, the GTFS dataset should cover at least the next 30 days of service.

__5.__ Remove old services (expired calendars) from the feed. <!-- (10) -->

__6.__ If a service modification will go into effect in 7 days or fewer, express this service change through a [GTFS-realtime](https://developers.google.com/transit/gtfs-realtime/) feed (service advisories or trip updates) rather than static GTFS dataset. <!-- (8) -->

__7.__ The web-server hosting GTFS data should be configured to correctly report the file modification date (see [HTTP/1.1 - Request for Comments 2616](https://tools.ietf.org/html/rfc2616#section-14.29), under Section 14.29). <!-- (9) -->

## Practice Recommendations Organized by File

This section shows practices organized by file and field, aligning with the [GTFS reference](https://github.com/google/transit/blob/master/gtfs/spec/en/reference.md).

### All Files

__1.__ __Mixed Case__: <!-- (12) -->
All customer-facing text strings (including stop names, route names, and headsigns) should use Mixed Case (not ALL CAPS), following local conventions for capitalization of place names on displays capable of displaying lower case characters.

<!-- We need a style to designate this is an example table. -->

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

__2.__ __Abbreviations__: <!-- (14) -->
Avoid use of abbreviations throughout the feed for names and other text (e.g. St. for Street) unless a location is called by its abbreviated name (e.g. “JFK Airport”). Abbreviations may be problematic for accessibility by screen reader software and voice user interfaces. Consuming software can be engineered to reliably convert full words to abbreviations for display, but converting from abbreviations to full words is prone to more risk of error.

<h3 id="agency">agency.txt</h3>

###### Trip Planners

###### Human Readability

###### Timetables

###### Planning and Analysis

Field Name | Recommendation
---------- | --------------
__1.__ `agency_id` <!-- (15) --> | Should be included, even if there is only one agency in the feed. (See also: recommendation to include `agency_id` in [`routes.txt`](#routes) and [`fare_attributes.txt`](#fare-rules))
__2.__ `agency_lang` <!-- (16) --> | Field should be included.
__3.__ `agency_phone` <!-- (17) --> | Should be included unless no such customer service phone exists.
__4.__ `agency_email` <!-- (18) --> | Should be included unless no such customer service email exists.
__5.__ `agency_fare_url` <!-- (19) --> | Should be included unless the agency is fully fare-free.

<h3 id="feed-info">feed_info.txt</h3>

###### Trip Planners

###### Human Readability

`feed_info.txt` should be included, with all fields below. <!-- (20) -->

Field Name | Recommendation
---------- | --------------
__1.__ `feed_publisher_name` <!-- (21) --> | Should be included
__2.__ `feed_publisher_url` <!-- (22) --> | Should be included
__3.__ `feed_lang` <!-- (23) --> | Should be included
__4.__ `feed_start_date` & `feed_end_date` <!-- (24) -->| Should be included
__5.__ `feed_version` <!-- (25) --> | Should be included
__6.__ `feed_contact_email` & `feed_contact_url` <!-- (26) --> | Provide at least one

<h3 id="stops">stops.txt</h3>

#### stop_id

###### Trip Planners

###### Arrival Predictions

__1.__ Stops that are in different physical locations (i.e., different designated precise locations for vehicles on designated routes to stop, potentially distinguished by signs, shelters, or other such public information, located on different street corners or representing different boarding facility such as a platform or bus bay, even if nearby each other) should have different `stop_id`. <!-- (27) -->

__2.__ `stop_id` is an internal ID, not intended to be shown to passengers. <!-- (38) -->

__3.__ Maintain consistent `stop_id` for the same stops across data iterations (see: [Dataset Publishing & General Practices](#publishing)). <!-- (28) -->

#### stop_name

###### Trip Planners

###### Timetables

###### Human Readability

__4.__ The `stop_name` should match the agency's public name for the stop, station, or boarding facility, e.g. what is printed on a timetable, published online, and/or presented at the location. <!-- (29) -->

__5.__ When there is not a published stop name, follow consistent stop naming conventions throughout the feed. <!-- (30) -->

__6.__ Avoid use of abbreviations other than for places that are most commonly called by an abbreviated name. See Abbreviations (#2) under [All Files](#all-files). <!-- (31) -->

__7.__ Provide stop names in mixed case, following local conventions, as per recommendation for all customer-facing text fields. <!-- (32) -->

__8.__ By default, `stop_name` should not contain generic or redundant words like “Station” or “Stop”, but some edge cases are allowed:

  * When it is actually part of the name (Union Station, Central Station)
  * When the `stop_name` is too generic (such as if it is the name of the city). “Station”, “Terminal”, or other words make the meaning clear.

#### stop_lat & stop_lon

###### Trip Planners

__9.__ Stop locations should be as accurate possible. Stop locations should have an error of **_no more_** than four meters when compared to the actual stop position. <!-- (34) -->

__10.__ Stop locations should be placed very near to the pedestrian right of way where a passenger will board (i.e. correct side of the street). <!-- (35) -->

__11.__ If a stop location is shared across separate data feeds (i.e. two agencies use exactly the same stop / boarding facility), indicate the stop is shared by using the exact same `stop_lat` and `stop_lon` for both stops. <!-- (36) -->

#### stop_code

__12.__ `stop_code` should be included in GTFS if there are passenger-facing stop numbers or short identifiers. <!-- (37) -->

#### parent_station & location_type

###### Trip Planners

###### Arrival Predictions

###### Timetables

__13.__ Many stations or terminals have multiple boarding facilities (depending on mode, they might be called a bus bay, platform, wharf, gate, or another term). In such cases, feed producers should describe stations, boarding facilities (also called child stops), and their relation. <!-- (40) -->

  * The station or terminal should be defined as a record in `stops.txt` with `location_type = 1`.
  * Each boarding facility should be defined as a stop with `location_type = 0`. The parent\_station field should reference the stop\_id of the station the boarding facility is in.

__14.__ When naming the station and child stops, set names that are well-recognized by riders, and can help riders to identify the station and boarding facility (bus bay, platform, wharf, gate, etc.). <!-- (41) -->

<table class="example">
  <thead>
    <tr>
      <th>Parent Station Name</th>
      <th>Child Stop Name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Chicago Union Station</td>
      <td>Chicago Union Station Platform 19</td>
    </tr>
    <tr>
      <td><a href="{{ "/images/sf-ferry" | prepend: site.baseurl }}">San Francisco Ferry Building Terminal</a></td>
      <td>San Francisco Ferry Building Terminal</td>
    </tr>
    <tr>
      <td><a href="{{ "/images/transit-center" | prepend: site.baseurl }}">Downtown Transit Center</a></td>
      <td>Downtown Transit Center Bay B</td>
    </tr>
  </tbody>
</table>

<h3 id="stop-times">stop_times.txt</h3>

#### pickup_type & drop_off_type

__1.__ Non-revenue (deadhead) trips that do not provide passenger service should be marked with `pickup_type` and `drop_off_type` value of `1` for all `stop_times` rows.<!-- 13 -->

__2.__ On revenue trips, internal “timing points” for monitoring operational performance and other places such as garages that a passenger cannot board should be marked with `pickup_type = 1` (no pickup available) and `drop_off_type = 1` (no drop off available). <!-- (46) -->


#### timepoint
__3.__ The `timepoint` field should be provided. It specifies which `stop_times` the operator will attempt to strictly adhere to (`timepoint=1`), and that other stop times are estimates (`timepoint=0`).<!-- (44) -->

#### arrival_time & departure_time

###### Trip Planners

###### Arrival Predictions

__4.__ `arrival_time` and `departure_time` fields should specify time values whenever possible, including non-binding estimated or interpolated times between timepoints. <!-- (45) -->

#### stop_headsign

###### Trip Planners

__5.__ `stop_headsign` values override the `trip_headsign` (in `trips.txt`). `stop_headsign` values should be provided when the text displayed on the headsign changes during a trip. `stop_headsign` values do not “carry down” to subsequent stops, and therefore values must be repeated if the stop headsign remains the same. In general, headsign values should also correspond to signs in the stations. <!-- (47) -->

Examples:

<table class="example">
  <thead>
    <tr>
      <th colspan="2">In NYC, for the 2 going Southbound:</th>
    </tr>
    <tr>
      <th>For <code>stop_times.txt</code> rows:</th>
      <th>Use this <code>stop_headsign</code> Value: </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Until Manhattan is Reached</td>
      <td><code>Manhattan & Brooklyn</code></td>
    </tr>
    <tr>
      <td>Until Downtown is Reached</td>
      <td><code>Downtown & Brooklyn</code></td>
    </tr>
    <tr>
      <td>Until Brooklyn is Reached</td>
      <td><code>Brooklyn</code></td>
    </tr>
    <tr>
      <td>Once Brooklyn is Reached</td>
      <td><code>Brooklyn (New Lots Av)</code></td>
    </tr>
  </tbody>
</table>

<table class="example">
  <thead>
    <tr>
      <th colspan="2">In Boston, for the Red Line going Southbound, for the Braintree branch:</th>
    </tr>
    <tr>
      <th>For <code>stop_times.txt</code> rows:</th>
      <th>Use this <code>stop_headsign</code> Value: </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Until Downtown is Reached</td>
      <td><code>Inbound to Braintree</code></td>
    </tr>
    <tr>
      <td>Once Downtown is Reached</td>
      <td><code>Braintree</code></td>
    </tr>
    <tr>
      <td>After Downtown</td>
      <td><code>Outbound to Braintree</code></td>
    </tr>
  </tbody>
</table>



In the above two cases, “Southbound” would mislead customers because it is not used in the station signs.

#### shape_dist_traveled

__6.__ `shape_dist_traveled` must be provided for routes that have looping or inlining (the vehicle crosses or travels over the same portion of alignment in one trip). See: [`shapes.shape_dist_traveled` recommendation.](#shape_dist_traveled) <!-- (48) -->

Loop routes: Loop routes require special `stop_times` considerations. (See: [Loop route case](#loop-routes))

<h3 id="transfers">transfers.txt</h3>

###### Trip Planners

#### transfers.transfer_type

`transfers.transfer_type` can be one of four values [defined in the GTFS](https://developers.google.com/transit/gtfs/reference/transfers-file). These `transfer_type` definitions are quoted from the GTFS Specification below, _in italics_, with additional practice recommendations. <!-- (49) -->

<q>0 or (empty): This is a recommended transfer point between two routes.</q> <!-- (50) -->

__1.__ If there are multiple transfer opportunities that include a superior option (i.e. a transit center with additional amenities or a station with adjacent or connected boarding facilities/platforms), specify a recommended transfer point. A change to the Specification — “recommended transfer point between ~~two~~ routes” — would make this definition more precise, as a recommended transfer point applies to all routes.

<q>1: This is a timed transfer point between two routes. The departing vehicle is expected to wait for the arriving one, with sufficient time for a passenger to transfer between routes.</q>

__2.__ This transfer type overrides a required interval to reliably make transfers.  As an example, Google Maps assumes that passengers need 3 minutes to safely make a transfer. Other applications may assume other defaults. <!-- (51) -->

<q>2: This transfer requires a minimum amount of time between arrival and departure to ensure a connection. The time required to transfer is specified by `min_transfer_time`.</q>

__3.__ Specify minimum transfer time if there are obstructions or other factors which increase the time to travel between stops. <!-- (52) -->

<q>3: Transfers are not possible between routes at this location.</q> <!-- (53) -->

__4.__ Specify this value if transfers are not possible because of physical barriers, or if they are made unsafe or complicated by difficult road crossings or gaps in the pedestrian network.

__5.__ If in-seat (block) transfers are allowed between trips, then the last stop of the arriving trip must be the same as the first stop of the departing trip. <!-- (55) -->

<h3 id="trips">trips.txt</h3>

* __See special case for loop routes:__ Loop routes are cases where trips start and end at the same stop, as opposed to linear routes, which have two distinct termini. Loop routes must be described following specific practices. [See Loop route case below.](#loop-routes)
* __See special case for lasso routes:__ Lasso routes are a hybrid of linear and loop geometries, in which vehicles travel on a loop for only a portion of the route. Lasso routes must be described following specific practices. [See Lasso route case below.](#lasso-routes)

#### trips.trip_headsign

###### Trip Planners

__1.__ Do not provide route names (matching `route_short_name` and `route_long_name`) in the `trip_headsign` or `stop_headsign` fields. <!-- (98) -->

__2.__ Should contain destination, direction, and/or other trip designation text shown on the headsign of the vehicle which may be used to distinguish amongst trips in a route. Consistency with direction information shown on the vehicle is the primary and overriding goal for determining headsigns supplied in GTFS datasets. Other information should be included only if it does not compromise this primary goal. If headsigns change during a trip, override `trip_headsign` with `stop_times.stop_headsign`. Below are recommendations for some possible cases. <!-- (58) -->

<!-- Make this into a table that makes it easy to look up examples for particular cases -->

<table class="example">
  <thead>
    <tr>
      <th>Route Description</th>
      <th>Recommendation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><nobr>2A. Destination-only</nobr></td>
      <td>Provide the terminus destination. e.g. "Transit Center", “Portland City Center”, or “Jantzen Beach” <!-- (58A) --> </td>
    </tr>
    <tr>
      <td><nobr>2B. Destinations with waypoints</nobr></td>
      <td>&lt;destination&gt; via &lt;waypoint&gt; “Highgate via Charing Cross”. If waypoint(s) are removed from the headsign show to passengers after the vehicle passes those waypoints, use <code>stop_times.stop_headsign</code> to set an updated headsign. <!-- (58B) --> </td>
    </tr>
    <tr>
      <td><nobr>2C. Regional placename with local stops</nobr></td>
      <td>If there will be multiple stops inside the city or borough of destination, use <code>stop_times.stop_headsign</code> once reaching the destination city. <!-- (58C) --> </td>
    </tr>
    <tr>
      <td><nobr>2D. Direction-only</nobr></td>
      <td>Indicate using terms such as “Northbound”, “Inbound”, “Clockwise,” or similar directions. <!-- (58D) --></td>
    </tr>
    <tr>
      <td><nobr>2E. Direction with destination</nobr></td>
      <td>&lt;direction&gt; to &lt;terminus name&gt; e.g. “Southbound to San Jose” <!-- (58E) --></td>
    </tr>
    <tr>
      <td><nobr>2F. Direction with destination and waypoints</nobr></td>
      <td>&lt;direction&gt; via &lt;waypoint&gt; to &lt;destination&gt; (“Northbound via Charing Cross to Highgate”). <!-- (58F) --></td>
    </tr>
  </tbody>
</table>

__3.__ Do not begin a headsign with the words “To” or “Towards”.


#### direction_id

###### Trip Planners

###### Timetables

###### Human Readability

__4.__ If trips on a route service opposite directions, distinguish these groups of trips with the `direction_id` field, using values 0 and 1. <!-- (64) -->

__5.__ Use values 0 and 1 consistently throughout the dataset. i.e. <!-- (65) -->

  * if 1 = Outbound on the Red route, then 1 = Outbound on the Green route
  * if 1 = Northbound on Route X, then 1 = Northbound on Route Y
  * if 1 = clockwise on Route X then 1 = clockwise on Route Y.

<h3 id="frequencies">frequencies.txt</h3>

###### Trip Planners

###### Timetables

###### Arrival Predictions

###### Human Readability

__1.__ Actual stop times are ignored for trips referenced by `frequencies.txt`; only travel time intervals between stops are significant for frequency-based trips. For clarity/human readability, it is recommended that the first stop time of a trip referenced in `frequencies.txt` should begin at 00:00:00 (first `arrival_time` value of 00:00:00). <!-- (99) -->

__2.__ `block_id` can be provided for frequency-based trips. <!-- (101) -->

<h3 id="routes">routes.txt</h3>

###### Trip Planners

###### Timetables

#### agency_id
__1.__ Must be included if it is defined in `agency.txt`. <!-- (68) -->

#### route_short_name
__2.__ Include `route_short_name` if there is a brief service designation. This should be the commonly-known passenger name of the service, no longer than 12 characters. <!-- (71) -->

#### route_long_name
__3.__ The definition from Specification reference:

<q>This name is generally more descriptive than the `route_short_name` and will often include the route's destination or stop. At least one of `route_short_name` or `route_long_name` must be specified, or potentially both if appropriate. If the route does not have a long name, please specify a `route_short_name` and use an empty string as the value for this field.</q>

Examples of types of long names are below:  <!-- (73) -->

<!-- This needs to be cleaned up - there should be another “route_short_name” / “route_long_name” -->

<table class="example">
  <thead>
    <tr>
      <th colspan="3">Primary Travel Path or Corridor</th>
    </tr>
    <tr>
      <th>Route Name</th>
      <th>Form</th>
      <th>Agency</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><a href="https://www.sfmta.com/getting-around/transit/routes-stops/n-judah">“N”/“Judah”</a></td>
      <td><code>route_short_name</code>/<code>route_long_name</code></td>
      <td><a href="https://www.sfmta.com/">Muni</a>, in San Francisco</td>
    </tr>
    <tr>
      <td><a href="https://trimet.org/schedules/r006.htm">"6"/"ML King Jr Blvd"</a></td>
      <td><code>route_short_name</code>/<code>route_long_name</code></td>
      <td><a href="https://trimet.org/">TriMet</a>, in Portland, Or.</td>
    </tr>
    <tr>
      <td><a href="http://www.ratp.fr/informer/pdf/orienter/f_plan.php?nompdf=m6">“6”/“Nation - Étoile”</a></td>
      <td><code>route_short_name</code>/<code>route_long_name</code></td>
      <td><a href="http://www.ratp.fr/">RATP</a>, in Paris France.</td>
    </tr>
    <tr>
      <td><a href="http://www.bvg.de/images/content/linienverlaeufe/LinienverlaufU2.pdf">“U2”-“Pankow – Ruhleben”</a></td>
      <td><code>route_short_name</code>-<code>route_long_name</code></td>
      <td><a href="http://www.bvg.de/">BVG</a>, in Berlin, Germany</td>
    </tr>
  </tbody>
</table>

<table class="example">
  <thead>
    <tr>
      <th>Description of the Service</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><a href="http://128bc.org/rev-hartwell-area-shuttle/">"Hartwell Area Shuttle"</a></td>
    </tr>
  </tbody>
</table>

__4.__ `route_long_name` should not contain the `route_short_name`. <!-- (72) -->

__5.__ Include the full designation including a service identity when populating `route_long_name`.

Examples: <!-- (69) --><!-- Examples need to be quoted here -->

<table class="example">
  <thead>
    <tr>
      <th>Service Identity</th>
      <th>Recommendation</th>
      <th>Examples</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>"MAX Light Rail"<br>TriMet, in Portland, Oregon</td>
      <td>The <code>route_long_name</code> should include the brand (MAX) and the specific route designation</td>
      <td>"MAX Red Line"<br>"MAX Blue Line"</td>
    </tr>
    <tr>
      <td>"Rapid Ride"<br>ABQ Ride, in Albuquerque, New Mexico</td>
      <td>The <code>route_long_name</code> should include the brand (Rapid Ride) and the specific route designation</td>
      <td>"Rapid Ride Red Line"<br>"Rapid Ride Blue Line"</td>
    </tr>
  </tbody>
</table>

#### route_id

__6.__ All trips on a given named route should reference the same `route_id`. <!-- (74) -->

  * Different directions of a route should not be separated into different `route_id` values.
  * Different spans of operation of a route should not be separated into different `route_id` values. i.e. do not create different records in `routes.txt` for “Downtown AM” and “Downtown PM” services).

__7.__ If a route group includes distinctly named branches (e.g. 1A and 1B), follow recommendations in the route [branches](#branches) case to determine `route_short_name` and `route_long_name`. <!-- (70) -->

#### route_color & route_text_color

__8.__ Should be consistent with signage and printed and online customer information (and thus not included if they do not exist in other places).  <!-- (76) -->

<h3 id="shapes">shapes.txt (alignments)</h3>

###### Trip Planners

###### Arrival Predictions

__1.__ Ideally, for alignments that are shared (i.e. in a case where Routes 1 and 2 operate on the same segment of roadway or track) then the shared portion of alignment should match exactly. This helps to facilitate high-quality transit cartography. <!-- (77) -->

__2.__ Alignments should follow the centerline of the right of way on which the vehicle travels. This could be either the centerline of the street if there are no designated lanes, or the centerline of the side of the roadway that travels in the direction the vehicle moves. <!-- (78) -->

  * Alignments should not “jag” to a curb stop, platform, or boarding location.

#### shape_dist_traveled

__3.__ Must be provided in both `shapes.txt` and `stop_times.txt` if an alignment includes looping or inlining (the vehicle crosses or travels over the same portion of alignment in one trip). <!-- (79) -->

<figure id="inlining-fig">
  <img src="{{ "/best-practices/images/inlining.svg" | prepend: site.baseurl }}" alt="An Inlining Route">
  <figcaption>If a vehicle retraces or crosses the route alignment at points in the course of a trip, <code>shape_dist_traveled</code> is important to clarify how portions of the points in <code>shapes.txt</code> line up correspond with records in <code>stop_times.txt</code>.</figcaption>
</figure>

__4.__ The `shape_dist_traveled` field allows the agency to specify exactly how the stops in the `stop_times.txt` file fit into their respective shape. A common value to use for the `shape_dist_traveled` field is the distance from the beginning of the shape as traveled by the vehicle (think something like an odometer reading).

* Route alignments (in `shapes.txt`) should be within 100 meters of stop locations which a trip serves.  <!-- (80) -->
* Simplify alignments so that `shapes.txt` does not contain extraneous points (i.e. remove extra points on straight-line segments; see discussion of line simplification problem). <!-- (81) -->

<h3 id="calendar">calendar.txt and calendar_dates.txt</h3>

###### Human Readability

###### Timetables

__1.__ `calendar_dates.txt` should only contain a limited number of exceptions to the schedule. Regularly-scheduled service should be configured using `calendar.txt`.

__2.__ Including a `calendar.service_name` field can also increase the human readability of GTFS, although this is not adopted in the spec.

<h3 id="fare-rules">fare_rules.txt and fare_attributes.txt</h3>

###### Trip Planners

__1.__ `agency_id` should be included in `fare_attributes.txt` if it the field is included in `agency.txt`. <!-- (84) -->

__2.__ If a fare system cannot be accurately modeled, avoid further confusion and leave it blank. <!-- (85) -->

__3.__ Include fares (`fare_attributes.txt` and `fare_rules.txt`) and model them as accurately as possible. In edge cases where fares cannot be accurately modeled, the fare should be represented as more expensive rather than less expensive so customers will not attempt to board with insufficient fare. If the vast majority of fares cannot be modeled correctly, do not include fare information in the feed. <!-- (86) -->


<h2 id="by-case">Practice Recommendations Organized by Case</h2>

This section covers particular cases with implications across files and fields.

<h3 id="loop-routes">Loop Routes</h3>

On loop routes, vehicles’ trips begin and end at the same location (sometimes a transit or transfer center). Vehicles usually operate continuously and allow passengers to stay onboard as the vehicle continues its loop.

<figure id="loop-route-fig">
  <img src="{{ "/best-practices/images/loop-route.svg" | prepend: site.baseurl }}" alt="A Loop Route">
  <figcaption>A loop route</figcaption>
</figure>

#### trips.trip_id
__1.__ Model the complete round-trip for the loop with a single trip.  <!-- (102) -->

#### stop_times.stop_id
__2.__ Include the first/last stop twice in `stop_times.txt` for the trip that is a loop. Example below. <!-- (87) -->

<table class="example">
  <thead>
    <tr>
      <th><code>trip_id</code></th>
      <th><code>stop_id</code></th>
      <th><code>stop_sequence</code></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>9000</td>
      <td>101</td>
      <td>1</td>
    </tr>
    <tr>
      <td>9000</td>
      <td>102</td>
      <td>2</td>
    </tr>
    <tr>
      <td>9000</td>
      <td>103</td>
      <td>3</td>
    </tr>
    <tr>
      <td>9000</td>
      <td>101</td>
      <td>4</td>
    </tr>
  </tbody>
</table>

Often, a loop route may include first and last trips that do not travel the entire loop. Include these trips as well.

#### trips.direction_id

__3.__ If loop operates in opposite directions (i.e. clockwise and counterclockwise), then designate `direction_id` as `0` or `1`. <!-- (89) -->

#### trips.block_id

__4.__ Indicate continuous loop trips with the same `block_id`. <!-- (90) -->

<h3 id="lasso-routes">Lasso Routes</h3>

Lasso routes are loop-routes from A to A via B with three sections:

* straight section from A to B;
* loop from and to B;
* straight section from B to A.

<figure id="lasso-route-fig">
  <img style="max-width: 30%" src="{{ "/best-practices/images/lasso-route.svg" | prepend: site.baseurl }}" alt="A Lasso Route">
  <figcaption>A lasso route</figcaption>
</figure>

<table class="example">
  <thead>
    <tr>
      <th>Examples:</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Subway Routes (<a href="http://www.transitchicago.com/assets/1/maps/L_Map_March_2016_s_lite.pdf">Chicago</a>)</td>
    </tr>
    <tr>
      <td>Bus Suburb to Downtown Routes (<a href="https://stalbert.ca/uploads/PDF-infosheets/201_207_Fall_2016.pdf">St. Albert</a> or <a href="http://webdocs.edmonton.ca/transit/route_schedules_and_maps/future/RT039.pdf">Edmonton</a>)</td>
    </tr>
    <tr>
      <td>See CTA Brown Line (<a href="http://www.transitchicago.com/brownline/">CTA Website</a> and <a href="https://transitfeeds.com/p/chicago-transit-authority/165/latest/route/Brn">TransitFeeds</a>)</td>
    </tr>
  </tbody>
</table>

#### trips.trip_id <!-- (103) -->

__1.__ The full extent of a “vehicle round-trip” (see illustration [above](#lasso-route-fig)) consists of travel from A to B to B and back to A. An entire vehicle round-trip may be expressed by:

  * __*A single*__ `trip_id`/record in `trips.txt`
  * __*Multiple*__ `trip_id` values/records in `trips.txt`, with continuous travel indicated by `block_id`.

#### stop_times.stop_headsign <!-- (94) -->

__2.__ The stops along the A-B section will be passed through in both directions. `stop_headsign` facilitates distinguishing travel direction. Therefore, providing `stop_headsign` is recommended for these trips.

<table class="example">
  <thead>
    <tr>
      <th>Examples:</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>"A via B"</td>
    </tr>
    <tr>
      <td>"A"</td>
    </tr>
  </tbody>
</table>

<table class="example">
  <thead>
    <tr>
      <th>Chicago Transit Authority's <a href="http://www.transitchicago.com/purpleline/">Purple Line</a></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>"Southbound to Loop"</td>
    </tr>
    <tr>
      <td>"Northbound via Loop"</td>
    </tr>
    <tr>
      <td>"Northbound to Linden"</td>
    </tr>
  </tbody>
</table>

<table class="example">
  <thead>
    <tr>
      <th>Edmonton Transit Service Bus Lines, here <a href="http://webdocs.edmonton.ca/transit/route_schedules_and_maps/future/RT039.pdf">the 39</a></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>"Rutherford"</td>
    </tr>
    <tr>
      <td>"Century Park"</td>
    </tr>
  </tbody>
</table>



#### trip.trip_headsign <!-- (95) -->

__3.__ The trip headsign should be a global description of the trip, like displayed in the schedules. Could be “Linden to Linden via Loop” (Chicago example), or “A to A via B” (generic example).

<h3 id="branches">Branches</h3>

Some routes may include branches. Alignment and stops are shared amongst these branches, but each also serves distinct stops and alignment sections. The relationship among branches may be indicated by route name(s), headsigns, and trip short name using the further guidelines below.

<figure id="branching-fig">
  <img src="{{ "/best-practices/images/branching.svg" | prepend: site.baseurl }}" alt="Configurations of Route Branches">
  <figcaption>Three potential configurations of route branches</figcaption>
</figure>

__1.__ In naming branch routes, it is recommended to follow other passenger information materials. Below are descriptions and examples of two cases: <!-- (97) -->

__1A.__ If timetables and on-street signage represent two distinctly named routes (e.g. 1A and 1B), then present this as such in the GTFS, using the `route_short_name` and/or `route_long_name` fields. <!-- (97A) -->

__Example__: GoDurham Transit [routes 2, 2A, and 2B](http://admin.gotransitnc.org/sites/default/files/godurham/aug2016/Route%202%20PDF%20August%202016.pdf) share a common alignment throughout the majority of the route, but they vary in several different aspects.

  * Route 2B serves additional stops in a spur of the shared alignment path.
  * Routes 2A and 2B operate daytime hours M-Sat.
  * Route 2 runs nights, Sundays, and holidays.

__1B.__ If agency-provided information describes branches as the same named route, then utilize the `trips.headsign`, `stop_times.headsign`, and/or `trips.trip_short_name` fields. <!-- (97B) -->

__Example__: GoTriangle [route 300](http://admin.gotransitnc.org/sites/default/files/maps-and-schedules/gotriangle/RoutesAndSchedules-1561.pdf) travels to different locations depending on the time of day. During peak commuter hours extra legs are added onto the standard route to accommodate workers entering and leaving the city.

<h2 id="about">About This Document</h2>

<h3 id="objectives">Objectives</h3>

The objectives of maintaining GTFS Best Practices is to:

* Improve end-user customer experience in public transportation apps
* Make it easier for software developers to deploy and scale applications, products, and services
* Facilitate the use of GTFS in various application categories (beyond its original focus on trip planning)

<h3 id="linking">Linking to This Document</h3>

Please link here in order to provide feed producers with guidance for correct formation of GTFS data. If your GTFS-consuming application involves particular requirements or recommendations for GTFS data practices, it is recommended to publish a document with those requirements or recommendations to supplement these common best practices.

<h3 id="amend">How to propose or amend published GTFS Best Practices</h3>

GTFS applications and practice evolve, and so this document may need to be amended from time to time. To propose an amendment to this document, open a pull request in GitHub and advocate for the change. The GTFS Best Practices Working Group will meet quarterly to discuss and approve selected changes.

<h2 id="working-group">GTFS Best Practices Working Group</h2>

The GTFS Best Practices Working Group consists of public transportation providers, developers of GTFS-consuming applications, consultants, and academic organizations to define common practices and expectations for GTFS data. The goals of this working group are to support greater interoperability of data data.

Members of this working group include:

* [Apple](http://www.apple.com/)
* [Cambridge Systematics](https://www.camsys.com/)
* [Capital Metro](https://www.capmetro.org/)
* [Center for Urban Transportation Research at University of South Florida](https://www.cutr.usf.edu/)
* [Conveyal](http://conveyal.com/)
* [Google](https://www.google.com/)
* [IBI Group](http://www.ibigroup.com/)
* [Mapzen](https://mapzen.com/)
* [Microsoft](https://www.microsoft.com/)
* [Moovel](https://www.moovel.com/)
* [Oregon Department of Transportation](http://www.oregon.gov/odot/)
* [Swiftly](https://goswift.ly/)
* [Transit](https://transitapp.com/)
* [Trillium](http://trilliumtransit.com/)
* [TriMet](https://trimet.org/)
* [World Bank](http://www.worldbank.org/)

To join the working group, email [gtfs-wg@rmi.org](mailto:gtfs-wg@rmi.org).

The GTFS Best Practices Working Group is convened and facilitated by [Rocky Mountain Institute](http://www.rmi.org/ITD), a non-profit organization transforming global energy use to create a clean, prosperous, and secure low-carbon future.
