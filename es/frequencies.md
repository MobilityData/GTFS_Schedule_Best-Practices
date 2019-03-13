### frequencies.txt
<div hidden>
###### trip-planners
###### arrival-predictions
###### timetables
###### human-readability
</div>

| Field Name | Recommendation |
| --- | --- |
| All Fields | Actual stop times are ignored for trips referenced by `frequencies.txt`; only travel time intervals between stops are significant for frequency-based trips. For clarity/human readability, it is recommended that the first stop time of a trip referenced in `frequencies.txt` should begin at 00:00:00 (first `arrival_time` value of 00:00:00). |
| block_id | Can be provided for frequency-based trips. |
