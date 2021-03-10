## Practice Recommendations Organized by Case

This section covers particular cases with implications across files and fields.

### Loop Routes

On loop routes, vehicles’ trips begin and end at the same location (sometimes a transit or transfer center). Vehicles usually operate continuously and allow passengers to stay onboard as the vehicle continues its loop.

<figure id="loop-route-fig">
  <figcaption>Below: Loop route. The vehicle returns to the starting point in one trip. Some loop routes offer travel in one direction, and others in two directions.</figcaption>
  <img src="loop-route.svg" alt="A Loop Route" width="20%"></img>
</figure>

Headsigns recommendations should therefore be applied in order to show riders the direction in which the vehicle is going.

To indicate the changing direction of travel, provide `stop_headsigns` in the `stop_times.txt` file. The `stop_headsign` describes the direction for trips departing from the stop for which it's defined. Adding `stop_headsigns` to each stop of a trip allows you to change the headsign information along a trip.

Don’t define one single circular trip in the stop_times.txt file for a route that operates between two endpoints (such as when the same bus goes back and forth). Instead, split the trip into two separate trip directions.
  
__Examples of circular trip modeling:__

- Circular trip with changing headsign for each stop

| Trip_id | arrival_time | departure_time | stop_id | stop_sequence | stop_headsign |
|---------|--------------|----------------|---------|---------------|---------------|
| trip_1  | 06:10:00     | 06:10:00       | stop_A  | 1             | "B"           |
| trip_1  | 06:15:00     | 06:15:00       | stop_B  | 2             | "C"           |
| trip_1  | 06:20:00     | 06:20:00       | stop_C  | 3             | "D"           |
| trip_1  | 06:25:00     | 06:25:00       | stop_D  | 4             | "E"           |
| trip_1  | 06:30:00     | 06:30:00       | stop_E  | 5             | "A"           |
| trip_1  | 06:35:00     | 06:35:00       | stop_A  | 6             | ""            |
 
- Circular trip with two headsigns

| Trip_id | arrival_time | departure_time | stop_id | stop_sequence | stop_headsign |
|---------|--------------|----------------|---------|---------------|---------------|
| trip_1  | 06:10:00     | 06:10:00       | stop_A  | 1             | "outbound"    |
| trip_1  | 06:15:00     | 06:15:00       | stop_B  | 2             | "outbound"    |
| trip_1  | 06:20:00     | 06:20:00       | stop_C  | 3             | "outbound"    |
| trip_1  | 06:25:00     | 06:25:00       | stop_D  | 4             | "inbound"     |
| trip_1  | 06:30:00     | 06:30:00       | stop_E  | 5             | "inbound"     |
| trip_1  | 06:35:00     | 06:35:00       | stop_F  | 6             | "inbound"     |
| trip_1  | 06:40:00     | 06:40:00       | stop_A  | 7             | ""            |

| Field Name | Recommendation |
| --- | --- |
| trips.trip_id | Model the complete round-trip for the loop with a single trip. |
| stop_times.stop_id | Include the first/last stop twice in `stop_times.txt` for the trip that is a loop. Example below. Often, a loop route may include first and last trips that do not travel the entire loop. Include these trips as well. <table class="example"><thead><tr><th><code>trip_id</code></th><th><code>stop_id</code></th><th><code>stop_sequence</code></th></tr></thead><tbody><tr><td>9000</td><td>101</td><td>1</td></tr><tr><td>9000</td><td>102</td><td>2</td></tr><tr><td>9000</td><td>103</td><td>3</td></tr><tr><td>9000</td><td>101</td><td>4</td></tr></tbody></table> |
| trips.direction_id | If loop operates in opposite directions (i.e. clockwise and counterclockwise), then designate `direction_id` as `0` or `1`. |
| trips.block_id | Indicate continuous loop trips with the same `block_id`. |

As a fallback, `trips.trip_headsign` can be defined as "Loop".