---
---

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
