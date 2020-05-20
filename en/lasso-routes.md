### Lasso Routes

Lasso routes combine aspects of a loop route and directional route.

<figure id="lasso-route-fig">
  <figcaption>Below: Lasso routes are loop-routes from A to A via B with three sections:<br>
    <ul>
      <li>straight section from A to B;</li>
      <li>loop from and to B;</li>
      <li>straight section from B to A.</li>
    </ul>
  </figcaption>
  <img src="lasso-route.svg" alt="A Lasso Route" width="30%"></img>
</figure>

| Examples: |
| -------- |
| Subway Routes ([Chicago](https://www.transitchicago.com/assets/1/6/ctamap_Lsystem.pdf)) |
| Bus Suburb to Downtown Routes ([St. Albert](https://stalbert.ca/uploads/PDF-infosheets/RideGuide-201-207_Revised_Oct_2017.pdf) or [Edmonton](http://webdocs.edmonton.ca/transit/route_schedules_and_maps/future/RT039.pdf)) |
| CTA Brown Line ([CTA Website](http://www.transitchicago.com/brownline/) and [TransitFeeds](https://transitfeeds.com/p/chicago-transit-authority/165/latest/route/Brn)) |

| Field Name | Recommendation |
| --- | --- |
| trips.trip_id | The full extent of a “vehicle round-trip” (see illustration [above](#lasso-route-fig)) consists of travel from A to B to B and back to A. An entire vehicle round-trip may be expressed by: <li>A __single__ `trip_id` value/record in `trips.txt`</li><li>__Multiple__ `trip_id` values/records in `trips.txt`, with continuous travel indicated by `block_id`.</li> |
| stop_times.stop_headsign | The stops along the A-B section will be passed through in both directions. `stop_headsign` facilitates distinguishing travel direction. Therefore, providing `stop_headsign` is recommended for these trips.example_table: <table class="example"><thead>  <tr><th>Examples:</th></tr></thead><tbody><tr><td>"A via B"</td></tr><tr><td>"A"</td></tr></tbody></table><table class="example"><thead><tr><th>Chicago Transit Authority's <a href="http://www.transitchicago.com/purpleline/">Purple Line</a></th></tr></thead><tbody><tr><td>"Southbound to Loop"</td></tr><tr><td>"Northbound via Loop"</td></tr><tr><td>"Northbound to Linden"</td></tr></tbody></table><table class="example"><thead><tr><th>Edmonton Transit Service Bus Lines, here <a href="http://webdocs.edmonton.ca/transit/route_schedules_and_maps/future/RT039.pdf">the 39</a></th></tr></thead><tbody><tr><td>"Rutherford"</td></tr><tr><td>"Century Park"</td></tr></tbody></table>
| trip.trip_headsign | The trip headsign should be a global description of the trip, like displayed in the schedules. Could be “Linden to Linden via Loop” (Chicago example), or “A to A via B” (generic example). |
