# Leveling Up

## Chapter 7: You're a Role Model Now (Sorry)

meaning of doing a good job

- the work you do is implicitly the type and standard of work that others will see as correct and emulate
- be mature, constructive and accountable
- being a role model doesn't necessarily mean being loud or a public figure
- you can lead being quiet and thoughtful, influencing through good decisions and collaboration
- leadership is a skill to build
- the below are 4 aspirational qualities to have
  - but have the good sense to know when conventional wisdom is wrong

be competent

- know things
  - have technical knowledge, which underpins the big-picture thinking, project execution and influence
  - have sufficient experience working through technical problems yourself before you go on the staff or manager track
  - build domain knowledge
    - your general experience helps to recognize problem shapes in new domains and pattern-match
    - the broader the scope of your experience the faster you can learn new things
  - have a growth mindset and keep learning
- be self-aware
  - admit what you know, being competent doesn't mean you need to be the best
  - admit what you don't know, so you don't make bad decisions and lose an opportunity to learn
  - understand topics in your own context well enough to be able to explain them simply to non-experts
- have high standards
  - seek out constructive criticism (ask for code or design reviews, peer evaluations, let someone poke holes in your idea)
  - mistakes will inevitably happen, so own them
    - set out to fix them and communicate clearly and quickly
    - consider having a retrospective
  - be reliable
    - finish what you start and become trusted to get things under control and done well

be responsible

- take ownership
  - own the whole problem, navigate problems and be accountable for the result
  - use your own good judgement, don't constantly ask for permission, but signal what you are going to do ('radiate intent')
  - this creates an opportunity to intervene but does not transfer blame if things go wrong
  - when a decision is needed: weigh the options, choose decisively, explain your reasoning
  - ask 'obvious' questions to make the implicit explicit
  - do glue work (unblocking, onboarding, mentoring, scheduling, ...) yourself and redirect juniors towards more technical tasks
