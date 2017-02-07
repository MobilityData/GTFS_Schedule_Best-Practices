---
layout: best-practices
---

# GTFS Data Best Practices

<h2 id="introduction">Introduction</h2>

This is an example of an inserted photo:

![Lucille looks mad!](/best-practices/images/lucille.jpg)
<figcaption>Caption text?</figcaption>

These are recommended practices for describing public transportation services in the [General Transit Feed Specification (GTFS)](https://developers.google.com/transit/gtfs/reference/). These practices have been synthesized from the experience of the [GTFS Best Practices working group]() members and [application-specific GTFS practice recommendations](http://www.transitwiki.org/TransitWiki/index.php/Best_practices_for_creating_GTFS).

#### __Document Structure__

Recommended practices are organized into three primary sections

* __[Dataset Publishing & General Practices](#publishing):__ These practices relate to the overall structure of the GTFS dataset and to the manner in which GTFS datasets are published.
* __[Practice Recommendations Organized by File](#by-file):__ Recommendations are organized by file and field in the GTFS to facilitate mapping practices back to the official GTFS reference.
* __[Practice Recommendations Organized by Case](#by-case):__ With particular cases, such as loop routes, practices may need to be applied across several files and fields. Such recommendations are consolidated in this section.

#### __System Tags__

Five different tags are included throughout the list of practices. These tags indicate the type of systems that require the practice being described.

###### Trip Planners
* These practices improve customer experience in applications like Google Maps that are used for trip planning.

###### Human Readability
* These practices help maintain the ability for a human reader to unzip and examine GTFS files.

###### Arrival Predictions
* These practices allow arrival prediction software to create real-time arrival estimates related to the schedules in trips.txt and stop_times.txt.

###### Planning and Analysis
* Software and projects such as OpenTripPlanner Analyst, Open Transit Indicators, Accessibility Observatory, National Transit Map, AllTransit and Remix provide summaries and attributes of service based on GTFS data that follow these practices.

###### Timetables
* These practices support the creation of HTML timetables based on GTFS, such as with the GTFS-to-HTML software.

Each practice recommendation is numbered.

<h2 id="publishing">Dataset Publishing & General Practices</h2>
1.  Datasets should be published at a public, permanent URL, including the zip file name. (e.g., [http://www.agency.org/gtfs/gtfs.zip](http://www.agency.org/gtfs/gtfs.zip)).  The URL should be directly accessible/downloadable by software applications and should not require a manual login to access the file.

2.  While it is recommended (and the most common practice) to make a GTFS dataset openly downloadable, if a data provider needs  to control access to GTFS for licensing or other reasons, it is recommended to control access to the GTFS dataset using a system of API keys, which will facilitate automatic downloads.

3.  GTFS data is published in iterations so that a single file at a stable location always contains the latest official description of service for a transit agency (or agencies).

4.  Maintain persistent identifiers (id fields) for stop_id, route_id, and agency_id across data iterations whenever possible.

5.  One GTFS dataset should contain current and upcoming service (sometimes called a “merged” dataset).

* At any time, the published GTFS dataset should be valid for for at least the next 7 days, and ideally for as long as the operator is confident that the schedule will continue to be operated.
* If possible, the GTFS dataset should cover at least the next 30 days of service.

8.  If a service modification will go into effect in 7 days or fewer, express this service change through a GTFS-realtime feed (service advisories or trip updates) rather than static GTFS dataset.

9.  The web-server hosting GTFS data should be configured to correctly report the file modification date (see https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html, under Section 14.29 Last-Modified).

10.  Remove old services (expired calendars) from the feed.

<h2 id="by-file">Practice Recommendations Organized by File</h2>

This section shows practices organized by file & field, aligning with the GTFS reference.

### All Files

12.  __Mixed case__:
All customer-facing text strings (including stop names, route names, and headsigns) should use Mixed Case (not ALL CAPS), following local conventions for capitalization of place names on displays capable of displaying lower case characters.

| Examples: | Other Examples: |
| --------- | ------------ |
| Brighton Churchill Square | My House |
| Villiers-sur-Marne | My Work |
| Market Street | My Favorite Cafe (changes quarterly) |

14.  Abbreviations: Avoid use of abbreviations throughout the feed for names and other text (e.g. St. for Street) unless a location is called by its abbreviated name (e.g. “JFK Airport”). Abbreviations may be problematic for accessibility by screen reader software and voice/audio user interfaces. Consuming software can be engineered to reliably convert full words to abbreviations for display, but converting from abbreviations to full words is prone to more risk of error.

<h3 id="agency">agency.txt</h3>

###### Trip Planners
###### Human Readability
###### Timetables
###### Planning and Analysis

agency_id <!-- 15 --> | Should be included, even if there is only one agency in the feed. (See also: recommendation to include agency_id in `routes.txt` and `fare_attributes.txt`.)
agency_lang <!-- 16 --> | Field should be included.
agency_phone <!-- 17 --> | Should be included unless no such customer service phone exists.
agency_email <!-- 18 --> | Should be included unless no such customer service email exists.
agency_fare_url <!-- 19 --> | Should be included unless the agency is fully fare-free, and `fare_attributes.txt` is included to indicate that the system is fare-free.

<h3 id="feed-info">feed_info.txt</h3>

###### Trip Planners
###### Human Readability
20.  **feed_info.txt** should be included, with all fields, below.
* 21.  **feed_publisher_name**
* 22.  **feed_publisher_url**
* 23.  **feed_lang**
* 24.  **feed_start_date**
102. **feed_end_date**
25.  feed_version
26.  feed_contact_email & feed_contact_url: Provide at least one
stops.txt
stop_id
Trip Planners     Arrival Predictions   
27.  Stops that are in different physical locations (i.e., different designated precise locations for vehicles on designated routes to stop, potentially distinguished by signs, shelters, or other such public information, located on different street corners or representing different boarding facility such as a platform or bus bay, even if nearby each other) should have different stop_ids.
28.  Maintain consistent stop_id for the same stops across data iterations (see: Dataset publishing & iterations).  
stop_name
  Trip Planners     Timetables  Human Readability      
 	29. The stop_name should  mMatch the agency's public name for the stop, station, or boarding facility, e.g. what is printed on a timetable, published online, and/or presented at the location.
30.  When there is not a published stop name, follow consistent stop naming conventions throughout the feed.
31.  Avoid use of abbreviations other than for places that are most commonly called by an abbreviated name. See Abbreviations.
32.  Provide stop names in mixed title case, following local conventions, as per recommendation for all customer-facing text fields.
33.  By default, stop_name should not contain generic or redundant words like “Station” or “Stop”, but some edge cases are allowed:
When it is actually part of the name (Union Station, Central Station)
When the stop_name is too generic (like the name of the city). “Station” emphasizes that the stop is the train station of that city.
stop_lat and stop_lon
 Trip Planners    
34.  Stop locations should be as accurate possible. Stop locations should have an error of no more than 4 meters when compared to the actual stop position.
35.  Stop locations should be placed very near to the pedestrian right of way where a passenger will board (i.e. correct side of the street)
36.  If a stop location is shared across separate feeds (i.e. two agencies use exactly the same stop / boarding facility), indicate the stop is shared by using the exact same stop_lat and stop_lon for both stops.
37.  stop_code should be included in GTFS if there are passenger-facing stop numbers or short identifiers. It is recommended to provide numbers only to support numeric input (such as a telephone keypad).
38.  stop_id is an internal ID, not intended to be shown to passengers.
  Trip Planners     Arrival Predictions    Timetables
39.  parent_station & location_type Provide station record when there are multiple boarding facilities in a single station or terminal.
  Trip Planners
40.  Many stations or terminals have multiple boarding facilities (depending on mode, they might be called a bus bay, platform, wharf, gate, or other term).
The station or terminal should be defined as a record in stops.txt with location_type = 1.
Each boarding facility should be defined as a stop with location_type = 0. The e parent_station field should reference the stop_id of the station the boarding is in.
41.  “When naming the station and child stops, set names that are well recognized by riders, and can help riders to identify the station and boarding facility (bus bay, platform, wharf, gate, etc.).

Examples
Parent station name = Chicago Union Station;
Child stop name = Chicago Union Station Platform 1
Parent station name = Downtown Transit Center
Child stop name = Downtown Transit Center Bay B


42.  If no parent_station is defined, do not put any boarding facility information in the stop_name.
43.  A station record (i.e. a stops.txt record with location_type=1) cannot have boarding facilityplatform information (platform, wharf, etc.); this should only be defined for child stops.
stop_times.txt
13. Non-revenue (deadhead) trips that do not provide passenger service should be marked with pickup_type and drop_off_type value of 1 for all stop_times rows.
44.  The timepoint field should be provided. It specifies which stop_times the operator will attempt to strictly adhere to (timepoint=1), and that other stop times are estimates (timepoint=0).timepoint field, which specifies timed stops and/or published stops in a schedule that the vehicle strictly adheres to, should be provided.
Trip Planners     Timetables    Arrival predictions  
45.  arrival_time and departure_time fields should specify times whenever possible, including non-binding estimated or interpolated times between timepoints.
Trip Planners     Timetables    Arrival predictions  
46.  Internal “timing points” for monitoring operational performance and other places such as garages and bus garages that ado not represent places a passenger cannot board should be marked as such with pickup_type = 1 (no pickup available) and drop_off_type = 1 (no drop off available).
 Trip Planners     Timetables     Accessibility Analysis  
47.  stop_headsign: Provide stop_headsign values in cases when the text displayed on the headsign changes during a trip. The headsign in the GTFS should also correspond to signs in the stations. stop_headsign values override the trip_headsign (in trips.txt). stop_headsign values do not “carry down” to subsequent stops, and therefore values must be repeated if the stop headsign remains the same.
Examples:
In NYC, for the 2 going southbound:
“Manhattan & Brooklyn” until Manhattan is reached.
“Downtown & Brooklyn” until Downtown Manhattan is reached.
“Brooklyn” until Brooklyn is reached.
“Brooklyn (New Lots Av)” once Brooklyn is reached.
In Boston, for the Red Line going southbound, for the Braintree branch:
“Inbound to Braintree” until downtown is reached.
“Braintree” when in downtown.
“Outbound to Braintree” after downtown.
In those two cases, “Southbound” would mislead customersbe a bad choice, since it isn’t used in the station signs.
48.  shape_dist_traveled must be provided for routes that have looping or inlining (the vehicle crosses or travels over the same portion of alignment in one trip). [See: shapes.shape_dist_traveled recommendation.]
[Case] Loop routes: Loop routes require special stop_times considerations. [See: Loop route case, below.]
transfers.txt
 Trip Planners  
49.  transfers.transfer_type can be one of 4 values defined in the GTFS. These transfer_type definitions are quoted from the Specification below, in italics, with additional practice recommendations.
50.  “0 or (empty): This is a recommended transfer point between two routes.” {Italicized text quoted from the GTFS reference.}
If there are multiple transfer opportunities that include a superior option (i.e. a transit center with additional amenities or a station with adjacent or connected boarding facilities/platforms), specify a recommended transfer point. A change to the Specification — “recommended transfer point between two routes” — would make this definition more precise, as a recommended transfer point applies to all routes.
51.  “1: This is a timed transfer point between two routes. The departing vehicle is expected to wait for the arriving one, with sufficient time for a passenger to transfer between routes.”
This transfer type overrides a required interval to reliably make transfers.  As an example, Google Maps assumes that passengers need 3 minutes to safely make a transfer. Other applications may assume other defaults.
52.  “2: This transfer requires a minimum amount of time between arrival and departure to ensure a connection. The time required to transfer is specified by min_transfer_time.”
Specify minimum transfer time if there are obstructions or other factors which increase the time to travel between stops.
53.  “3: Transfers are not possible between routes at this location”.
Specify this value if transfers are not possible because of physical barriers, or if they are made unsafe or complicated by difficult road crossings or gaps in the pedestrian network.
54.  There are new transfer_type values proposed (4 and 5) to define in-seat transfer availability.
55.  If in-seat (block) transfers are allowed between trips, then the last stop of the arriving trip must be the same as the first stop of the departing trip.
56.  Currently, there should only be a single record per transfers.from_stop_id and transfers.to_stop_id ordered pair.
trips.txt
See special case for loop routes: Loop routes are cases where trips start and end at the same stop, as opposed to linear routes, which have two distinct termini. Loop routes must be described following specific practices. [See Loop route case below.]
See special case for lasso routes: Lasso routes are a hybrid of linear and loop geometries, in which vehicles travel on a loop for only a portion of the route. Lasso routes must be described following specific practices. [See Lasso route case below.]
trips.trip_headsign
 Trip Planners    
98. [out-of-order]. Do not provide route names (matching route_short_name and route_long_name) in the trip_headsign or stop_headsign fields.
62.  If no headsign is shown on the vehicle and there are no meaningful directional distinctions among trips and no direction information is shown on the vehicle, then generally the trip_headsign field can be left blank. In most of these cases, the headsign shown on the operating vehicle is a route name (e.g. “Green Route”), rather than a destination.
58.  trip_headsign should contain destination, direction, and/or other trip designation text shown on the headsign of the vehicle which may be used to distinguish amongst trips in a route. Consistency with direction information shown on the vehicle is the primary and overriding goal for determining headsigns supplied in GTFS datasets. Other information should be included only if it does not compromise this primary goal. If headsigns change during a trip, override trip_headsign with stop_times.stop_headsign. Below are recommendations for some possible cases.
58 A.) Destination-only: Provide the terminus destination, e.g. “Transit Center”, “Portland City Center”, or “Jantzen Beach”
58 B.) Destinations with waypoints: <destination> via <waypoint> “Highgate via Charing Cross”. If waypoint(s) are removed from the headsign show to passengers after the vehicle passes those waypoints, use stop_times.stop_headsign to set an updated headsign.
58 C.) Regional placename with local stops: If there will be multiple stops inside the city or borough of destination, use stop_times.stop_headsign once reaching the destination city.
58 D.) Direction-only: Indicate using terms such as “Northbound”, “Inbound”, “Clockwise,” or similar directions.
58 E.) Direction with destination: <direction> to <terminus name> e.g. “Southbound to San Jose”
58 F.) Direction with destination and waypoints: <direction> via <waypoint> to <destination> (“Northbound via Charing Cross to Highgate”).
57.  Do not begin a headsign with the words “To” or “Towards”.


