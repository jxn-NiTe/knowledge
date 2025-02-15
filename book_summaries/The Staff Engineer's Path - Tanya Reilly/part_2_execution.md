# Execution

## Finite Time

doing all the things

time

- opportunity cost, choosing something implicitly means choosing not do something else
- odd default that work calendar shows only meetings, i.e. the interruptions to focus work
- put specific non-meeting items in the calendar too (e.g. review proposal, write design doc etc.)
- this way you also know how much time for side-quests is available, when a new request can be answered, and things can be shuffled by priority
- leadership work can be unpredictable, so be aware how many hours you want to work in an average week and how many you are comfortable spiking to
- so have some buffer to react to unplanned obligations
- use the locator and treasure map to evaluate project's or activity's importance, then find a balance between choosing the most important work and what is right for you

resource constraints

- needs (not a comprehensive list but a useful model)
  - energy: understand what kinds of work are expensive for you and when it makes sense to start a task or not (e.g. debugging, 1:1 meetings, coding)
  - credibility: solve problems and show good technical judgement, avoid absolutism, be calm under stress, communicate clearly, balance between big picture and pragmatic local solution
  - quality of life: find balance of interesting work, enjoyable colleagues, money, optimizing for future happiness, having time outside work
  - skills: can become less relevant or outdated, so deliberately learn, work closely with skilled people, learn by doing
  - social capital: mix of trust, friendship feeling of owing someone, builds up over time (track record, repay for favours), invest it wisely
- when evaluation new projects, consider their effect on each resource, but don't overthink it for smaller tasks since perfect optimization is too difficult

choosing projects (using projects in a loose sense, any initiative or standalone task)

- where projects come from
  - you are invited to join: already momentum, but maybe not an growth opportunity (you are asked since you did something similar in the past)
  - you ask to join: be explicit about your intention
  - you have an idea: find a narrative to convince others
  - the fire alarm goes off: abrupt context switch, but clear goals and action oriented
  - claiming a problem (like a wonky API:) do as side quest since probably not highest priority, good to build up credibility and social capital
  - invited to join grassroots effort: can have huge impact or be huge waste of time, consider organizational buy-in, exit criteria, process for making decisions
  - someone needs to...: do fair share of work that belongs to no one
  - just meddling: can bring in good ideas but be wary to cause chaos and disengage before experiencing the consequences
- be clear with yourself about the shape of your tasks
  - projects can ramp up in approval phase
  - do meetings need prep time
  - can you hand off a process later on? define exit criteria
- questions to ask yourself
  - energy
    - how many things are you already doing
    - does this kind of work give or take energy
    - are you procrastinating (postpone big, complicated steps and fill the gap with low effort, low impact work)
    - is this fight worth it
  - quality of life
    - do you enjoy this work
    - how do you feel about the project's goals
  - credibility
    - does this project use your technical skills
    - does this project show your leadership skills
  - social capital
    - kind of work that company or manager expects at your level
    - will this work be respected
    - are you squandering the capital you have built (e.g. burn yourself on fixing a messy but low rate of change system)
  - skills
    - will this project teach you something you want to learn
    - will people around you raise your game
- what if it is the wrong project
  - do it anyway (is it short-term or has clear exit criteria?)
  - compensate for the project (have a side-quest that gives the lacking qualities of the main project, drop something to have more time and energy)
  - let others lead
  - resize the project (e.g. help in initial design phase)
  - don't do it
  - if you feel negatively about it, don't rationalize it away
- defend your time

## Leading Big Projects

- issues in projects usually not rooted in technology, but ambiguity (alignment, humans, legacy systems)
- needed qualities: perseverance, courage, willingness to talk to other people, handling complexity
- in the following, assume
  - big, difficult project for which you are the tech lead, thus responsible for the result
  - nobody is directly reporting to you
  - other leaders involved like project or product manager counterparts or engineering managers who have a team working on their own areas
- so we need to look at the whole problem, including parts that lie in the fissures between teams or that aren't really anyone's job

start of a project

- if you are feeling overwhelmed
  - big projects involve many people with opinions, deadlines, existing history, personality dynamics, documentation
  - takes time and energy to build mental maps
  - beware the imposter syndrome, difficulty (by ambiguity) is the nature of the work, so be brave enough to make and own mistakes
  - five things you can do to manage discomfort
    - create an anchor for yourself (have a place to write things down: reminders, to-dos, uncertainties, ...)
    - talk to your project sponsor (clarify what they want to achieve and how success looks like)
    - decide who gets your uncertainty (find a person you can be open and unsure with)
    - give yourself a win (take things step by step)
    - use your strengths (writing code vs read documents vs build relationships with people)
