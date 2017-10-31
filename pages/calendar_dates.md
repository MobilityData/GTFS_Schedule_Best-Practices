---
---
### calendar_dates.txt {#calendar_dates}

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
    <tr id="calendar_dates_1" class="anchor-row">
      <td rowspan="2"><code></code></td>
      <td>
        <span class="tag human-readability"></span>
        <span class="tag timetables"></span>
      </td>
      <td>1</td>
      <td><code>calendar_dates.txt</code> should only contain a limited number of exceptions to the schedule. Regularly-scheduled service should be configured using <code>calendar.txt</code>.</td>
    </tr>
    <tr id="calendar_dates_2" class="anchor-row">
      <td></td>
      <td>2</td>
      <td>Including a <code>calendar.service_name</code> field can also increase the human readability of GTFS, although this is not adopted in the spec.</td>
    </tr>
  </tbody>
</table>
