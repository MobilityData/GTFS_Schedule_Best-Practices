---
layout: best-practices
---

# GTFS Data Best Practices

<h2 id="introduction">Introduction</h2>

This is an example of an inserted photo:

![Lucille looks mad!]({{ "/best-practices/images/lucille.jpg" | prepend: site.baseurl }})
<figcaption style="text-align: center; margin-bottom: 50px;">"You want me to ride the <em>what?</em>"</figcaption>

And an inline svg! God save us...

<svg width="0" height="0" style="display:none;">
  <symbol id="kiwi-svg">
    <path fill="black" d="m213.888556,1.330997c-105.966,0.774 -222.682,85.306 -209.277,211.118c4.303,40.393 18.533,63.704 52.171,79.03c36.307,16.544 57.022,54.556 50.406,112.954c-9.935,4.88 -17.405,11.031 -19.132,20.015c7.531,-0.17 14.943,-0.312 22.59,4.341c20.333,12.375 31.296,27.363 42.979,51.72c1.714,3.572 8.192,2.849 8.312,-3.078c0.17,-8.467 -1.856,-17.454 -5.226,-26.933c-2.955,-8.313 3.059,-7.985 6.917,-6.106c6.399,3.115 16.334,9.43 30.39,13.098c5.392,1.407 5.995,-3.877 5.224,-6.991c-1.864,-7.522 -11.009,-10.862 -24.519,-19.229c-4.82,-2.984 -0.927,-9.736 5.168,-8.351l20.234,2.415c3.359,0.763 4.555,-6.114 0.882,-7.875c-14.198,-6.804 -28.897,-10.098 -53.864,-7.799c-11.617,-29.265 -29.811,-61.617 -15.674,-81.681c12.639,-17.938 31.216,-20.74 39.147,43.489c-5.002,3.107 -11.215,5.031 -11.332,13.024c7.201,-2.845 11.207,-1.399 14.791,0c17.912,6.998 35.462,21.826 52.982,37.309c3.739,3.303 8.413,-1.718 6.991,-6.034c-2.138,-6.494 -8.053,-10.659 -14.791,-20.016c-3.239,-4.495 5.03,-7.045 10.886,-6.876c13.849,0.396 22.886,8.268 35.177,11.218c4.483,1.076 9.741,-1.964 6.917,-6.917c-3.472,-6.085 -13.015,-9.124 -19.18,-13.413c-4.357,-3.029 -3.025,-7.132 2.697,-6.602c3.905,0.361 8.478,2.271 13.908,1.767c9.946,-0.925 7.717,-7.169 -0.883,-9.566c-19.036,-5.304 -39.891,-6.311 -61.665,-5.225c-43.837,-8.358 -31.554,-84.887 0,-90.363c29.571,-5.132 62.966,-13.339 99.928,-32.156c32.668,-5.429 64.835,-12.446 92.939,-33.85c48.106,-14.469 111.903,16.113 204.241,149.695c3.926,5.681 15.819,9.94 9.524,-6.351c-15.893,-41.125 -68.176,-93.328 -92.13,-132.085c-24.581,-39.774 -14.34,-61.243 -39.957,-91.247c-21.326,-24.978 -47.502,-25.803 -77.339,-17.365c-23.461,6.634 -39.234,-7.117 -52.98,-31.273c-29.365,-51.617 -81.947,-74.215 -137.452,-73.811zm235.398,137.679c6.12,0 11.112,4.919 11.112,11.038c0,6.119 -4.994,11.111 -11.112,11.111s-11.038,-4.994 -11.038,-11.111c0,-6.119 4.92,-11.038 11.038,-11.038z" id="bird"/>
    <text xml:space="preserve" text-anchor="middle" font-family="serif" font-size="24" id="svg_2" y="319.159355" x="332.666668" stroke-linecap="null" stroke-linejoin="null" stroke-dasharray="null" stroke-width="0" fill="#000000">&#x27;sup I'm a kiwi</text>
  </symbol>
</svg>