- building context
  - goals: understand the 'why'
  - customer needs: talk to them, understand what they want (not necessarily the same as what they tell you they want)
  - success metrics: needs to be agreed with sponsor and other leads, get real measurable goals in place (e.g. revenue, number of outages, not lines of code)
  - sponsors, stakeholders, customers: easier to sell the value of the work if you can find others who want it too
  - fixed constraints: deadlines, budget, dependencies on other teams or systems
  - risks: make frequent iterative changes to get feedback and course-correct, identify areas of uncertainty (unknowns, dependencies, key people)
  - history: what was tried before and failed?
  - team: build relationships with other leaders and have contacts in each team
- giving your project structure
  - defining roles, e.g.
    - table of leadership responsibilities (who is product manager, tech lead, ..., which tasks like coding, reporting belongs to which lead etc)
    - above table can be turned to a matrix with RACI (responsible, accountable, consulted, informed), can be overkill, but provides uncontroversial structure for decision-making
    - Venn diagram with what -> engineering manager, how -> engineering lead, why -> product manager, can be extended with when -> project manager
    - overarching goal is to have alignment and the required roles filled
  - recruiting people (need to work together, complement each other, push through friction, get the job done)
  - agreeing on scope
    - triangle of time, budget, scope, or fast, cheap, good -- pick two
    - each incremental change potentially changes the requirements for the next one
    - make increments small enough that there is always a milestone in sight
    - consider splitting things up in work streams and phases, keep track of dependencies and key junctures
  - estimating time
    - notoriously difficult ('... then multiply by 3')
    - break up tasks as far as possible
    - constantly update schedules, the more you do in a project the more experience you have how much something takes
    - talk to teams you depend on as early as possible and understand their availability
  - agreeing on logistics
    - meetings: which, when, where, how
    - informal communication
    - how to share status, e.g. who sends update mails at which cadence
    - where to find documentation
    - development practices (deployments, reviews, testing)
  - having a kickoff meeting (who is involved, goals, story so far, structures, what's next, where can people find out more)

driving the project (driving implies an active role: choosing the route, making decisions, react to what is encountered)

- exploring
  - what are the important aspects
    - have a clear story what to do
    - different teams will have different goals, expectations, constraints, mental models
    - get to the point where you can concisely explain what different teams in the project want in way that the'll agree is accurate
    - talk to users and stakeholders to refine framing the problem
  - possible approaches
    - don't go into the project with a solution already in mind, be open minded, consider existing solutions
    - learn from history: where have similar approaches succeeded or failed
    - thin beyond creating code (maintenance, operations, deployment, monitoring)
- clarifying
  - reduce complexity for others, how does the project connect to them, shared understanding
  - mental models
    - analogies and metaphors can make new topics approachable, make it possible to chain something new or abstract back to something already known
    - useful abstractions remove cognitive cost
  - naming
    - find a ubiquitous language (cf. DDD) shared by developers and real-world domain experts
  - pictures and graphs, e.g.
    - before and after to illustrate a change
    - nested objects, parallel objects, hierarchies/trees
    - be aware of existing associations (e.g. cylinder = data store), use legends to avoid interpretation
- designing
  - sharing designs
    - write things down, to get everyone on the same page, literally
    - extent should be proportionate to company culture and project size
  - RFC templates
    - no fixed standards, depends on needs and formality of company
    - but having a checklist helps avoiding common mistakes, and making the right decisions intentionally instead of implicitly
  - parts of an RFC
    - context
    - goals (without implementation details)
    - design -- can include: APIs, code snippets, diagrams, data models, process steps, ...
      - being wrong is better than vague (feedback, correction, learning)
      - be precise and clear, avoid ambiguity by applying usual technical writing tips (active verbs, replace 'this' and 'that' with nouns, etc)
    - security/privacy/compliance
    - alternatives considered
      - discuss tradeoffs
      - avoid having the same discussion multiple times if no new arguments are brought up
    - other topics may include: background, risks, dependencies, operations, ...
  - technical pitfalls
    - misidentifying a problem as new, when it isn't and solutions exist
    - thinking of something as easy, when you have not understood it in full yet
    - building for only the present, or for too far into the futures
    - figure out difficult parts early
    - be clear if a change requires a rewrite
    - keep things operable (observable, debuggable)
    - avoid bikeshedding
- coding
  - should you (as project lead) code on the project? it depends (team size, gain understanding, are there higher leverage topics, balance of writing and reviewing)
  - be an exemplar, but not a bottleneck
    - aim for solutions to empower your team, not to take over from them (pairing, settle for good enough in review comments)
- communicating
  - talking to each other
    - get to a level of comfortable familiarity, where it's normal to ask questions and admit what you don't know
    - find opportunities, e.g. shared meetings, channels, demos, social events
  - sharing status
    - make it easy for stakeholders, sponsors, customer teams to find out via e,g, conversations, email updates, dashboards
    - don't put all the details, but focus on overall message and impact, lead with the headlines
    - be clear about milestone dates
    - ask for help if you are stuck
- navigating
  - assume something will go wrong (technological fit, licensing, key person quits, ...)
  - reframe roadblocks as opportunity to learn
  - you are responsible for rerouting, escalating and breaking news
  - don't create panic, ask for help, don't struggle alone

## Why Have We Stopped?
