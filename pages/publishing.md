---
---

<h1 id="practices">Practices</h1>

<h2 id="publishing">Dataset Publishing & General Practices</h2>

<table class="recommendation">
  <thead>
    <tr>
      <th>#</th>
      <th>Recommendation</th>
    </tr>
  </thead>
  <tbody>
    <tr id="publishing_1" class="anchor-row">
      <td>1</td>
      <td>Datasets should be published at a public, permanent URL, including the zip file name. (e.g., <a href="http://www.agency.org/gtfs/gtfs.zip">www.agency.org/gtfs/gtfs.zip</a>).  Ideally, the URL should be directly downloadable without requiring login to access the file, to facilitate download by consuming software applications.<!-- (1) --> While it is recommended (and the most common practice) to make a GTFS dataset openly downloadable, if a data provider does need to control access to GTFS for licensing or other reasons, it is recommended to control access to the GTFS dataset using API keys, which will facilitate automatic downloads. <!-- (2) --></td>
    </tr>
    <tr id="publishing_2" class="anchor-row">
      <td>2</td>
      <td>GTFS data is published in iterations so that a single file at a stable location always contains the latest official description of service for a transit agency (or agencies). <!-- (3) --></td>
    </tr>
    <tr id="publishing_3" class="anchor-row">
      <td>3</td>
      <td>Maintain persistent identifiers (id fields) for <code>stop_id</code>, <code>route_id</code>, and <code>agency_id</code> across data iterations whenever possible. <!-- (4) --></td>
    </tr>
    <tr id="publishing_4" class="anchor-row">
      <td>4</td>
      <td>One GTFS dataset should contain current and upcoming service (sometimes called a “merged” dataset). Google transitfeed tool's <a href="https://github.com/google/transitfeed/wiki/Merge">merge function</a> can be used to create a merged dataset from two different GTFS feeds. <!-- (5) -->

        <ul>
          <li>At any time, the published GTFS dataset should be valid for at least the next 7 days, and ideally for as long as the operator is confident that the schedule will continue to be operated.</li>
          <li>If possible, the GTFS dataset should cover at least the next 30 days of service.</li>
        </ul>

      </td>
    </tr>
    <tr id="publishing_5" class="anchor-row">
      <td>5</td>
      <td>Remove old services (expired calendars) from the feed. <!-- (10) --></td>
    </tr>
    <tr id="publishing_6" class="anchor-row">
      <td>6</td>
      <td>If a service modification will go into effect in 7 days or fewer, express this service change through a <a href="https://developers.google.com/transit/gtfs-realtime/">GTFS-realtime</a> feed (service advisories or trip updates) rather than static GTFS dataset. <!-- (8) --></td>
    </tr>
    <tr id="publishing_7" class="anchor-row">
      <td>7</td>
      <td>The web-server hosting GTFS data should be configured to correctly report the file modification date (see <a href="https://tools.ietf.org/html/rfc2616#section-14.29">HTTP/1.1 - Request for Comments 2616</a>, under Section 14.29). <!-- (9) --></td>
    </tr>
  </tbody>
</table>