direction_id
  Trip Planners     Timetables     Human Readability
64.  If trips on a route service opposite directions, distinguish these groups of trips with the direction_id field, using values 0 and 1.
65.  Use values 0 and 1 consistently throughout the dataset. I.e.
if 1 = Outbound on the Red route, then 1 = Outbound on the Green route
if 1 = Northbound on Route X, then 1 = Northbound on Route Y
if 1 = clockwise on Route X then 1 = clockwise on Route Y.
66.  Leave direction_id blank if there is only one meaningful direction of travel in a route (e.g. a loop route that only loops in one direction).

frequencies.txt
 Trip Planners  /   Timetables  / Arrival Predictions  / Human Readability
67.  It is recommended not to use frequencies.txt for any trip with different first arrival and departure times because of an ambiguity of the Specification. The GTFS reference defines that “the [frequencies.]start_time field specifies the time at which service begins with the specified frequency.” The Spec does not specify if service begins when the vehicle arrives at the first stop, or departs. See GTFS-changes for more discussion.
99. [out-of-order]. Actual stop times are ignored for trips referenced by frequencies.txt; only travel time intervals between stops are significant for frequency-based trips. For clarity/human readability, it is recommended that the first stop time of a trip referenced in frequencies.txt should begin at 00:00:00 (first arrival_time value of 00:00:00).

