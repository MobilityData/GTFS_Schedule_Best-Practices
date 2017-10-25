---
---
<h3 id="trips">trips.txt</h3>

* __See special case for loop routes:__ Loop routes are cases where trips start and end at the same stop, as opposed to linear routes, which have two distinct termini. Loop routes must be described following specific practices. [See Loop route case below.](#loop-routes)
* __See special case for lasso routes:__ Lasso routes are a hybrid of linear and loop geometries, in which vehicles travel on a loop for only a portion of the route. Lasso routes must be described following specific practices. [See Lasso route case below.](#lasso-routes)

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
    <tr id="trips_1" class="anchor-row">
      <td rowspan="3"><code>trip_headsign</code></td>
      <td><span class="tag trip-planners"></span></td>
      <td>1</td>
      <td>Do not provide route names (matching <code>route_short_name</code> and <code>route_long_name</code>) in the <code>trip_headsign</code> or <code>stop_headsign</code> fields. <!-- (98) --></td>
    </tr>
    <tr id="trips_2" class="anchor-row">
      <td></td>
      <td>2</td>
      <td>Should contain destination, direction, and/or other trip designation text shown on the headsign of the vehicle which may be used to distinguish amongst trips in a route. Consistency with direction information shown on the vehicle is the primary and overriding goal for determining headsigns supplied in GTFS datasets. Other information should be included only if it does not compromise this primary goal. If headsigns change during a trip, override <code>trip_headsign</code> with <code>stop_times.stop_headsign</code>. Below are recommendations for some possible cases. <!-- (58) -->
        <table class="example">
          <thead>
            <tr>
              <th>Route Description</th>
              <th>Recommendation</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>2A. Destination-only</td>
              <td>Provide the terminus destination. e.g. "Transit Center", “Portland City Center”, or “Jantzen Beach” <!-- (58A) --> </td>
            </tr>
            <tr>
              <td>2B. Destinations with waypoints</td>
              <td>&lt;destination&gt; via &lt;waypoint&gt; “Highgate via Charing Cross”. If waypoint(s) are removed from the headsign show to passengers after the vehicle passes those waypoints, use <code>stop_times.stop_headsign</code> to set an updated headsign. <!-- (58B) --> </td>
            </tr>
            <tr>
              <td>2C. Regional placename with local stops</td>
              <td>If there will be multiple stops inside the city or borough of destination, use <code>stop_times.stop_headsign</code> once reaching the destination city. <!-- (58C) --> </td>
            </tr>
            <tr>
              <td>2D. Direction-only</td>
              <td>Indicate using terms such as “Northbound”, “Inbound”, “Clockwise,” or similar directions. <!-- (58D) --></td>
            </tr>
            <tr>
              <td>2E. Direction with destination</td>
              <td>&lt;direction&gt; to &lt;terminus name&gt; e.g. “Southbound to San Jose” <!-- (58E) --></td>
            </tr>
            <tr>
              <td>2F. Direction with destination and waypoints</td>
              <td>&lt;direction&gt; via &lt;waypoint&gt; to &lt;destination&gt; (“Northbound via Charing Cross to Highgate”). <!-- (58F) --></td>
            </tr>
          </tbody>
        </table>
      </td>
    </tr>
    <tr id="trips_3" class="anchor-row">
      <td></td>
      <td>3</td>
      <td>Do not begin a headsign with the words “To” or “Towards”.</td>
    </tr>
    <tr id="trips_4" class="anchor-row field-row">
      <td rowspan="2"><code>direction_id</code></td>
      <td>
        <span class="tag trip-planners"></span>
        <span class="tag timetables"></span>
        <span class="tag human-readability"></span>
      </td>
      <td>4</td>
      <td>If trips on a route service opposite directions, distinguish these groups of trips with the <code>direction_id</code> field, using values 0 and 1. <!-- (64) --></td>
    </tr>
    <tr id="trips_5" class="anchor-row">
      <td></td>
      <td>5</td>
      <td>Use values 0 and 1 consistently throughout the dataset. i.e. <!-- (65) -->
        <ul>
          <li>If 1 = Outbound on the Red route, then 1 = Outbound on the Green route</li>
          <li>If 1 = Northbound on Route X, then 1 = Northbound on Route Y</li>
          <li>If 1 = clockwise on Route X then 1 = clockwise on Route Y.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
