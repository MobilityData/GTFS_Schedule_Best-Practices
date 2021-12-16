### stop_times.txt

Loop routes: Loop routes require special `stop_times` considerations. (See: [Loop route case](/best-practices/#loop-routes))

| Field Name | Recommendation |
| --- | --- |
| pickup_type & drop_off_type | Non-revenue (deadhead) trips that do not provide passenger service should be marked with `pickup_type` and `drop_off_type` value of `1` for all `stop_times` rows.
| | On revenue trips, internal “timing points” for monitoring operational performance and other places such as garages that a passenger cannot board should be marked with `pickup_type = 1` (no pickup available) and `drop_off_type = 1` (no drop off available).  |
| arrival_time & departure_time | `arrival_time` and `departure_time` fields should specify time values whenever possible, including non-binding estimated or interpolated times between timepoints.  |
| stop_headsign | In general, headsign values should also correspond to signs in the stations.<br><br>In the cases below, “Southbound” would mislead customers because it is not used in the station signs.
| | <table class="example"><thead><tr><th colspan="2">In NYC, for the 2 going Southbound:</th></tr><tr><th>For <code>stop_times.txt</code> rows:</th><th>Use <code>stop_headsign</code> value:</th></tr></thead><tbody><tr><td>Until Manhattan is Reached</td><td><code>Manhattan & Brooklyn</code></td></tr><tr><td>Until Downtown is Reached</td><td><code>Downtown & Brooklyn</code></td></tr><tr><td>Until Brooklyn is Reached</td><td><code>Brooklyn</code></td></tr><tr><td>Once Brooklyn is Reached</td><td><code>Brooklyn (New Lots Av)</code></td></tr></tbody></table> |
| | <table class="example"><thead><tr><th colspan="2">In Boston, for the Red Line going Southbound, for the Braintree branch:</th></tr><tr><th>For <code>stop_times.txt</code> rows:</th><th>Use <code>stop_headsign</code> value:</th></tr></thead><tbody><tr><td>Until Downtown is Reached</td><td><code>Inbound to Braintree</code></td></tr><tr><td>Once Downtown is Reached</td><td><code>Braintree</code></td></tr><tr><td>After Downtown</td><td><code>Outbound to Braintree</code></td>  </tr></tbody></table> |
| shape_dist_traveled | `shape_dist_traveled` must be provided for routes that have looping or inlining (the vehicle crosses or travels over the same portion of alignment in one trip). See the [`shapes.shape_dist_traveled`](#shapestxt) recommendation. |