100. [out-of-order]. For trips defined in frequencies.txt that are loop routes (successive trips are made by the same vehicle, and vehicle trips begin and end at the same stop), block_ids should be provided. For trips referenced in frequencies.txt that are not loop routes, block_id should be empty.

101. [out-of-order]. block_id can be provided for frequency-based trips.
routes.txt  
 Trip Planners  /   Timetables
68.  agency_id must be included if it is defined in agency.txt.
69.  Include the full designation including a service identity when populating route_long_name. For example, in Portland, Oregon, the TriMet’s light rail services are branded as “MAX Light Rail”. The route_long_name should include the brand (MAX) and the more-specific route designation i.e.b “MAX Red Line”, “MAX Blue Line”, etc.
70.  If a route group includes distinctly named branches (e.g. 1A and 1B), follow recommendations in the route branches case to determine route_short_name and route_long_name.
71.  route_short_name should be the commonly-known passenger name of the service, no longer than 12 characters. Include route_short_name if there is a brief service designation.
72.  route_long_name should not contain the route_short_name.
73.  route_long_name definition from Specification reference: “This name is generally more descriptive than the route_short_name and will often include the route's destination or stop. At least one of route_short_name or route_long_name must be specified, or potentially both if appropriate. If the route does not have a long name, please specify a route_short_name and use an empty string as the value for this field.” Examples of types of long names are below:
Primary travel path or corridor. For example (using “route_short_name” / “route_long_name” notation): “N”/“Judah” in San Francisco, Cal. (agency Muni) or “6”/“ML King Jr Blvd” in Portland, Or. (agency TriMet)List of primary destinations or termini. For example (using “route_short_name” / “route_long_name” notation): “6”/“Nation - Étoile” in Paris, France (agency RATP) or “U2”-“Pankow – Ruhleben” in Berlin, Germany (agency BVG).
description of the service (e.g. “Hartwell Area Shuttle”)
72.  route_long_name should not contain the route_short_name.
route_id
74.  All trips on a given named route should reference the same route_id.
Different directions of a route should not be separated into different route_id values.
Different spans of operation of a route should not be separated into different route_id values (do not do “Transit Center - Downtown AM” and “Transit Center - Downtown PM”).
For further discussion of when to add new records in routes.txt, see Branches.
75.  Maintain consistent identifiers (ID values) from one version to the next of the same feed.
76.  route_color and route_text_color should be consistent with signage and printed and online customer information (and thus not included if they do not exist in other places).
shapes.txt (alignments)
 Trip Planners    Accessibility    Arrival Predictions
