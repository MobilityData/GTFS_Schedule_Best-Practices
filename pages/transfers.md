---
---
<h3 id="transfers">transfers.txt</h3>

`transfers.transfer_type` can be one of four values [defined in the GTFS](https://developers.google.com/transit/gtfs/reference/transfers-file). These `transfer_type` definitions are quoted from the GTFS Specification below, _in italics_, with additional practice recommendations. <!-- (49) -->

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
    <tr id="transfers_1" class="anchor-row">
      <td rowspan="5"><code>transfers.transfer_type</code></td>
      <td>
        <span class="tag trip-planners"></span>
      </td>
      <td>1</td>
      <td>
        <q>0 or (empty): This is a recommended transfer point between routes.</q>
        <br>If there are multiple transfer opportunities that include a superior option (i.e. a transit center with additional amenities or a station with adjacent or connected boarding facilities/platforms), specify a recommended transfer point.<!-- (50) -->
      </td>
    </tr>
    <tr id="transfers_2" class="anchor-row">
      <td></td>
      <td>2</td>
      <td>
        <q>1: This is a timed transfer point between two routes. The departing vehicle is expected to wait for the arriving one, with sufficient time for a passenger to transfer between routes.</q>
        <br>This transfer type overrides a required interval to reliably make transfers.  As an example, Google Maps assumes that passengers need 3 minutes to safely make a transfer. Other applications may assume other defaults. <!-- (51) -->
      </td>
    </tr>
    <tr id="transfers_3" class="anchor-row">
      <td></td>
      <td>3</td>
      <td>
        <q>2: This transfer requires a minimum amount of time between arrival and departure to ensure a connection. The time required to transfer is specified by <code>min_transfer_time</code>.</q>
        Specify minimum transfer time if there are obstructions or other factors which increase the time to travel between stops. <!-- (52) -->
      </td>
    </tr>
    <tr id="transfers_4" class="anchor-row">
      <td></td>
      <td>4</td>
      <td>
        <q>3: Transfers are not possible between routes at this location.</q>
        Specify this value if transfers are not possible because of physical barriers, or if they are made unsafe or complicated by difficult road crossings or gaps in the pedestrian network. <!-- (53) -->
      </td>
    </tr>
    <tr id="transfers_5" class="anchor-row">
      <td></td>
      <td>5</td>
      <td>If in-seat (block) transfers are allowed between trips, then the last stop of the arriving trip must be the same as the first stop of the departing trip. <!-- (55) --></td>
    </tr>
  </tbody>
</table>
