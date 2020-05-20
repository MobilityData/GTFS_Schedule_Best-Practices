
| Field Name | Recommendation |
| --- | --- |
| agency_id | Should be included, even if there is only one agency in the feed. (See also recommendation to include `agency_id` in [`routes.txt`](#routestxt) and [`fare_attributes.txt`](#fare_attributestxt)) |
| agency_lang | Should be included. |
| agency_phone | Should be included unless no such customer service phone exists. |
| agency_email | Should be included unless no such customer service email exists. |
| agency_fare_url | Should be included unless the agency is fully fare-free. |

__Examples:__

- Bus services are run by several small bus agencies. But there is one big agency that is responsible for scheduling and ticketing and from a user’s perspective responsible for the bus services.The one big agency should be defined as agency within the feed. Even if the data is split internally by different small bus operators there should only be one agency defined in the feed.
  
- The feed provider runs the ticketing portal, but there are different agencies that actually operate the services and are known by users to be responsible. The agencies actually operating the services should be defined as agencies within the feed.
