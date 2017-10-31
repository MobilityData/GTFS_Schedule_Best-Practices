---
---
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
