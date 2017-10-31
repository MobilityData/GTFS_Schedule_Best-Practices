---
---
### frequencies.txt {#frequencies}

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
    <tr id="frequencies_1" class="anchor-row">
      <td><code></code></td>
      <td>
        <span class="tag trip-planners"></span>
        <span class="tag timetables"></span>
        <span class="tag arrival-predictions"></span>
        <span class="tag human-readability"></span>
      </td>
      <td>1</td>
      <td>Actual stop times are ignored for trips referenced by <code>frequencies.txt</code>; only travel time intervals between stops are significant for frequency-based trips. For clarity/human readability, it is recommended that the first stop time of a trip referenced in <code>frequencies.txt</code> should begin at 00:00:00 (first <code>arrival_time</code> value of 00:00:00). <!-- (99) --></td>
    </tr>
    <tr id="frequencies_2" class="anchor-row field-row">
      <td><code>block_id</code></td>
      <td></td>
      <td>2</td>
      <td>Can be provided for frequency-based trips. <!-- (101) --></td>
    </tr>
  </tbody>
</table>