77.  Ideally, for alignments that are shared (i.e. in a case where Routes 1 and 2 operate on the same segment of roadway or track) then the shared portion of alignment should match exactly. This helps to facilitate high-quality transit cartography.
78.  Alignments should follow the centerline of the right of way on which the vehicle travels. This could be either the centerline of the street if there are no designated lanes, or the centerline of the side of the roadway that travels in the direction the vehicle moves.
Alignments should not “jag” to a curb stop, platform, or boarding location.
79.  shape_dist_traveled must be provided in both shapes.txt and stop_times.txt if an alignment includes looping or inlining (the vehicle crosses or travels over the same portion of alignment in one trip).

The shape_dist_traveled field allows the agency to specify exactly how the stops in the stop_times.txt file fit into their respective shape. A common value to use for the shape_dist_traveled field is the distance from the beginning of the shape as traveled by the vehicle (think something like an odometer reading).
80.  Route alignments (in shapes.txt) should be within 100  meters of stop locations which a trip serves.
81.  Simplify alignments so that shapes.txt does not contain extraneous points (i.e. remove extra points on straight-line segments; see discussion of line simplification problem).
calendar.txt and calendar_dates.txt
 Human Readability  / Timetables
82.  calendar_dates.txt should only contain a limited number of exceptions to the schedule. Regularly-scheduled service should be configured using calendar.txt.
83.  Including a calendar.service_name field can also increase the human readability of GTFS, although this is not adopted in the spec.
fare_rules.txt and fare_attributes.txt
 Trip Planners     Accessibility Analysis
