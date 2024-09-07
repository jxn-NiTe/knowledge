# The Five Thieves Of Time

* time is preacious, and not renewable
* need to protect against the five time thieves encountered in IT/tech workplaces

1. too much work-in-progress (WIP): work started, but not finished
2. unknown dependencies: something you weren't aware of initially, but required to finish
3. unplanned work: interruptions that prevent you from finishing work or stopping at a good breaking point
4. conflicting priorities: competing projects or tasks
5. neglected work: partially completed work that sits idle

## Too Much Work-In-Progress (WIP)

* definition of too much WIP = demand on team exceeds team's capacity
* humans have a hard time to say 'no', taking on more work than they have capacity, reasons include:
  * we are team players
  * fear of humilation or refusing a manager's request (being critized or fired)
  * we like new and shiny, rather than finishing a topic doing grunt work
  * misjudge size of request
  * we like to please people
* two flavours of customers:
  * external: outside your organization, buying/using your product/service, risk of losing revenue or getting bad review
  * internal: inside your organization, who consume your work
* most metrics in business or tech are trailing indicators
  * lead time = elapsed time from requested to completed
  * cycle time = elapsed time that a work item spends as WIP
  * throughput = number of completed things over period of time
* WIP is a leading indicator of cycle time -- the more items are worked on simultaneously, the more opportunities for dependencies and interruptions
* Little's law: avg cycle time = avg WIP : avg throughput
* consequences of too much WIP
  * context switching (wasting time, reducing time spent on high-quality knowledge work)
  * delayed delivery of value (with its own cost such as late feedback, or missed opportunity)
  * increased cost
  * decreased quality
  * conflictong priorities
  * irritable staff
* signs of too much WIP
  * context switching is common (leading to overhead and prevents flow or focused concentration)
  * customers wait for long periods of time
  * quality suffers (cannot give adequate attention to everything)
  * irritated staff (due to distractions, interruptions)
  * answering 'yes' to 'got five minutes?' too often (ending up working late)
* Kanban board as a method to combat WIP:
  * cards representing work
  * columns for backlog, in progress (sub-stages prep, implement, feedback)
  * imposing a WIP limit, making it a pull-based system
* must learn to say 'no' to additional work when schedules are full (which can be transparently reflected in a personal Kanban board)

## Unknown Dependencies

* three types of dependencies
  * architecture (both software and hardware), e.g. change in one are impacts another area
  * expertise, e.g. need aid from a person with specific knowledge to do something
  * activity, e.g. cannot progress until another acticty is completed
* typical examples
  * waiting on a test environment, database refresh or management decision to go forward
  * tightly coupled software architecture (remove table from DB impacts another team)
  * too few people with required specialized expert-skill set end up as bottleneck pulled in many directions
  * third parties and cloud downtime
* importance of dependencies: only one possible combination of inputs results in on-time delivery => every additional dependency halves the chance of delivering on time
* signs of unknown dependencies
  * coordination needs are high, project managers struggling to reach alignment
  * people not available when needed
  * change in one area of code or plan unexpectedly changes something else
* need to balance team size and dependencies across teams, i.e. from company-wide perspective, benefits of small, fast-moving teams diminishes when it leads to higher integration or coordination costs

## Unplanned Work

* unplanned and expedited work steals time away from work that's creating value
* DORA report shows that high performers spend 28% more time on planned work
* unplanned work increases risk, uncertainty, and reduces predictability
* Kanban helps making unplanned work visible (by having cards live on the board instead of a weekly status report where it might get obfuscated due to politcs)
* plan for unplanned work by reserving capacity (complete upfront preplanning is impossible anyway), since sometimes there is no choice (e.g. when a system became unavailalbe due to database crash)

## Conflicting Priorities

* invisible work and invisible priorities hamper alignment between engineers, project managers and business people
* conflicting priorities that compete for same people and resources block flow and increase partially completed work
* conflicting priorities lead to more WIP, and thus longer cycle times
* instead of tackling everything at once, tackle tasks by level of value and let people know what most important thing is

## Neglected Work

* common example of neglected work: deferred maintenance, bugs, technical debt and code without tests
* technical debt incurs interest payments, by increasing extra effort to fix bugs and develop new features, and can eventually blow up as an emergency
* beware the trade-off of short-term focus on shipping and costs vs accruing technical debt
* acknowledge zombie projects and consider the incremental investment needed to finish in comparison to its economic return (rather than falling for the sunk cost fallacy), and then either give them the required attention or kill them off
