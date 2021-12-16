### fare_rules.txt

| Field Name | Recommendation |
| --- | --- |
| All Fields | If a fare system cannot be accurately modeled, avoid further confusion and leave it blank. |
| | Include fares (`fare_attributes.txt` and `fare_rules.txt`) and model them as accurately as possible. In edge cases where fares cannot be accurately modeled, the fare should be represented as more expensive rather than less expensive so customers will not attempt to board with insufficient fare. If the vast majority of fares cannot be modeled correctly, do not include fare information in the feed. |
