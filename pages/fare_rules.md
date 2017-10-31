---
---
### fare_rules.txt {#fare_rules}

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
    <tr id="fare_rules_1" class="anchor-row">
      <td rowspan="3"><code></code></td>
      <td>
        <span class="tag trip-planners"></span>
        <span class="tag accessibility"></span>
      </td>
      <td>1</td>
      <td><code>agency_id</code> should be included in <code>fare_attributes.txt</code> if it the field is included in <code>agency.txt</code>. <!-- (84) --></td>
    </tr>
    <tr id="fare_rules_2" class="anchor-row">
      <td></td>
      <td>2</td>
      <td>If a fare system cannot be accurately modeled, avoid further confusion and leave it blank. <!-- (85) --></td>
    </tr>
    <tr id="fare_rules_3" class="anchor-row">
      <td></td>
      <td>3</td>
      <td>Include fares (<code>fare_attributes.txt</code> and <code>fare_rules.txt</code>) and model them as accurately as possible. In edge cases where fares cannot be accurately modeled, the fare should be represented as more expensive rather than less expensive so customers will not attempt to board with insufficient fare. If the vast majority of fares cannot be modeled correctly, do not include fare information in the feed. <!-- (86) --></td>
    </tr>
  </tbody>
</table>