84.  agency_id should be included in fare_attributes.txt if it the field is included in agency.txt.
85.  If a fare system cannot be accurately modeled, avoid further confusion and leave it blank.
86.  Include fares (fare_attributes.txt and fare_rules.txt) and model them as accurately as possible. In edge cases where fares cannot be accurately modeled, the fare should be represented as more expensive rather than less expensive so customers will not attempt to board with insufficient fare. If the vast majority of fares cannot be modeled correctly, do not include fare information in the feed.


<h2 id="by-case">Practice Recommendations Organized by Case</h2>
This section covers particular cases with implications across files and fields.
Loop routes
On loop routes, vehicles’ trips begin and end at the same location (sometimes a transit or transfer center). Vehicles usually operate continuously and allow passengers to stay onboard as the vehicle continues its loop.

87.  stop_times.stop_id: Include the first/last stop twice in stop_times.txt for the trip that is a loop. Example below.
trip_id
stop_id
stop_sequence
9000
101
1
9000
102
2
9000
103
3
9000
101
4
Often, a loop route may include first and last trips that do not travel the entire loop. Include these trips as well. If the vehicle provides service before or after the central pulse location (where the vehicle returns at the top of the loop), also include those stops.
trips.direction_id
88.  if the loop operates in a single direction, then leave direction_id blank
89.  if loop operates in opposite directions (i.e. clockwise and counterclockwise), then designate direction_id as 0 or 1
90.  trips.block_id: Indicate continuous loop trips with the same block_id.
→ For trips referenced in frequencies.txt that are loop routes, block_ids should also be provided. Frequencies can only be used on a loop trip if the headway (frequencies.headway_secs) is greater than or equal to the operating time for the trip (last arrival_time - first departure_time). If headway is less than operating time for the trip, this will result in an overlapping block error.
91.  frequencies.txt: The Specification does not allow continuous loop routes through frequencies. Individual loops should be separately included in trips.txt, such that the interlining between loops can be included.
Lasso routes
Lasso routes are loop-routes from A to A via B with three sections:
straight section from A to B;
loop from and to B;
straight section from B to A.


