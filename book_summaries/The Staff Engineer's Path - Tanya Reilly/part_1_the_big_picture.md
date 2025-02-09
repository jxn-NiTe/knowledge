# The Big Picture

## Chapter 1: What Would You Say You Do Here?

big picture view on what staff engineers are and why organizations need them

career ladders

- idea of dual track, to distinguish between classical management path and technical leadership
  - classical: manager -> senior manager -> director
  - technical/IC: staff engineer -> senior staff engineer -> principal engineer
- allows engineers alternative to choose between senior engineer as terminal level or be forced to go the manager track for career progression

decisions and the big picture

- good decisions need context ("it depends", big picture)
  - trade-offs in technology choice, risk profile, available time or money, business goals, ...
  - individual teams optimize for their own interests (local maxima), ignoring consequences for broader organization (global maxima)
  - what is the technical strategic direction, which platforms to standardize on?
  - need engineers to create alignment between technical decisions and business needs (managers have a full time job with people and can't keep up on technology, CTO cannot be bottleneck)

leading big projects

- if project spans multiple teams, problems of local maxima, 0 or 2 teams taking ownership
- team boundaries have overlap or gaps that leak into architecture
- need alignment and key decisions beyond initial design documents
- need someone who
  - feels ownership overall (not for individual parts)
  - maintains engineering standards
  - has experience to anticipate risk
  - unblocks topics
  - mentors others

being role model

- solve business problems while achieving high level of quality, efficient use of resources and minimize level of chaos
- code and design reviews
- architecture best practices
- provide tooling that makes everyone safer and faster
- set engineering norms
- working at this level of influence means writing less code

being a leader

- when feeling 'someone should to something here', chances are the someone is you
- accomplishing larger things means working with larger groups of people, requiring a wider set of skills
- as your time becomes more expensive, the work you do is expected to have more impact
- take on increasingly bigger projects requiring collaboration, communication and alignment
- be a role model to other engineers
- teaching, raise everyone's game, setting technical direction, review code and design, protect others from common mistakes
- this _is_ leadership, but different from rating performance or approving vacation

a technical role

- high standards what excellent engineering looks like
- code and design reviews instructive for others
- understand trade-offs and help others understanding them too
- don't necessarily write a lot of code yourself, rather make ambiguous problem manageable so it becomes growth opportunity for others
- more relevant that technical problems get solved not how (could be codebase deep dives, writing documents, lots of one-on-one meetings, ...)

aim to be autonomous

- have your manager bring you context, but tell them what is important as much as the other way around
- create the backlog of high-impact work yourself
- defend and structure your time
  - learn to speak up (positive 'no'), rather than silently let a disaster unfold

set technical direction

- make sure technical decisions get made, they get made well, and they get documented

communicate often and well

- the better you are at being understood, the easier your job will be

reporting chains

- reporting 'high' (to a VP or director)
  - will give a broad perspective
  - will be asked to solve impactful problems
  - learning experience to watch them navigate topics
  - get less of your manager's time, which could lead to less visibility and less advocating for you or helping you
- reporting 'low' (to a manager)
  - if focusing on single technical area, can be beneficial to have a manager close to that area
  - information you get is prone to be filtered and centered on specific team
  - possibly you are more experienced than your manager, look to have skip-level meetings (if they are not common place: make clear it's about getting more context, not undermining)
  - local vs global maximum disagreements can cause tension

scope

- be aware of major decisions being made
- have opinions about changes and represent people who don't have the leverage to prevent poor technical decisions
- develop the next generation of senior and staff engineers
- if reporting to a director, have clarity if you work within one domain or operate at a higher level and tie more things together
- issues of too broad or undefined scope
  - lack of impact, too easy for everything to become your problem
  - becoming a bottleneck, when the convention is that your are needed for every decision
  - decision fatigue, when constantly deciding which thing to do
  - missing relationships, since it becomes difficult to have enough regular contact to build friendly relationships or to provide mentorship
- issues of too narrow scope (e.g. part of a single team reporting to a line manager)
  - lack of impact, when spending time on something that doesn't need staff engineer expertise, e.g. not at least a core component of a mission-critical team
  - opportunity cost
  - overshadowing other engineers, and taking learning opportunities away from them
  - overengineering, can easily happen when not busy

shape of your role

- depth-first vs breadth-first
  - preference, but more enjoyable if lined up with your scope
- four required disciplines
  - core technical skills - coding
  - product management - figuring out what needs to be done and why, maintaining a narrative about the work
  - project management - achieving the goal, removing chaos, tracking tasks, resolve blockers
  - people management - building a team, mentoring, dealing with their problems
- how much to code? it varies
  - many switch to reading and reviewing more than writing
  - others remain core contributors to projects
  - others take on noncritical projects that are interesting but don't delay the project
  - e.g. do not take on a broad architectural role when not coding makes you feel antsy
- delayed gratification
  - cross-organizational projects have different feedback loops than coding
- keeping a foot on the manager's track
  - some staff engineers have direct reports, like a tech lead manager / team lead
  - challenging to be responsible for both the humans and technical outcomes at the same time
  - some people go back and forth between a staff and management role
- staff archetypes (as described by Will Larson), neither exhaustive nor prescriptive
  - tech leads - partner with manager to guide the execution of one or more teams
  - architects - responsible for technical direction and quality across a critical area
  - solvers -wade into one difficult problem at a time
  - right hands - add leadership bandwidth to an organization

primary focus

- choosing what to do also means choosing what not to do
- need to work on what is important (opportunity cost)
- does not mean fancy technologies or VP-sponsored initiatives, often times it can be the work nobody sees
- can be gathering data that does not exist, or going through dusty documents that have not been touched in a decade
- know why the problem you are working on is strategically important, and if it's not, do something else
- take on projects that need you
  - if there are more wise voice of reason than people actually typing code, look for a different problem

aligning on scope, shape and primary focus

- does your picture match everyone's else?
- write out understanding of your job and share it with your manager, and thus resolve ambiguity
  - plan for work over next year, primary focus, other topics and how much relatively
  - specific goals
  - sample activities
  - what does success look like?
  - get it right enough, not perfect
- remember that your job is to make the organization successful

## Chapter 2: Three Maps

- analogously to real life maps, use different dedicated maps and not overlay everything into one (elevation, voting districts, streets)
- below maps already exist, maybe implicitly, and need to be uncovered
- maps will change over time as company priorities shift, and need to be uncovered again
- learn over time, what mails and meetings are important to inform your context
- note down relevant information

locator map

- perspective: what happens outside and at the boundary of your scope
- what is a team's purpose, who are its customers, how does the work affect other people
- dangers of being too absorbed in any domain
  - prioritizing badly (local vs global maxima)
  - losing empathy (when communicating, experts overestimate average person's familiarity with their topic)
  - tuning out the background noise (not recognizing gradual change that slides into a catastrophe)
  - forgetting what the work is for
- to combat this, try to take the view of an outsider
  - escape the echo chamber
    - seek out peers, build relationships so you can speak the truth to one another
    - get feedback, challenge pre-existing notions, remain objective
    - go beyond engineering (product, customer support, admin staff, ...)
  - what is actually important
    - technology only means to an end
    - don't pay off technical debt while you are lacking core features that would keep customers on board
  - what do customers care about
    - measure success from their pov (also applies to internal customers)
    - e.g. if a website is unreachable, it does not matter if SLOs on the DNS service are upheld
  - have your problems been solved before?
    - goal is solving problems, not necessarily writing code to do so
    - understand what already exists before building something new (conferences, newsletters, ...)

topographical map

- navigating paths inside the organization
- how are decisions made, how do leaders prefer to work, uncovering shadow organization charts
- friction and gaps between teams, open up paths of communication
- challenges when not knowing the terrain
  - your good ideas don't get traction (convince other people you are right, how to spread the idea)
  - don't find out about the difficult parts until you get there (what was tried before and failed, what is a better path?)
  - everything takes longer (your ideas in relation to organization's planning cycles)
- understand your organization
  - culture (degree of autonomy or inclusion, safe to make mistakes, ...)
    - secret vs open wrt information sharing
    - oral vs written (red tape process vs learning news randomly in the hallway, ideally somewhere in the middle)
    - top-down vs bottom-up (where to get support for initiatives)
    - fast vs deliberate
    - back channels vs front doors (approach someone over coffee or file a ticket)
    - allocated vs available
    - liquid vs crystallized (fixed hierarchy or meritocracy)
  - information flow, as classified by the Westrum organizational model
  
      | Pathological | Bureaucratic | Generative |
      | -- | -- | -- |
      | Power-oriented | Rule-oriented | Performance-oriented |
      | Low Cooperation |  Modes cooperation | High cooperation |
      | Messengers shot | Messengers neglected | Messengers trained |
      | Responsibilities shirked | Narrow responsibilities | Risks shared |
      | Bridging discouraged | Bridging tolerated | Bridging encouraged |
      | Failure -> scapegoating | Failure -> justice | Failure -> inquiry |
      | Novelty crushed | Novelty -> problems | Novelty implemented |

    - as evidenced by DORA, generative organizations have higher software delivery performance
    - possible actions to get there: cooperative cross-functional teams, blameless postmortems, break down silos, calculated risks, encourage experimentation
  - points of interest
    - chasms (teams' responsibilities rarely line up perfectly, e.g. gaps between product-focused and security )
    - fortresses (gatekeepers, might require sponsorship to pass through, filled out questionnaires, addressing budget estimates or risk mitigation plans)
    - disputed territory (power struggles and complicated decision making due to lack of alignment or overlapping responsibilities)
    - uncrossable deserts (project too big or politically messy, need lots of evidence if picking this fight)
    - paved roads, shortcuts, long ways around (official way to do things should be the most efficient, but isn't always in practice)
- points of interest on the map
  - need to understand how decisions are made to anticipate or influence them
  - where are decisions made and who takes part (weekly management meeting, director's staff meeting, slack channel of a central architecture group, ...)
  - when asking to be included, have a compelling story how this affects the organization positively, and then be prepared
  - shadow org chart: who is an influencer without being formally a decision maker (connectors or old-timers)
- keep map up to date by e.g.
  - announcement lists or channels
  - 'walk the floor', i.e. keep doing hands-on work to keep context and technical credibility
  - lurking, e.g. get information that isn't secret but not necessary like meetings notes, list of channels etc.
  - make time for reading (RFC, design documents, ...)
  - check in with your leadership for behind-the-scenes updates confirm alignment
  - talk with people to build context and build relationships (just ask a question and be interested ...)
- build bridges (bring people together, write email summaries or documents, ...)

treasure map

- where are we going? destinations and points to get there
- alignment on what and why
- problems that can arise when not looking beyond short-term goals
  - harder to keep everyone going in the same direction
  - not finishing big things (can also lead to others not seeing the value of your projects)
  - accumulating cruft (not knowing the bigger goal can lead to overcomplicated flexible solutions or becoming a weird edge case)
  - competing initiatives (everyone trying to do the right thing but inadvertently creating chaos)
  - engineers stop growing
- how knowing the long term goal helps
  - no need to keep tight alignment along the way, people can figure out their own route
  - explains the 'why' (e.g. technology x helps to reduce time to market)
  - knowing the goal helps to evaluate if proposed work will get us there
  - share with others, so they have a definition of success and know what they are aiming for
- if there is disagreement on the map
  - see if confusion or misalignment can be lifted
  - if this is not possible, create a new map

with these maps you can build a narrative and even small task become part of a story

## Chapter 3: Creating the Big Picture