<svg id="kiwi-actual" width="630" height="485">
  <title>Kiwi</title>
  <desc>It's a kiwi</desc>
  <use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="#kiwi-svg"></use>
</svg>

These are recommended practices for describing public transportation services in the [General Transit Feed Specification (GTFS)](https://developers.google.com/transit/gtfs/reference/). These practices have been synthesized from the experience of the [GTFS Best Practices working group]() members and [application-specific GTFS practice recommendations](http://www.transitwiki.org/TransitWiki/index.php/Best_practices_for_creating_GTFS).

#### Document Structure

Recommended practices are organized into three primary sections

* __[Dataset Publishing & General Practices](#publishing):__ These practices relate to the overall structure of the GTFS dataset and to the manner in which GTFS datasets are published.
* __[Practice Recommendations Organized by File](#by-file):__ Recommendations are organized by file and field in the GTFS to facilitate mapping practices back to the official GTFS reference.
* __[Practice Recommendations Organized by Case](#by-case):__ With particular cases, such as loop routes, practices may need to be applied across several files and fields. Such recommendations are consolidated in this section.

#### System Tags

Five different tags are included throughout the list of practices. These tags indicate the type of systems that require the practice being described.

###### Trip Planners
* These practices improve customer experience in applications like Google Maps that are used for trip planning.

###### Human Readability
* These practices help maintain the ability for a human reader to unzip and examine GTFS files.

###### Arrival Predictions
* These practices allow arrival prediction software to create real-time arrival estimates related to the schedules in [`trips.txt`](#trips) and [`stop_times.txt`](#stop-times).

###### Planning and Analysis
* Software and projects such as OpenTripPlanner Analyst, Open Transit Indicators, Accessibility Observatory, National Transit Map, AllTransit and Remix provide summaries and attributes of service based on GTFS data that follow these practices.

###### Timetables
* These practices support the creation of HTML timetables based on GTFS, such as with the GTFS-to-HTML software.


<h2 id="publishing">Dataset Publishing & General Practices</h2>

* Datasets should be published at a public, permanent URL, including the zip file name. (e.g., [www.agency.org/gtfs/gtfs.zip](http://www.agency.org/gtfs/gtfs.zip)).  The URL should be directly accessible/downloadable by software applications and should not require a manual login to access the file. <!-- (1) -->

* While it is recommended (and the most common practice) to make a GTFS dataset openly downloadable, if a data provider needs  to control access to GTFS for licensing or other reasons, it is recommended to control access to the GTFS dataset using a system of API keys, which will facilitate automatic downloads. <!-- (2) -->

* GTFS data is published in iterations so that a single file at a stable location always contains the latest official description of service for a transit agency (or agencies). <!-- (3) -->

* Maintain persistent identifiers (id fields) for __stop_id__, __route_id__, and __agency_id__ across data iterations whenever possible. <!-- (4) -->

* One GTFS dataset should contain current and upcoming service (sometimes called a “merged” dataset). <!-- (5) -->

  * At any time, the published GTFS dataset should be valid for for at least the next 7 days, and ideally for as long as the operator is confident that the schedule will continue to be operated.
  * If possible, the GTFS dataset should cover at least the next 30 days of service.

* If a service modification will go into effect in 7 days or fewer, express this service change through a GTFS-realtime feed (service advisories or trip updates) rather than static GTFS dataset. <!-- (8) -->

* The web-server hosting GTFS data should be configured to correctly report the file modification date (see [this document](https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html), under Section 14.29 Last-Modified). <!-- (9) -->

* Remove old services (expired calendars) from the feed. <!-- (10) -->



<h2 id="by-file">Practice Recommendations Organized by File</h2>

This section shows practices organized by file & field, aligning with the GTFS reference.

### All Files

__Mixed Case__: <!-- (12) -->
All customer-facing text strings (including stop names, route names, and headsigns) should use Mixed Case (not ALL CAPS), following local conventions for capitalization of place names on displays capable of displaying lower case characters.

| Examples: |
| --------- |
| Brighton Churchill Square |
| Villiers-sur-Marne |
| Market Street |

__Abbreviations__: <!-- (14) -->
Avoid use of abbreviations throughout the feed for names and other text (e.g. St. for Street) unless a location is called by its abbreviated name (e.g. “JFK Airport”). Abbreviations may be problematic for accessibility by screen reader software and voice user interfaces. Consuming software can be engineered to reliably convert full words to abbreviations for display, but converting from abbreviations to full words is prone to more risk of error.

<h3 id="agency">agency.txt</h3>

###### Trip Planners

###### Human Readability

###### Timetables

###### Planning and Analysis

Field Name | Recommendation
---------- | --------------
__agency_id__ <!-- (15) --> | Should be included, even if there is only one agency in the feed. (See also: recommendation to include agency_id in [`routes.txt`](#routes) and [`fare_attributes.txt`](#fare-rules).)
__agency_lang__ <!-- (16) --> | Field should be included.
__agency_phone__ <!-- (17) --> | Should be included unless no such customer service phone exists.
__agency_email__ <!-- (18) --> | Should be included unless no such customer service email exists.
__agency_fare_url__ <!-- (19) --> | Should be included unless the agency is fully fare-free, and `fare_attributes.txt` is included to indicate that the system is fare-free.

<h3 id="feed-info">feed_info.txt</h3>

###### Trip Planners

###### Human Readability

`feed_info.txt` should be included, with all fields below. <!-- (20) -->

Field Name | Recommendation
---------- | --------------
__feed_publisher_name__ <!-- (21) --> | Should be included
__feed_publisher_url__ <!-- (22) --> | Should be included
__feed_lang__ <!-- (23) --> | Should be included
__feed_start_date__ & __feed_end_date__ <!-- (24) -->| Should be included
__feed_version__ <!-- (25) --> | Should be included
__feed_contact_email__ & __feed_contact_url__ <!-- (26) --> | Provide at least one

<h3 id="stops">stops.txt</h3>   

#### stop_id

###### Trip Planners

###### Arrival Predictions

* Stops that are in different physical locations (i.e., different designated precise locations for vehicles on designated routes to stop, potentially distinguished by signs, shelters, or other such public information, located on different street corners or representing different boarding facility such as a platform or bus bay, even if nearby each other) should have different __stop_ids__. <!-- (27) -->
* Maintain consistent __stop_id__ for the same stops across data iterations (see: [Dataset Publishing & General Practices](#publishing)). <!-- (28) -->

#### stop_name

###### Trip Planners

###### Timetables

###### Human Readability

* The __stop_name__ should match the agency's public name for the stop, station, or boarding facility, e.g. what is printed on a timetable, published online, and/or presented at the location. <!-- (29) -->
* When there is not a published stop name, follow consistent stop naming conventions throughout the feed. <!-- (30) -->
* Avoid use of abbreviations other than for places that are most commonly called by an abbreviated name. See Abbreviations under [All Files](#all-files). <!-- (31) -->

* Provide stop names in mixed case, following local conventions, as per recommendation for all customer-facing text fields. <!-- (32) -->

* By default, __stop_name__ should not contain generic or redundant words like “Station” or “Stop”, but some edge cases are allowed:

  * When it is actually part of the name (Union Station, Central Station)
  * When the __stop_name__ is too generic (like the name of the city). “Station” emphasizes that the stop is the train station of that city.

#### stop_lat & stop_lon

###### Trip Planners

* Stop locations should be as accurate possible. Stop locations should have an error of **_no more_** than four meters when compared to the actual stop position. <!-- (34) -->
* Stop locations should be placed very near to the pedestrian right of way where a passenger will board (i.e. correct side of the street) <!-- (35) -->
* If a stop location is shared across separate feeds (i.e. two agencies use exactly the same stop / boarding facility), indicate the stop is shared by using the exact same __stop_lat__ and __stop_lon__ for both stops. <!-- (36) -->

#### stop_code

* Should be included in GTFS if there are passenger-facing stop numbers or short identifiers. <!-- (37) -->

#### stop_id

* __stop_id__ is an internal ID, not intended to be shown to passengers. <!-- (38) -->

#### parent_station & location_type

###### Trip Planners

###### Arrival Predictions

###### Timetables

* Many stations or terminals have multiple boarding facilities (depending on mode, they might be called a bus bay, platform, wharf, gate, or other term). In such cases, feed producers should describe stations, boarding facilities (also called child stops), and their relation. <!-- (40) -->
  * The station or terminal should be defined as a record in [`stops.txt`](#stops) with `location_type = 1`.
  * Each boarding facility should be defined as a stop with `location_type = 0`. The e parent_station field should reference the stop_id of the station the boarding is in.
* When naming the station and child stops, set names that are well recognized by riders, and can help riders to identify the station and boarding facility (bus bay, platform, wharf, gate, etc.). <!-- (41) -->

| Parent Station Name | Child Stop Name |
| ------------------- | --------------- |
| Chicago Union Station | Chicago Union Station Platform |
| [San Francisco Ferry Building Terminal](/best-practices/images/sf-ferry-building.png) | San Francisco Ferry Building Terminal Gate E |
| Downtown Transit Center | Downtown Transit Center Bay B |

<h3 id="stop-times">stop_times.txt</h3>

* Non-revenue (deadhead) trips that do not provide passenger service should be marked with __pickup_type__ and __drop_off_type__ value of `1` for all __stop_times__ rows.<!-- 13 -->
* The __timepoint__ field should be provided. It specifies which __stop_times__ the operator will attempt to strictly adhere to (`timepoint=1`), and that other stop times are estimates (`timepoint=0`).<!-- (44) -->

#### arrival_time & departure_time

###### Trip Planners

###### Timetables

###### Arrival Predictions

* Should specify times whenever possible, including non-binding estimated or interpolated times between timepoints. <!-- (45) -->

###### Trip Planners

###### Timetables

###### Arrival Predictions

* Internal “timing points” for monitoring operational performance and other places such as garages that a passenger cannot board should be marked with `pickup_type = 1` (no pickup available) and `drop_off_type = 1` (no drop off available). <!-- (46) -->

#### stop_headsign

###### Trip Planners

###### Timetables

###### Accessibility Analysis  

* Provide __stop_headsign__ values in cases when the text displayed on the headsign changes during a trip. The headsign in the GTFS should also correspond to signs in the stations. __stop_headsign__ values override the __trip_headsign__ (in `trips.txt`). __stop_headsign__ values do not “carry down” to subsequent stops, and therefore values must be repeated if the stop headsign remains the same. <!-- (47) -->

Examples:

> * In NYC, for the 2 going southbound:
>   * “Manhattan & Brooklyn” until Manhattan is reached.
>   * “Downtown & Brooklyn” until Downtown Manhattan is reached.
>   * “Brooklyn” until Brooklyn is reached.
>   * “Brooklyn (New Lots Av)” once Brooklyn is reached.

> * In Boston, for the Red Line going southbound, for the Braintree branch:
>   * “Inbound to Braintree” until downtown is reached.
>   * “Braintree” when in downtown.
>   * “Outbound to Braintree” after downtown.

In those two cases, “Southbound” would mislead customers, since it isn’t used in the station signs.

#### shape_dist_traveled

* Must be provided for routes that have looping or inlining (the vehicle crosses or travels over the same portion of alignment in one trip). [See: shapes.shape_dist_traveled recommendation.] <!-- (48) -->

[Case] Loop routes: Loop routes require special __stop_times__ considerations. (See: [Loop route case](#loop-routes))

<h3 id="transfers">transfers.txt</h3>

###### Trip Planners

#### transfers.transfer_type

__transfers.transfer_type__ can be one of four values [defined in the GTFS](https://developers.google.com/transit/gtfs/reference/transfers-file). These __transfer_type__ definitions are quoted from the GTFS Specification below, _in italics_, with additional practice recommendations. <!-- (49) -->

<q>0 or (empty): This is a recommended transfer point between two routes.</q> <!-- (50) -->

  * If there are multiple transfer opportunities that include a superior option (i.e. a transit center with additional amenities or a station with adjacent or connected boarding facilities/platforms), specify a recommended transfer point. A change to the Specification — “recommended transfer point between ~~two~~ routes” — would make this definition more precise, as a recommended transfer point applies to all routes.

<q>1: This is a timed transfer point between two routes. The departing vehicle is expected to wait for the arriving one, with sufficient time for a passenger to transfer between routes.</q>

  * This transfer type overrides a required interval to reliably make transfers.  As an example, Google Maps assumes that passengers need 3 minutes to safely make a transfer. Other applications may assume other defaults. <!-- (51) -->

<q>2: This transfer requires a minimum amount of time between arrival and departure to ensure a connection. The time required to transfer is specified by min_transfer_time.</q>

  * Specify minimum transfer time if there are obstructions or other factors which increase the time to travel between stops. <!-- (52) -->

<q>3: Transfers are not possible between routes at this location.</q> <!-- (53) -->

  * Specify this value if transfers are not possible because of physical barriers, or if they are made unsafe or complicated by difficult road crossings or gaps in the pedestrian network.

If in-seat (block) transfers are allowed between trips, then the last stop of the arriving trip must be the same as the first stop of the departing trip. <!-- (55) -->

<h3 id="trips">trips.txt</h3>

* **_See special case for loop routes:_** Loop routes are cases where trips start and end at the same stop, as opposed to linear routes, which have two distinct termini. Loop routes must be described following specific practices. [See Loop route case below.](#loop-routes)
* **_See special case for lasso routes:_** Lasso routes are a hybrid of linear and loop geometries, in which vehicles travel on a loop for only a portion of the route. Lasso routes must be described following specific practices. [See Lasso route case below.](#lasso-routes)

#### trips.trip_headsign

###### Trip Planners

* Do not provide route names (matching __route_short_name__ and __route_long_name__) in the __trip_headsign__ or __stop_headsign__ fields. <!-- (98) -->
* Should contain destination, direction, and/or other trip designation text shown on the headsign of the vehicle which may be used to distinguish amongst trips in a route. Consistency with direction information shown on the vehicle is the primary and overriding goal for determining headsigns supplied in GTFS datasets. Other information should be included only if it does not compromise this primary goal. If headsigns change during a trip, override __trip_headsign__ with __stop_times.stop_headsign__. Below are recommendations for some possible cases. <!-- (58) -->
  * Destination-only: Provide the terminus destination, e.g. “Transit Center”, “Portland City Center”, or “Jantzen Beach” <!-- (58A) -->
  * Destinations with waypoints: <destination> via <waypoint> “Highgate via Charing Cross”. If waypoint(s) are removed from the headsign show to passengers after the vehicle passes those waypoints, use stop_times.stop_headsign to set an updated headsign. <!-- (58B) -->
  * Regional placename with local stops: If there will be multiple stops inside the city or borough of destination, use stop_times.stop_headsign once reaching the destination city. <!-- (58C) -->
  * Direction-only: Indicate using terms such as “Northbound”, “Inbound”, “Clockwise,” or similar directions. <!-- (58D) -->
  * Direction with destination: <direction> to <terminus name> e.g. “Southbound to San Jose” <!-- (58E) -->
  * Direction with destination and waypoints: <direction> via <waypoint> to <destination> (“Northbound via Charing Cross to Highgate”). <!-- (58F) -->
* Do not begin a headsign with the words “To” or “Towards”.


#### direction_id

###### Trip Planners

###### Timetables

###### Human Readability

* If trips on a route service opposite directions, distinguish these groups of trips with the __direction_id__ field, using values 0 and 1. <!-- (64) -->
* Use values 0 and 1 consistently throughout the dataset. i.e. <!-- (65) -->
  * if 1 = Outbound on the Red route, then 1 = Outbound on the Green route
  * if 1 = Northbound on Route X, then 1 = Northbound on Route Y
  * if 1 = clockwise on Route X then 1 = clockwise on Route Y.

<h3 id="frequencies">frequencies.txt</h3>

###### Trip Planners

###### Timetables

###### Arrival Predictions

###### Human Readability

* Actual stop times are ignored for trips referenced by `frequencies.txt`; only travel time intervals between stops are significant for frequency-based trips. For clarity/human readability, it is recommended that the first stop time of a trip referenced in frequencies.txt should begin at 00:00:00 (first __arrival_time__ value of 00:00:00). <!-- (99) -->

* __block_id__ can be provided for frequency-based trips. <!-- (101) -->

<h3 id="routes">routes.txt</h3>

###### Trip Planners

###### Timetables

#### agency_id
* Must be included if it is defined in agency.txt. <!-- (68) -->

#### route_short_name
* Should be the commonly-known passenger name of the service, no longer than 12 characters. Include __route_short_name__ if there is a brief service designation. <!-- (71) -->

#### route_long_name
* The definition from Specification reference:

<q>This name is generally more descriptive than the __route_short_name__ and will often include the route's destination or stop. At least one of __route_short_name__ or __route_long_name__ must be specified, or potentially both if appropriate. If the route does not have a long name, please specify a __route_short_name__ and use an empty string as the value for this field.</q>

* Examples of types of long names are below:  <!-- (73) -->
  * Primary travel path or corridor. Examples:
    * (using “route_short_name” / “route_long_name” notation): [“N”/“Judah”](https://www.sfmta.com/getting-around/transit/routes-stops/n-judah) in San Francisco, Cal. (agency: Muni)
    * [“6”/“ML King Jr Blvd”](https://trimet.org/schedules/r006.htm) in Portland, Or. (agency: TriMet) List of primary destinations or termini.
    * (using “route_short_name” / “route_long_name” notation): [“6”/“Nation - Étoile”](http://www.ratp.fr/informer/pdf/orienter/f_plan.php?nompdf=m6) in Paris, France (agency RATP)
    * [“U2”-“Pankow – Ruhleben”](http://www.bvg.de/images/content/linienverlaeufe/LinienverlaufU2.pdf) in Berlin, Germany (agency BVG).
  * description of the service (e.g. [“Hartwell Area Shuttle”](http://128bc.org/rev-hartwell-area-shuttle/))
* __route_long_name__ should not contain the __route_short_name__. <!-- (72) -->
* Include the full designation including a service identity when populating __route_long_name__. Examples: <!-- (69) -->
  * In Portland, Oregon, USA the TriMet’s light rail services are branded as “MAX Light Rail”. The __route_long_name__ should include the brand (MAX) and the more-specific route designation i.e.b “MAX Red Line”, “MAX Blue Line”, etc.
  * In Albuquerque, New Mexico USA, ABQ Ride in has special express routes called Rapid Ride. __route_long_name__ for these routes should be Rapid Ride Red Line, Rapid Ride Blue Line, etc.

#### route_id

* All trips on a given named route should reference the same __route_id__. <!-- (74) -->
  * Different directions of a route should not be separated into different __route_id__ values.
  * Different spans of operation of a route should not be separated into different __route_id__ values (do not do “Transit Center - Downtown AM” and “Transit Center - Downtown PM”).
  * For further discussion of when to add new records in routes.txt, see [Branches](#branches).
* If a route group includes distinctly named branches (e.g. 1A and 1B), follow recommendations in the route [branches](#branches) case to determine __route_short_name__ and __route_long_name__. <!-- (70) -->
* Maintain consistent identifiers (ID values) from one version to the next of the same feed. <!-- (75) -->

#### route_color & route_text_color

* Should be consistent with signage and printed and online customer information (and thus not included if they do not exist in other places).  <!-- (76) -->

<h3 id="shapes">shapes.txt (alignments)</h3>

###### Trip Planners

###### Accessibility

###### Arrival Predictions

* Ideally, for alignments that are shared (i.e. in a case where Routes 1 and 2 operate on the same segment of roadway or track) then the shared portion of alignment should match exactly. This helps to facilitate high-quality transit cartography. <!-- (77) -->
* Alignments should follow the centerline of the right of way on which the vehicle travels. This could be either the centerline of the street if there are no designated lanes, or the centerline of the side of the roadway that travels in the direction the vehicle moves. <!-- (78) -->
  * Alignments should not “jag” to a curb stop, platform, or boarding location.

#### shape_dist_traveled

* Must be provided in both `shapes.txt` and `stop_times.txt` if an alignment includes looping or inlining (the vehicle crosses or travels over the same portion of alignment in one trip). <!-- (79) -->

* The __shape_dist_traveled__ field allows the agency to specify exactly how the stops in the `stop_times.txt` file fit into their respective shape. A common value to use for the __shape_dist_traveled__ field is the distance from the beginning of the shape as traveled by the vehicle (think something like an odometer reading).
* Route alignments (in `shapes.txt`) should be within 100 meters of stop locations which a trip serves.  <!-- (80) -->
* Simplify alignments so that `shapes.txt` does not contain extraneous points (i.e. remove extra points on straight-line segments; see discussion of line simplification problem). <!-- (81) -->

<h3 id="calendar">calendar.txt and calendar_dates.txt</h3>

###### Human Readability

###### Timetables

* `calendar_dates.txt` should only contain a limited number of exceptions to the schedule. Regularly-scheduled service should be configured using `calendar.txt`.
* Including a __calendar.service_name__ field can also increase the human readability of GTFS, although this is not adopted in the spec.

<h3 id="fare-rules">fare_rules.txt and fare_attributes.txt</h3>

###### Trip Planners

###### Accessibility Analysis

* __agency_id__ should be included in `fare_attributes.txt` if it the field is included in `agency.txt`. <!-- (84) -->
* If a fare system cannot be accurately modeled, avoid further confusion and leave it blank. <!-- (85) -->
* Include fares (`fare_attributes.txt` and `fare_rules.txt`) and model them as accurately as possible. In edge cases where fares cannot be accurately modeled, the fare should be represented as more expensive rather than less expensive so customers will not attempt to board with insufficient fare. If the vast majority of fares cannot be modeled correctly, do not include fare information in the feed. <!-- (86) -->


<h2 id="by-case">Practice Recommendations Organized by Case</h2>

This section covers particular cases with implications across files and fields.

<h3 id="loop-routes">Loop Routes</h3>

On loop routes, vehicles’ trips begin and end at the same location (sometimes a transit or transfer center). Vehicles usually operate continuously and allow passengers to stay onboard as the vehicle continues its loop.

#### trips.trip_id
* Model the complete round-trip for the loop with a single trip.  <!-- (102) -->

#### stop_times.stop_id
* Include the first/last stop twice in stop_times.txt for the trip that is a loop. Example below. <!-- (87) -->

| trip_id | stop_id | stop_sequence |
| ------- | ------- | ------------- |
|   9000  |   101   |       1       |
|   9000  |   102   |       2       |
|   9000  |   103   |       3       |
|   9000  |   101   |       4       |

Often, a loop route may include first and last trips that do not travel the entire loop. Include these trips as well.

#### trips.direction_id

* If loop operates in opposite directions (i.e. clockwise and counterclockwise), then designate __direction_id__ as `0` or `1`. <!-- (89) -->

#### trips.block_id

* Indicate continuous loop trips with the same __block_id__. <!-- (90) -->

<h3 id="lasso-routes">Lasso Routes</h3>

Lasso routes are loop-routes from A to A via B with three sections:
* straight section from A to B;
* loop from and to B;
* straight section from B to A.

Examples: subway routes ([Chicago](http://www.transitchicago.com/assets/1/maps/L_Map_March_2016_s_lite.pdf)) or bus suburb to downtown routes ([St. Albert](https://stalbert.ca/uploads/PDF-infosheets/201_207_Fall_2016.pdf) or [Edmonton](http://webdocs.edmonton.ca/transit/route_schedules_and_maps/future/RT039.pdf)).  
See CTA Brown Line ([CTA website](http://www.transitchicago.com/brownline/) and [TransitFeeds](https://transitfeeds.com/p/chicago-transit-authority/165/latest/route/Brn))

#### stop_times.stop_headsign <!-- (94) -->
* The stops along the A-B section will be passed through in both directions. __stop_headsign__ facilitates distinguishing travel direction. Therefore, providing __stop_headsign__ is recommended for these trips. Examples:
  * “A via B”
  * “A”
For Chicago Transit Authority’s [Purple Line](http://www.transitchicago.com/purpleline/):
  * “Southbound to Loop”
  * “Northbound via Loop”
  * “Northbound to Linden”
For Edmonton Transit Service bus lines, for example [the 39](http://webdocs.edmonton.ca/transit/route_schedules_and_maps/future/RT039.pdf):
  * “Rutherford”
  * “Century Park”



#### trip.trip_headsign <!-- (95) -->

* The trip headsign should be a global description of the trip, like displayed in the schedules. Could be “Linden to Linden via Loop” (Chicago example), or “A to A via B” (generic example).

<h3 id="branches">Branches</h3>

Some routes may share significant portions of alignment and stops, but also include sections that serve distinct stops and alignments. The primary route name and relationship to its branches may be indicated by route name(s), headsigns, and trip short name.

In naming branch routes, it is recommended to follow other passenger information materials. Below are descriptions and examples of two cases: <!-- (97) -->
* If timetables and on-street signage represent two distinctly named routes (e.g. 1A and 1B), then present this as such in the GTFS, using the __route_short_name__ and/or __route_long_name__ fields. <!-- (97A) -->
* __Example__: GoDurham Transit [routes 2, 2A, and 2B](http://admin.gotransitnc.org/sites/default/files/godurham/aug2016/Route%202%20PDF%20August%202016.pdf) share a common alignment throughout the majority of the route, but they vary in several different aspects.
  * Route 2B serves additional stops in a spur of the shared alignment path.
  * Routes 2A and 2B operate daytime hours M-Sat.
  * Route 2 runs nights, Sundays, and holidays.

* If agency-provided information describes branches as the same named route, then utilize the __trips.headsign__, __stop_times.headsign__, and/or __trips.trip_short_name__ fields. <!-- (97B) -->
* __Example__: GoTriangle [route 300](http://admin.gotransitnc.org/sites/default/files/maps-and-schedules/gotriangle/RoutesAndSchedules-1561.pdf) travels to different locations depending on the time of day. During peak commuter hours extra legs are added onto the standard route to accommodate workers entering and leaving the city.


<!-- {To-do: illustrate with examples of branching; find two types of branching -- one where there should be a single routes.txt record and variants are indicated with trip_headsign and/or trip_short_name, and another where there should be two different records in routes.txt}
Gold Coast Transit Route 1A/1B

Como Connect Route 2 {remove this; directions are branded differently -- somewhat irregular/obscure} (Direction A = Clockwise; Direction B = Counterclockwise) -->

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

The GTFS Best Practices Working Group consists of public transportation providers, developers of GTFS-consuming applications, consultants, and academic organizations to define common practices and expectations for GTFS data. The goals of this working group are to support greater interoperability of data data. Further goals are defined in the “Objectives”.

Members of this working group include:

* Apple
* Cambridge Systematics
* Capital Metro
* Center for Urban Transportation Research at University of South Florida
* Conveyal
* Google
* IBI Group
* Mapzen
* Microsoft
* Moovel
* Oregon Department of Transportation
* Swiftly
* Transit
* Trillium
* TriMet
* World Bank

To join the working group, email [gtfs-wg@rmi.org](mailto:gtfs-wg@rmi.org).

The GTFS Best Practices Working Group is convened and facilitated by Rocky Mountain Institute, a non-profit organization transforming global energy use.


<!-- [Logo file: http://www.nwp.com/energysummit16/images/RockyMountainInstitute.png] -->