Examples: subway routes (Chicago) or bus suburb to downtown routes (St. Albert or Edmonton).  
See CTA Brown Line (CTA website and TransitFeeds)

93.  trips.direction_id: empty.
The stops along the A-B section will be passed through in both directions. Therefore, assigning direction_id to the whole trip do not make sense. The direction_id should be kept blank for those trips.
94.  stop_times.stop_headsign:
The stops along the A-B section will be passed through in both directions., the only way to distinguish the two is to have different stop_headsign facilitates distinguishing travel direction. Therefore, providing stop_headsign is recommended for these trips. Examples:
“A via B”
“A”
For Chicago Transit Authority’s Purple Line:
“Southbound to Loop”
“Northbound via Loop”
“Northbound to Linden”
For Edmonton Transit Service bus lines, for example the 39:
“Rutherford”
“Century Park”



95.  trip.trip_headsign
The trip headsign should be a global description of the trip, like displayed in the schedules. Could be “Linden to Linden via Loop” (Chicago example), or “A to A via B” (generic example).
In-seat transfers & vehicle blocks
 Trip Planners     Arrival Predictions
trips.block_id “identifies the block to which the trip belongs. A block consists of two or more sequential trips made using the same vehicle, where a passenger can transfer from one trip to the next just by staying in the vehicle. The block_id must be referenced by two or more trips in trips.txt.” [GTFS reference - trips.txt file]

