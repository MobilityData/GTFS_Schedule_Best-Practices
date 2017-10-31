---
---
### shapes.txt {#shapes}

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
    <tr id="shapes_1" class="anchor-row">
      <td rowspan="2"><code></code></td>
      <td>
        <span class="tag trip-planners"></span>
        <span class="tag accessibility"></span>
        <span class="tag arrival-predictions"></span>
      </td>
      <td>1</td>
      <td>Ideally, for alignments that are shared (i.e. in a case where Routes 1 and 2 operate on the same segment of roadway or track) then the shared portion of alignment should match exactly. This helps to facilitate high-quality transit cartography. <!-- (77) --></td>
    </tr>
    <tr id="shapes_2" class="anchor-row">
      <td></td>
      <td>2</td>
      <td>Alignments should follow the centerline of the right of way on which the vehicle travels. This could be either the centerline of the street if there are no designated lanes, or the centerline of the side of the roadway that travels in the direction the vehicle moves. <!-- (78) -->
      <br>
      Alignments should not “jag” to a curb stop, platform, or boarding location.</td>
    </tr>
    <tr id="shapes_3" class="anchor-row field-row">
      <td rowspan="2"><code>shape_dist_traveled</code></td>
      <td></td>
      <td>3</td>
      <td>Must be provided in both <code>shapes.txt</code> and <code>stop_times.txt</code> if an alignment includes looping or inlining (the vehicle crosses or travels over the same portion of alignment in one trip). <!-- (79) -->

        <figure id="inlining-fig">
          <img src="{{ "/best-practices/images/inlining.svg" | prepend: site.baseurl }}" alt="An Inlining Route">
          <figcaption>If a vehicle retraces or crosses the route alignment at points in the course of a trip, <code>shape_dist_traveled</code> is important to clarify how portions of the points in <code>shapes.txt</code> line up correspond with records in <code>stop_times.txt</code>.</figcaption>
        </figure>

      </td>
    </tr>
    <tr id="shapes_4" class="anchor-row">
      <td></td>
      <td>4</td>
      <td>The <code>shape_dist_traveled</code> field allows the agency to specify exactly how the stops in the <code>stop_times.txt</code> file fit into their respective shape. A common value to use for the <code>shape_dist_traveled</code> field is the distance from the beginning of the shape as traveled by the vehicle (think something like an odometer reading).

        <ul>
          <li>Route alignments (in <code>shapes.txt</code>) should be within 100 meters of stop locations which a trip serves.  <!-- (80) --></li>
          <li>Simplify alignments so that <code>shapes.txt</code> does not contain extraneous points (i.e. remove extra points on straight-line segments; see discussion of line simplification problem). <!-- (81) --></li>
        </ul>

      </td>
    </tr>
  </tbody>
</table>
