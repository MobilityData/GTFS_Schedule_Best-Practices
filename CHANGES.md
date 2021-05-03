### GTFS Schedule Best Practices Amendment Process
Anyone may propose a change to the GTFS Schedule Best Practices by following the process below.

1. Create a git branch with updates to all relevant parts of the documentation (except for translations).
1. Create a pull request on [MobilityData/GTFS_Schedule_Best-Practices](https://github.com/MobilityData/GTFS_Schedule_Best-Practices). Pull requests must contain an extended description of the patch following the template provided (Best Practice being proposed, use cases, data examples, and optional public-facing implementation). The creator of the pull request becomes the _advocate_.
1. The discussion of the proposal follows. Pull request comments should be used as the sole discussion forum.
  	- The discussion lasts for as long as the advocate feels necessary, but must be at least 7 calendar days.
  	- The advocate is responsible for timely update of the proposal (i.e. pull request) based on the comments for which they agree to.
  	- The advocate can claim the proposal abandoned at any time before calling for a vote, in which case the advocate should close the pull request.
1. The advocate can call for a vote on a version of the proposal at any point in time following the initial 7-day interval required for discussion.
1. Voting lasts the minimum period sufficient to cover 7 full calendar days (i.e., 168 hours), ending at 23:59:59 UTC.
  	- The advocate should announce the specific end time at the start of the vote.
  	- During the voting period, only editorial changes to the proposal are allowed (typos, wording may change as long as it does not change the meaning of the proposal).
  	- Anyone is allowed to vote yes (+1) or no (-1) in the form of comment on the pull request. Votes can be changed until the end of the voting period. If a voter changes their vote, it is recommended to do so by updating the original vote comment by striking through the original vote and writing the new vote.
  	- Votes before the start of the voting period are not considered.
1. The proposal is accepted if there are at least 3 votes with at least 80% in favor.
  	- The proposer's vote does not count towards the 3 vote total. For example, if Proposer X creates a pull request and votes yes, and User Y and Z vote yes, this is counted as 2 total yes votes.
  	- Votes against shall be motivated, and provide actionable and constructive feedback.
  	- If the vote has failed, then the advocate may choose to continue work on the proposal, or to abandon the proposal. Either decision of the advocate must be announced in pull request discussion.
  	- If the advocate continues the work on the proposal then a new vote can be called for at any point in time.
1. Any pull request remaining inactive for 30 calendar days will be automatically closed by a moderator. When a pull request is closed, the corresponding proposal is considered abandoned. The advocate may reopen the pull request at any time if they wish to continue or maintain the discussion.
1. If the proposal is accepted:
  	- MobilityData is committed to merging the voted upon version of the pull request, and performing the pull request within 5 business days.