- take charge
  - step up in an emergency, explicitly coordinate and set expectations, rather than adding noise
  - ask for more information when everyone is confused (which junior people might not do, being afraid to admit they don't know something)
  - drive meetings: make sure there is an agenda, take and distribute notes (allows to frame the decision)
  - when someone said something offensive in a public channel, speak up
- create calm
  - defuse problems, don't amplify them
  - avoid blame, create an environment where its safe talking through an event and learn something
  - be consistent and predictable to create a sense of safety (this requires working in a sustainable way yourself)

remember the goal

- remember there's a business
  - software is in service of business goals
  - adapt to the situation, businesses change and so will your responsibilities (growth, new markets, holiday seasons, ,,,)
  - be aware of the budget and spend resources mindfully
- remember there's a user
  - know who uses your software and how, don't imagine a set of fictional, perfect users
  - make sure they can use the software and want to by writing things down (be clear about requirements, get proposed API reviewed, discuss a UI mockup, check in frequently)
- remember there's a team
  - don't become a single point of failure jumping on all the problems (not sustainable)
  - be aware of the team's capabilities and reach goals by empowering others

look ahead

- 'software engineering is programming integrated over time', don't optimize for now at the cost of future velocity or engineering ability
- anticipate what you'll wish you had done
  - telegraph what's coming, e.g. announce intention to deprecate a system, so new projects will know not to invest in it
  - tidy up: leave environments, codebase or documentation so that it just works, follow style guide, leave no traps like dangerous script
  - keep tools sharp: look for optimizations that will let you build, deploy and release more quickly
  - write things down to create institutional memory (decision records, system diagrams, code comments that explain context), include searchable keywords
- expect failure
  - can't predict everything: network, hardware, people, bugs, interactions
  - but predict that something will go wrong and build expectation of failure into your products
  - test error-paths and make product do something sensible and user-friendly
  - make sure you will find out when the system misbehaves
  - think about incident command system, chaos engineering and drills
- optimize for maintenance, not creation
  - software is created once and needs to be maintained for years (monitoring, scaling, regulatory requirements, updated protocols, ...)
  - make it understandable by documentation and diagrams, make your system observable (tracing, easy to analyze and debug)
  - keep it simple: after initial solution see if you can make it simpler (fewer LOC, fewer branches, fewer hours of maintenance, fewer ...)
  - when dealing with inherently complex problems, make deliberate decision where in the system to put the complexity (business logic, optimization), so it can be treated as a black box and everything else is easy to reason about
  - build things modular with clean interfaces, to keep with evolving architecture
- create future leaders
  - junior engineers are future senior engineers
  - give them space to learn, opportunities to do hands-on work and solve increasingly difficult problems

'the metric for success is whether other people want to work with you'

## Chapter 8: Good Influence at Scale

good influence

- better engineers -> better software -> better business outcomes
- when you work with someone who is missing skills or has lower standards, take your time to level them up
- ripple effect across the company and time
- shapes that influence can take

  | | Individual | Group | Catalyst |
  | -- | -- | -- | -- |
  | Advice | Mentoring, sharing knowledge, feedback | Tech talks, documentation, articles | mentorship program, tech talk events |
  | Teaching | Code review, design review, coaching/pairing/shadowing | Classes, codelabs | onboarding curriculum, teaching people to teach |
  | Guardrails | Code review, change review, design review | processes, linters, style guides | Frameworks, culture change |
  | Opportunity | Delegating, sponsorship, cheerleading, ongoing support | Sharing the spotlight, empowering your team | creating a culture of opportunity, see your junior colleagues change the world |

advice

- if unsolicited, needs to be helpful and non-obvious, can ask for permission or alternatively turn it into a blog post
- individual
  - mentorship: very individual (what works for someone else), figure out the actual need, set expectations (goals, meeting schedule)
  - answering questions: be accessible, find out what is implicitly solicited without infodumping, be clear if you share info or ask for a change (code reviews)
  - feedback: be honest in a kind way, don't hide the truth
  - peer reviews: aks yourself what a person could do to jump to the next senior level, be aware of formal context
- group
  - write things down, documentation means that you don't have to explain a topic again and again
  - if you want to reach outside the company, consider a blog post or article
  - look for opportunities to get a microphone and audience (all-hands meeting, conference)
- catalyst
  - set up advice flows that don't need you to be involved
  - have an easy-to-use documentation platform rather than relying on 1:1 conversation
  - set up monthly tech talk meetings or mentorship programs (beware of the administrative work)

teaching

- difference to advice: receive information vs internalizing information
- individual
  - unlocking a topic: have a specific goal, include hands-on learning
  - pairing: you execute, they shadow -> pairing -> they execute, you shadow
  - code/design review: suggest better alternatives and encourage behavior
    - understand the context (new to language vs 4-eyes check, initial draft vs before launch)
    - explain why (e.g. why prefer unique_ptr over shared_ptr)
    - give examples what would be better
    - be clear (e.g. is something just a nitpick or safety critical like SQL injection, what is blocking)
    - remain respectful, critique the code not the person
  - coaching:
    - teach people to solve problems themselves
    - open questions
    - active listening
    - leave enough space for coachee to reflect
- group
  - classes, high-upfront cost which amortizes over time, specific goals, exercises
  - codelabs, asynchronous, step-by-step tutorial, solving exercises
  - create learning paths (e.g. day 1 send two pull requests to add name to team list, add favorite joke, have back-and-forth in PR, day 2 build and run pre-made tiny client + server in prod including log, UI, metrics, make tiny change to logging)
- catalyst
  - teach others to teach classes
  - add class to onboarding curriculum (if applicable to every engineer)
  - evangelize learning paths
  - set up framework that makes it easy to create codelabs

guardrails

- stop someone to go over the edge and encourage autonomy, exploration and innovation
- individual
  - code, design, change review: neither rubber-stamp nor gate-keep, look for
    - should this work exist (technical solution instead of talking to someone)
    - does it actually solve the problem (can users use it, performance issues)
    - handling failure (edge cases, malformed input, load spikes)
    - is it understandable (can be maintained or debugged, naming)
    - does it fit into the bigger picture (patterns, risky change scheduled at unsuitable time)
    - do the right people know about it (names attached to action points?)
  - project guardrails: warn of pitfalls, be specific (promise review of design, or advocate for ideas with management)
- group
  - processes
    - standard steps
      - e.g. for prelaunch: security approval needed, giving notice, feature flags, monitoring, documentation
      - other examples: outage/incident response, agreeing on RFCs
    - trade-off standardization vs thinking, the bigger the company the higher the chance some structure is needed
    - needs to be lightweight (or will be sneaked around)
    - make the right way the easy way
  - written decisions
    - make a decision and write it down to not have repeated arguments and decision fatigue
    - style guides
    - paved roads (recommend set of standard, well-supported technologies)
    - policies (use sparingly, difficult to account for all edge cases)
    - technical vision and strategy
  - robots and reminders
    - automated reminders
    - linters (enforce style guide by machine, not reviewer)
    - templates (e.g. for RFC, include security section)
    - config checkers and pre-commit hooks
- catalyst
  - culture change, really difficult, so
    - solve a real problem (be able to answer why)
    - choose your battles
    - offer support (make it easy to do the right thing)
    - find allies (high level sponsors, influences, consider the shadow org chart)

opportunities

- people learn by doing, find them experiences they need to grow
- individual
  - delegation
    - really hand over, not micromanage
    - target the difficulty (bit of a stretch but manageable with support)
    - redirect questions, not proxy information
  - sponsorship
    - advocate for someone else: promote their work, recommend them for opportunities, bring them into a network, stand up for them
    - look for people that want opportunities to grow and that you trust
  - connecting people
- group
  - share the stage, let other people do the work if it is good enough
- catalyst
  - empower your colleagues to go to senior and staff level

## Chapter 9: What's Next?

your career

- what is important to you
  - introspect, common examples
    - being financially secure
    - supporting your family
    - having a flexible schedule
    - learning a lot
    - being visible
    - doing cool things
    - challenge yourself
    - building wealth
    - working for yourself
    - making a difference
    - enabling your vocation
    - and many more: traveling, health, friends, ...
- where are you going
  - relate above priorities to a 'trail map' with milestones along the way
  - find non-obvious path by not drawing entirely from your own experience, expand perspective (read, conferences, asking people)
- what do you need to invest in
  - building skills
    - what do you want or need to be good at?
    - is it worth the time investment?
    - fast-paced industry requires life-long learning and energy management
    - nobody knows everything -- no reason to suffer from imposter syndrome
  - building a network
    - be known
      - get opportunities that are not published but decided in back-channel conversation (job offers, conference spots, project lead)
    - know people
      - get insights (what does competent and professional look to people in other roles, communication patterns), learn from experts
    - networking is particular difficult for introverts, practical tips: <https://www.scienceofpeople.com/networking/>, <https://leaddev.com/career-development/engineering-leadership-little-help-my-friends>
  - building visibility
    - let people see you are solving problems, ask insightful questions, have a strategy in situations of chaos
    - optional, but helpful: external contributions (open source, working groups, podcasts, conference talks, ...)
  - choosing roles and projects deliberately
    - what will give you the experience you want to have (big vs small company, management vs hands-on, learning opportunities)

your current role

- metrics
  - measure if you grow towards your goals over time, detect trends or stagnation

  | Signals | are you learning? growing? | learning transferable skills vs coping with your org's dysfunction? | feel about recruiting friends to company? | confidence level? | is the job physically good for you? |
  | -- | -- | -- | -- | -- | -- |
  | Scale | 0=stagnant, 5=rocketship growth | 0=coping in this org, 5=learning transferable skills | 0=morally conflicted, 5=wildly enthusiastic | 0=being eroded, 5=growing | 0=stress, stress, stress, 5=feeling healthy |
  | \<date\> | | | | | |
  | ... | | | | | |

- can you get what you want from your role
  - evaluate what is good in your role vs what could be improved in relation to your goals
- should you change jobs
  - reasons to stay
    - feedback loops (see consequences of your actions)
    - depth
    - relationships
    - context (takes time to build, different in every place)
    - familiarity
  - reasons to move
    - employability (learn transferable skills, keep domain fresh)
    - experiences
    - growth (easier to get next level compared to promotions)
    - money
    - mismatch (not all roles are available in all places)

paths from here

- keep doing what you are doing (beware industry changes making your skills obsolete)
- work toward promotion (for the right reason: cash, prestige, challenges, scope, respect, influence, ...)
- work less (be deliberate which hours you drop and align expectations)
- change teams (fresh start without rebuilding context and relationships)
- build a new specialty
- explore (e.g. rotation program)
- take a management role (change of profession, not promotion, can swing back and forth)
- take on reports for the first time (and be ready to do less technical work)
- find or invent your own niche (find/define a role that fits your skills)
- do the same job for a different employer
- change employers and go up a level (e.g. bigger company or work you enjoy more)
- change employers and go down a level
- set up your own startup
- go independent (profits from network and public presence)
- change careers

be prepared to reset and start anew (maps, context, relationships)

take software seriously and help build a good software industry and impact lives positively
