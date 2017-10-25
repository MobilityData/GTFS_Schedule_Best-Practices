---
layout: best-practices
---

# GTFS Data Best Practices

<h2 id="introduction">Introduction</h2>

These are recommended practices for describing public transportation services in the [General Transit Feed Specification (GTFS)](https://gtfs.org). These practices have been synthesized from the experience of the [GTFS Best Practices working group](#working-group) members and [application-specific GTFS practice recommendations](http://www.transitwiki.org/TransitWiki/index.php/Best_practices_for_creating_GTFS). For further background, see the [Frequently Asked Questions](faq).

### Linking to This Document

Please link here in order to provide feed producers with guidance for correct formation of GTFS data. Each individual recommendation has an anchor link. Click the recommendation to get the URL for the in-page anchor link.

If a GTFS-consuming application makes requirements or recommendations for GTFS data practices that are not described here, it is recommended to publish a document with those requirements or recommendations to supplement these common best practices.

### Document Structure

Recommended practices are organized into three primary sections

* __[Dataset Publishing & General Practices](#publishing):__ These practices relate to the overall structure of the GTFS dataset and to the manner in which GTFS datasets are published.
* __[Practice Recommendations Organized by File](#by-file):__ Recommendations are organized by file and field in the GTFS to facilitate mapping practices back to the official GTFS reference.
* __[Practice Recommendations Organized by Case](#by-case):__ With particular cases, such as loop routes, practices may need to be applied across several files and fields. Such recommendations are consolidated in this section.

### System Tags

Five different tags are included throughout the list of practices. These tags indicate the type of systems that require the practice being described.

<span class="tag trip-planners"></span>

These practices improve customer experience in applications like Google Maps that are used for trip planning.

<span class="tag human-readability"></span>

These practices help maintain the ability for a human reader to unzip and examine GTFS files.

<span class="tag arrival-predictions"></span>

These practices allow arrival prediction software to create real-time arrival estimates related to the schedules in [`trips.txt`](#trips) and [`stop_times.txt`](#stop-times).

<span class="tag timetables"></span>

These practices support the creation of HTML timetables based on GTFS, such as with the GTFS-to-HTML software.

<h1 id="practices">Practices</h1>

<h2 id="publishing">Dataset Publishing & General Practices</h2>

<table class="recommendation">
  <thead>
    <tr>
      <th>#</th>
      <th>Recommendation</th>
    </tr>
  </thead>
  <tbody>
    <tr id="publishing_1" class="anchor-row">
      <td>1</td>
      <td>Datasets should be published at a public, permanent URL, including the zip file name. (e.g., <a href="http://www.agency.org/gtfs/gtfs.zip">www.agency.org/gtfs/gtfs.zip</a>).  Ideally, the URL should be directly downloadable without requiring login to access the file, to facilitate download by consuming software applications.<!-- (1) --> While it is recommended (and the most common practice) to make a GTFS dataset openly downloadable, if a data provider does need to control access to GTFS for licensing or other reasons, it is recommended to control access to the GTFS dataset using API keys, which will facilitate automatic downloads. <!-- (2) --></td>
    </tr>
    <tr id="publishing_2" class="anchor-row">
      <td>2</td>
      <td>GTFS data is published in iterations so that a single file at a stable location always contains the latest official description of service for a transit agency (or agencies). <!-- (3) --></td>
    </tr>
    <tr id="publishing_3" class="anchor-row">
      <td>3</td>
      <td>Maintain persistent identifiers (id fields) for <code>stop_id</code>, <code>route_id</code>, and <code>agency_id</code> across data iterations whenever possible. <!-- (4) --></td>
    </tr>
    <tr id="publishing_4" class="anchor-row">
      <td>4</td>
      <td>One GTFS dataset should contain current and upcoming service (sometimes called a “merged” dataset). Google transitfeed tool's <a href="https://github.com/google/transitfeed/wiki/Merge">merge function</a> can be used to create a merged dataset from two different GTFS feeds. <!-- (5) -->

        <ul>
          <li>At any time, the published GTFS dataset should be valid for at least the next 7 days, and ideally for as long as the operator is confident that the schedule will continue to be operated.</li>
          <li>If possible, the GTFS dataset should cover at least the next 30 days of service.</li>
        </ul>

      </td>
    </tr>
    <tr id="publishing_5" class="anchor-row">
      <td>5</td>
      <td>Remove old services (expired calendars) from the feed. <!-- (10) --></td>
    </tr>
    <tr id="publishing_6" class="anchor-row">
      <td>6</td>
      <td>If a service modification will go into effect in 7 days or fewer, express this service change through a <a href="https://developers.google.com/transit/gtfs-realtime/">GTFS-realtime</a> feed (service advisories or trip updates) rather than static GTFS dataset. <!-- (8) --></td>
    </tr>
    <tr id="publishing_7" class="anchor-row">
      <td>7</td>
      <td>The web-server hosting GTFS data should be configured to correctly report the file modification date (see <a href="https://tools.ietf.org/html/rfc2616#section-14.29">HTTP/1.1 - Request for Comments 2616</a>, under Section 14.29). <!-- (9) --></td>
    </tr>
  </tbody>
</table>

<h2 id="by-file">Practice Recommendations Organized by File</h2>

This section shows practices organized by file and field, aligning with the [GTFS reference](https://github.com/google/transit/blob/master/gtfs/spec/en/reference.md).

<h3 id="all-files">All Files</h3>

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

{{ site.best-practices | where: "slug", "agency" }}
{{ site.best-practices | where: "slug", "feed_info" }}
{{ site.best-practices | where: "slug", "stops" }}
{{ site.best-practices | where: "slug", "stop_times" }}
{{ site.best-practices | where: "slug", "transfers" }}
{{ site.best-practices | where: "slug", "trips" }}
{{ site.best-practices | where: "slug", "frequencies" }}
{{ site.best-practices | where: "slug", "routes" }}
{{ site.best-practices | where: "slug", "shapes" }}
{{ site.best-practices | where: "slug", "calendar" }}
{{ site.best-practices | where: "slug", "calendar_dates" }}
{{ site.best-practices | where: "slug", "fare_rules" }}
{{ site.best-practices | where: "slug", "fare_attributes" }}

<h2 id="by-case">Practice Recommendations Organized by Case</h2>

This section covers particular cases with implications across files and fields.

<h3 id="loop-routes">Loop Routes</h3>

On loop routes, vehicles’ trips begin and end at the same location (sometimes a transit or transfer center). Vehicles usually operate continuously and allow passengers to stay onboard as the vehicle continues its loop.

<figure id="loop-route-fig">
  <figcaption>Below: Loop route. The vehicle returns to the starting point in one trip. Some loop routes offer travel in one direction, and others in two directions.</figcaption>
  <img src="{{ "/best-practices/images/loop-route.svg" | prepend: site.baseurl }}" alt="A Loop Route">
</figure>

<table class="recommendation">
  <thead>
    <tr>
      <th>Field Name</th>
      <th>Tags</th>
      <th>#</th>
      <th>Recommendation</th>
    </tr>
  </thead>
  <tbody>
    <tr id="loop_route_1" class="anchor-row">
      <td><code>trips.trip_id</code></td>
      <td></td>
      <td>1</td>
      <td>Model the complete round-trip for the loop with a single trip.  <!-- (102) --></td>
    </tr>
    <tr id="loop_route_2" class="anchor-row field-row">
      <td><code>stop_times.stop_id</code></td>
      <td></td>
      <td>2</td>
      <td>Include the first/last stop twice in <code>stop_times.txt</code> for the trip that is a loop. Example below. <!-- (87) -->

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

      </td>
    </tr>
    <tr id="loop_route_3" class="anchor-row field-row">
      <td><code>trips.direction_id</code></td>
      <td></td>
      <td>3</td>
      <td>If loop operates in opposite directions (i.e. clockwise and counterclockwise), then designate <code>direction_id</code> as <code>0</code> or <code>1</code>. <!-- (89) --></td>
    </tr>
    <tr id="loop_route_4" class="anchor-row field-row">
      <td><code>trips.block_id</code></td>
      <td></td>
      <td>4</td>
      <td>Indicate continuous loop trips with the same <code>block_id</code>. <!-- (90) --></td>
    </tr>
  </tbody>
</table>

<h3 id="lasso-routes">Lasso Routes</h3>

Lasso routes combine aspects of a loop route and directional route.

<figure id="lasso-route-fig">
  <figcaption>Below: Lasso routes are loop-routes from A to A via B with three sections:<br>
    <ul>
      <li>straight section from A to B;</li>
      <li>loop from and to B;</li>
      <li>straight section from B to A.</li>
    </ul>
  </figcaption>
  <img style="max-width: 30%" src="{{ "/best-practices/images/lasso-route.svg" | prepend: site.baseurl }}" alt="A Lasso Route">
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

<table class="recommendation">
  <thead>
    <tr>
      <th>Field Name</th>
      <th>Tags</th>
      <th>#</th>
      <th>Recommendation</th>
    </tr>
  </thead>
  <tbody>
    <tr id="lasso_route_1" class="anchor-row">
      <td><code>trips.trip_id</code></td>
      <td></td>
      <td>1</td>
      <td>The full extent of a “vehicle round-trip” (see illustration <a href="#lasso-route-fig">above</a>) consists of travel from A to B to B and back to A. An entire vehicle round-trip may be expressed by: <!-- (103) -->

        <ul>
          <li>A <strong>single</strong> <code>trip_id</code> value/record in <code>trips.txt</code></li>
          <li><strong>Multiple</strong> <code>trip_id</code> values/records in <code>trips.txt</code>, with continuous travel indicated by <code>block_id</code>.</li>
        </ul>

      </td>
    </tr>
    <tr id="lasso_route_2" class="anchor-row field-row">
      <td><code>stop_times.stop_headsign</code></td>
      <td></td>
      <td>2</td>
      <td>The stops along the A-B section will be passed through in both directions. <code>stop_headsign</code> facilitates distinguishing travel direction. Therefore, providing <code>stop_headsign</code> is recommended for these trips. <!-- (94) -->

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

      </td>
    </tr>
    <tr id="lasso_route_3" class="anchor-row field-row">
      <td><code>trip.trip_headsign</code></td>
      <td></td>
      <td>3</td>
      <td>
      The trip headsign should be a global description of the trip, like displayed in the schedules. Could be “Linden to Linden via Loop” (Chicago example), or “A to A via B” (generic example). <!-- (95) -->
      </td>
    </tr>
  </tbody>
</table>

<h3 id="branches">Branches</h3>

Some routes may include branches. Alignment and stops are shared amongst these branches, but each also serves distinct stops and alignment sections. The relationship among branches may be indicated by route name(s), headsigns, and trip short name using the further guidelines below.

<figure id="branching-fig">
<figcaption>Below: Three potential configurations of route branches. Primary alignment is in black. Branch is colored gold.</figcaption>
  <img src="{{ "/best-practices/images/branching.svg" | prepend: site.baseurl }}" alt="Configurations of Route Branches">
</figure>

<table class="recommendation">
  <thead>
    <tr>
      <th>Field Name</th>
      <th>Tags</th>
      <th>#</th>
      <th>Recommendation</th>
    </tr>
  </thead>
  <tbody>
    <tr id="branches_1" class="anchor-row">
      <td rowspan="3"><code></code></td>
      <td>
      </td>
      <td>1</td>
      <td>In naming branch routes, it is recommended to follow other passenger information materials. Below are descriptions and examples of two cases: <!-- (97) --></td>
    </tr>
    <tr id="branches_1A" class="anchor-row">
      <td></td>
      <td>1A</td>
      <td>If timetables and on-street signage represent two distinctly named routes (e.g. 1A and 1B), then present this as such in the GTFS, using the <code>route_short_name</code> and/or <code>route_long_name</code> fields. <!-- (97A) -->

      Example: <a href="{{ "/branch-example-godurham" | prepend: site.baseurl }}">GoDurham Transit routes 2, 2A, and 2B</a> demonstrate branched routes with deviations and extensions.

      </td>
    </tr>
    <tr id="branches_1B" class="anchor-row">
      <td></td>
      <td>1B</td>
      <td>If agency-provided information describes branches as the same named route, then utilize the <code>trips.trip_headsign</code>, <code>stop_times.stop_headsign</code>, and/or <code>trips.trip_short_name</code> fields. <!-- (97B) -->

      Example: GoTriangle <a href="http://admin.gotransitnc.org/sites/default/files/maps-and-schedules/gotriangle/RoutesAndSchedules-1561.pdf">route 300</a> travels to different locations depending on the time of day. During peak commuter hours extra legs are added onto the standard route to accommodate workers entering and leaving the city.

      </td>
    </tr>
  </tbody>
</table>

<h2 id="about">About This Document</h2>

<h3 id="objectives">Objectives</h3>

The objectives of maintaining GTFS Best Practices is to:

* Improve end-user customer experience in public transportation apps
* Make it easier for software developers to deploy and scale applications, products, and services
* Facilitate the use of GTFS in various application categories (beyond its original focus on trip planning)

<h3 id="amend">How to propose or amend published GTFS Best Practices</h3>

GTFS applications and practice evolve, and so this document may need to be amended from time to time. To propose an amendment to this document, open a pull request [in the GTFS Best Practices GitHub repository](https://github.com/rocky-mountain-institute/gtfs-best-practices) and advocate for the change. The GTFS Best Practices Working Group will meet quarterly to discuss and approve selected changes. Please send other questions or suggestions to [gtfs@rmi.org](mailto:gtfs@rmi.org).

<h2 id="working-group">GTFS Best Practices Working Group</h2>

The GTFS Best Practices Working Group consists of public transportation providers, developers of GTFS-consuming applications, consultants, and academic organizations to define common practices and expectations for GTFS data. The goals of this working group are to support greater interoperability of data data. To join the working group, email [gtfs@rmi.org](mailto:gtfs@rmi.org).

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

<figure>
  <a href="http://www.rmi.org/mobility"><img id="rmi-logo" src="/best-practices/images/rmi-small.png" alt="The Rocky Mountain Institute Mobility Transformation" width="240" height="63" border="0" style="height:63px;width:240px;"></a>
  <figcaption>The GTFS Best Practices Working Group is convened and facilitated by <a href="http://rmi.org/ITD">Rocky Mountain Institute</a> (RMI),an independent nonprofit founded in 1982. RMI is working to transform global energy use to create a clean, prosperous, and secure low-carbon future. It engages businesses, communities, institutions, and entrepreneurs to accelerate the adoption of market-based solutions that cost-effectively shift from fossil fuels to efficiency and renewables. RMI has offices in Basalt and Boulder, Colorado; New York City; Washington, D.C.; and Beijing.</figcaption>
</figure>
