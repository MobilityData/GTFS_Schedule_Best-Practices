---
---
<h3 id="stop-times">stop_times.txt</h3>

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
    <tr id="stop_times_1" class="anchor-row field-row">
      <td rowspan="2"><code>pickup_type</code> & <code>drop_off_type</code></td>
      <td></td>
      <td>1</td>
      <td>Non-revenue (deadhead) trips that do not provide passenger service should be marked with <code>pickup_type</code> and <code>drop_off_type</code> value of <code>1</code> for all <code>stop_times</code> rows.<!-- (13) --></td>
    </tr>
    <tr id="stop_times_2" class="anchor-row">
      <td></td>
      <td>2</td>
      <td>On revenue trips, internal “timing points” for monitoring operational performance and other places such as garages that a passenger cannot board should be marked with <code>pickup_type = 1</code> (no pickup available) and <code>drop_off_type = 1</code> (no drop off available). <!-- (46) --></td>
    </tr>
    <tr id="stop_times_3" class="anchor-row field-row">
      <td><code>timepoint</code></td>
      <td></td>
      <td>3</td>
      <td>The <code>timepoint</code> field should be provided. It specifies which <code>stop_times</code> the operator will attempt to strictly adhere to (<code>timepoint=1</code>), and that other stop times are estimates (<code>timepoint=0</code>).<!-- (44) --></td>
    </tr>
    <tr id="stop_times_4" class="anchor-row field-row">
      <td><code>arrival_time</code> & <code>departure_time</code></td>
      <td>
        <span class="tag trip-planners"></span>
        <span class="tag arrival-predictions"></span>
      </td>
      <td>4</td>
      <td><code>arrival_time</code> and <code>departure_time</code> fields should specify time values whenever possible, including non-binding estimated or interpolated times between timepoints. <!-- (45) --></td>
    </tr>
    <tr id="stop_times_5" class="anchor-row field-row">
      <td><code>stop_headsign</code></td>
      <td>
        <span class="tag trip-planners"></span>
      </td>
      <td>5</td>
      <td><code>stop_headsign</code> values override the <code>trip_headsign</code> (in <code>trips.txt</code>). <code>stop_headsign</code> values should be provided when the text displayed on the headsign changes during a trip. <code>stop_headsign</code> values do not “carry down” to subsequent stops, and therefore values must be repeated if the stop headsign remains the same. In general, headsign values should also correspond to signs in the stations. <!-- (47) -->
      Examples:
        <table class="example">
          <thead>
            <tr>
              <th colspan="2">In NYC, for the 2 going Southbound:</th>
            </tr>
            <tr>
              <th>For <code>stop_times.txt</code> rows:</th>
              <th>Use <code>stop_headsign</code> value: </th>
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
      </td>
    </tr>
    <tr id="stop_times_6" class="anchor-row field-row">
      <td><code>shape_dist_traveled</code></td>
      <td></td>
      <td>6</td>
      <td><code>shape_dist_traveled</code> must be provided for routes that have looping or inlining (the vehicle crosses or travels over the same portion of alignment in one trip). See: <a href="#shape_dist_traveled"><code>shapes.shape_dist_traveled</code></a> recommendation.<!-- (48) --></td>
    </tr>
  </tbody>
</table>

Loop routes: Loop routes require special `stop_times` considerations. (See: [Loop route case](#loop-routes))