Trip planner and arrival prediction software have different requirements for vehicle block information:
Trip Planners only require sequential trips where passengers can make in-seat transfers to be indicated with block_id
Arrival prediction systems operate more reliably with block_id assigned for all trips, as it makes it possible to better match and compare vehicles to their scheduled service.
Recommended current practice
96.  This current difference in requirements makes it necessary to publish two GTFS datasets in cases where block_id is required for an arrival prediction system, but in-seat transfers are not universally allowed.
Specification change discussion
There is currently a proposal to add new types transfers to the GTFS (transfers.transfer_type). New transfer types proposed are:

4: In-seat transfer between these two stops / routes / trips is allowed
5: In-seat block transfer not allowed (even if two trips on the same block ID can be chained end to end here, the passenger must alight and walk to transfer between them)”

This discussion has resumed on November 18 on GTFS-changes.
Branches
Some routes may share significant portions of alignment and stops, but also include sections that serve distinct stops and alignments. The primary route nameA and relationship to its branches may be indicated by route name(s), headsigns, and trip short name.and relationship to a primar may be named to convey this. Gold Coast Transit routes 1A and 1B provide an example.



97.  In naming branch routes, it is recommended to follow other passenger information materials. Below are descriptions and examples of two cases:
	97A.) If timetables and on-street signage represent two distinctly named routes (e.g. 1A and
                            1B), then present this as such in the GTFS, using the route_short_name and/or
                            route_long_name fields.
            	           ex: GoDurham Transit routes 2, 2A, and 2B share a common alignment throughout the
                                   majority of the route, but they vary in several different aspects.
Route 2B serves additional stops in a spur of the shared alignment path.
Routes 2A and 2B operate daytime hours M-Sat.
Route 2 runs nights, Sundays, and holidays.

97B.) If agency-provided information describes branches as the same named route, then
                            utilize the trips.headsign, stop_times.headsign, and/or trips.trip_short_name fields.
	            Ex: GoTriangle route 300 travels to different locations depending on the time of   			             day. During peak commuter hours extra legs are added onto the standard route
                             to accommodate workers entering and leaving the city.





{To-do: illustrate with examples of branching; find two types of branching -- one where there should be a single routes.txt record and variants are indicated with trip_headsign and/or trip_short_name, and another where there should be two different records in routes.txt}
Gold Coast Transit Route 1A/1B

 Como Connect Route 2 {remove this; directions are branded differently -- somewhat irregular/obscure} (Direction A = Clockwise; Direction B = Counterclockwise)

About this Document
Objectives
The objectives of maintaining GTFS Best Practices is to
Improve end-user customer experience in public transportation apps
Make it easier for software developers to deploy and scale applications, products, and services
Facilitate the use of GTFS in various application categories (beyond its original focus on trip planning)
Linking to this document
Please link here in order to provide feed producers with guidance for correct formation of GTFS data. If your GTFS-consuming application involves particular requirements or recommendations for GTFS data practices, it is recommended to publish a document with those requirements or recommendations to supplement these common best practices.
How to propose or amend published GTFS Best Practices
GTFS applications and practice evolve, and so this document may need to be amended from time to time. To propose an amendment to this document, open a pull request in GitHub and advocate for the change. The GTFS Best Practices Working Group will meet quarterly to discuss and approve selected changes.

GTFS Best Practices Working Group {PAGE}
The GTFS Best Practices Working Group consists of public transportation providers, developers of GTFS-consuming applications, consultants, and academic organizations to define common practices and expectations for GTFS data. The goals of this working group are to support greater interoperability of data data. Further goals are defined in the “Objectives”.

Members of this working group include:
Apple
Cambridge Systematics
Capital Metro
Center for Urban Transportation Research at University of South Florida
Conveyal
Google
IBI Group
Mapzen
Microsoft
Moovel
Oregon Department of Transportation
Swiftly
Transit
Trillium
TriMet
World Bank

To join the working group, email gtfs-wg@rmi.org.

The GTFS Best Practices Working Group is convened and facilitated by Rocky Mountain Institute, a non-profit organization transforming global energy use.


[Logo file: http://www.nwp.com/energysummit16/images/RockyMountainInstitute.png]
