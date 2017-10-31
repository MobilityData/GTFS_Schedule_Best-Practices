---
---
### stops.txt {#stops}

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
    <tr id="stops_1" class="anchor-row">
      <td rowspan="3"><code>stop_id</code></td>
      <td>
        <span class="tag trip-planners"></span>
        <span class="tag arrival-predictions"></span>
      </td>
      <td>1</td>
      <td>Stops that are in different physical locations (i.e., different designated precise locations for vehicles on designated routes to stop, potentially distinguished by signs, shelters, or other such public information, located on different street corners or representing different boarding facility such as a platform or bus bay, even if nearby each other) should have different <code>stop_id</code>. <!-- (27) --> </td>
    </tr>
    <tr id="stops_2" class="anchor-row">
      <td></td>
      <td>2</td>
      <td><code>stop_id</code> is an internal ID, not intended to be shown to passengers. <!-- (38) --></td>
    </tr>
    <tr id="stops_3" class="anchor-row">
      <td></td>
      <td>3</td>
      <td>Maintain consistent <code>stop_id</code> for the same stops across data iterations (see: <a href="#publishing">Dataset Publishing & General Practices</a>). <!-- (28) --></td>
    </tr>
    <tr id="stops_4" class="anchor-row field-row">
      <td rowspan="5"><code>stop_name</code></td>
      <td>
        <span class="tag trip-planners"></span>
        <span class="tag timetables"></span>
        <span class="tag human-readability"></span>
      </td>
      <td>4</td>
      <td>The <code>stop_name</code> should match the agency's public name for the stop, station, or boarding facility, e.g. what is printed on a timetable, published online, and/or presented at the location. <!-- (29) --></td>
    </tr>
    <tr id="stops_5" class="anchor-row">
      <td></td>
      <td>5</td>
      <td>When there is not a published stop name, follow consistent stop naming conventions throughout the feed. <!-- (30) --></td>
    </tr>
    <tr id="stops_6" class="anchor-row">
      <td></td>
      <td>6</td>
      <td>Avoid use of abbreviations other than for places that are most commonly called by an abbreviated name. See Abbreviations (#2) under <a href="#all-files">All Files</a>. <!-- (31) --></td>
    </tr>
    <tr id="stops_7" class="anchor-row">
      <td></td>
      <td>7</td>
      <td>Provide stop names in mixed case, following local conventions, as per recommendation for all customer-facing text fields. <!-- (32) --></td>
    </tr>
    <tr id="stops_8" class="anchor-row">
      <td></td>
      <td>8</td>
      <td>By default, <code>stop_name</code> should not contain generic or redundant words like “Station” or “Stop”, but some edge cases are allowed:
        <ul>
          <li>When it is actually part of the name (Union Station, Central Station)</li>
          <li>When the <code>stop_name</code> is too generic (such as if it is the name of the city). “Station”, “Terminal”, or other words make the meaning clear.</li>
        </ul>
      </td>
    </tr>
    <tr id="stops_9" class="anchor-row field-row">
      <td rowspan="3"><code>stop_lat</code> & <code>stop_lon</code></td>
      <td><span class="tag trip-planners"></span></td>
      <td>9</td>
      <td>Stop locations should be as accurate possible. Stop locations should have an error of <strong>no more</strong> than four meters when compared to the actual stop position.<!-- (34) --></td>
    </tr>
    <tr id="stops_10" class="anchor-row">
      <td></td>
      <td>10</td>
      <td>Stop locations should be placed very near to the pedestrian right of way where a passenger will board (i.e. correct side of the street).<!-- (35) --></td>
    </tr>
    <tr id="stops_11" class="anchor-row">
      <td></td>
      <td>11</td>
      <td>If a stop location is shared across separate data feeds (i.e. two agencies use exactly the same stop / boarding facility), indicate the stop is shared by using the exact same <code>stop_lat</code> and <code>stop_lon</code> for both stops.<!-- (36) --></td>
    </tr>
    <tr id="stops_12" class="anchor-row field-row">
      <td><code>stop_code</code></td>
      <td></td>
      <td>12</td>
      <td><code>stop_code</code> should be included in GTFS if there are passenger-facing stop numbers or short identifiers.<!-- (37) --></td>
    </tr>
    <tr id="stops_13" class="anchor-row field-row">
      <td rowspan="2"><code>parent_station</code> & <code>location_type</code></td>
      <td>
        <span class="tag trip-planners"></span>
        <span class="tag arrival-predictions"></span>
        <span class="tag timetables"></span>
      </td>
      <td>13</td>
      <td>
      Many stations or terminals have multiple boarding facilities (depending on mode, they might be called a bus bay, platform, wharf, gate, or another term). In such cases, feed producers should describe stations, boarding facilities (also called child stops), and their relation. <!-- (40) -->
        <ul>
          <li>The station or terminal should be defined as a record in <code>stops.txt</code> with <code>location_type = 1</code>.</li>
          <li>Each boarding facility should be defined as a stop with <code>location_type = 0</code>. The <code>parent_station</code> field should reference the <code>stop_id</code> of the station the boarding facility is in.</li>
        </ul>
      </td>
    </tr>
    <tr id="stops_14" class="anchor-row">
      <td></td>
      <td>14</td>
      <td>When naming the station and child stops, set names that are well-recognized by riders, and can help riders to identify the station and boarding facility (bus bay, platform, wharf, gate, etc.). <!-- (41) -->
        <table class="example">
          <thead>
            <tr>
              <th>Parent Station Name</th>
              <th>Child Stop Name</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><a href="{{ "/images/chicago-union" | prepend: site.baseurl }}">Chicago Union Station</a></td>
              <td>Chicago Union Station Platform 19</td>
            </tr>
            <tr>
              <td><a href="{{ "/images/sf-ferry" | prepend: site.baseurl }}">San Francisco Ferry Building Terminal</a></td>
              <td>San Francisco Ferry Building Terminal Gate E</td>
            </tr>
            <tr>
              <td><a href="{{ "/images/transit-center" | prepend: site.baseurl }}">Downtown Transit Center</a></td>
              <td>Downtown Transit Center Bay B</td>
            </tr>
          </tbody>
        </table>
      </td>
    </tr>
  </tbody>
</table>
