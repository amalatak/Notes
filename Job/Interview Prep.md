Experience
Lunar Mission Systems Engineer, All Lunar Programs, Blue Origin (Oct. 2023 - Present)

- Develop and maintain 400+ software-intensive mission system requirements in Jama, managing end-to-end traceability and ensuring compliance with human-spaceflight standards. 
- Plan and execute verification campaigns to demonstrate compliance with technical requirements, including for flight as well as for supporting major integration and vehicle test events. 
- Lead a small team responsible for requirements development and verification, managing priorities, dependencies, schedules, and deliverables.
- Collaborate with stakeholders, developers, and system architects to define interfaces and expected behavior across ground software, mission planning, mission design, and network systems. 
- Serve as a certified primary team lunar lander flight controller with vehicle command authority

Lead Simulations Systems Engineer, Ball Aerospace (June 2020 - Sept. 2023)

- Developed spacecraft physics and hardware emulation simulations in MATLAB and C++
- Designed and executed tests to integrate flight-software, GN&C, and engineering model hardware via Hardware-in-the-Loop and Software-in-the-Loop simulations. 
- Conducted root-cause analyses on hardware and simulation software to solve integration conflicts
- Authored requirements and architected code emphasizing reusability, and simplicity.
- Led cross-functional, cross-discipline prototyping efforts for early spacecraft development.

Additional Experience
Independent Verification and Validation Intern, Odyssey Space Research (June 2019 - August 2019)

- Developed Python test cases and post-processing tools to verify SpaceX ground software. 
- Investigated software and client-server communication issues and documented verification results

Lead GNC Engineer, Texas Rocket Engineering Lab (March 2019 - June 2020)

- Worked in a small team to develop GNC algorithms for liquid-fueled Karman-line-class rocket
- Chief architect of Trick-based C++ 6DOF simulation for FSW modeling and testing

Technical Skills
- Proficient with Jama, Python, C/C++, Linux, MATLAB/Simulink, NASA-Trick, Git/SVN
- Experience with SQL, REST APIs, HTML, CSS, JavaScript

Education
The University of Texas at Austin
Bachelor of Science, Aerospace Engineering 2020
Certificate, Computational Science and Engineering
GPA: 3.9
# Resume Discussion
I consider myself somewhere on the spectrum of software-aerospace-dynamics. Currently I am a mission systems engineer, I lead a team for requirements and verification development (delivered requirements and verification for MK2) for software-focused teams in the mission operations system. I write requirements, verification plans, I work with SMEs to close TBDs and define interfaces (Payload interfaces, NASA ICD), and I check our compliance with safety standards with the safety RE (write tests for and breakdown safety requirements and standards e.g. failover testing, availability, software lifecycle management). 

I'm also a flight controller for our pathfinder mission and just got a "promotion" to the next program controller. 

At my last job I was a simulation developer. I defined requirements and design for simulation models, wrote them, and then tested (not usually the same model, that was generally frowned upon) and verified. I did a lot of troubleshooting and worked in the lab to do root-cause for HIL testing issues. I assumed a role of leader there to own one of our hardware racks for a small program and aided in FSW and GNC development. 

Additionally I have a general GNC-focused background. 


Misc Large Projects
* Ball
	* Reaction wheel model
	* IMU model
	* HIL simulation procedures
	* Integration with FSW, GNC, and HIL end to end testing
	* Verifying models
* Blue
	* Deliver VEs
	* Delivery Requirements
	* Define systems
	* Conduct testing with limited background
	* Orchestrate and execute test campaigns

Comp question
* It depends a lot on the scope of work and risk of the company, but generally I would say for me to make a move it starts somewhere in the 175 range. 

Company information:
* On site in Golden
# Sample Questions

#### Why X or why a startup
It's a mix of a few things but really it comes down to wanting to learn and enjoying working in a small, dynamic space. I learned the most I ever did in that time span working as an intern at a small company in Houston. My experiences in the past also point to being happier in a smaller, dynamic space where I know the people. I mean I used to be down the hall from the CEO, and the IT guy was in the next room. 

For this role in particular I think there are a lot of really great, challenging problems to solve that could do a lot of good for the industry, prolonging vehicle life and cutting down on debris which is something I studied under one of the leading voices in the field, at least in part. 

#### Tell me about a time where you were a leader
* New R&V work, I own the requirements and verification definition, I coordinate with stakeholders and customers, deliver products, make timelines, and break down tasks into finite details that I can give to other engineers to take care of. Specifically with the GSW work. 

#### Difficult Engineer / Personal Conflict
* Belinda is hard to work with sometimes - communicate effectively and don't take anything personally
* Just recently had a weirdly combative meeting and in part it's on us as SEs to take it on the chin when no one else does
* I've never personally had a significant conflict that needed to go to HR

#### Technical Ownership
* Technically difficult problem
	* Current job space to ground ICD verification
	* Last job Building a RS-422 plant model
* Complex system I own
	* GSW Requirements and Verification for both programs
* Integration issue
	* 
* System I designed
	* I've designed plant systems at my last job
	* At this one I design systems of systems, which means how we write requirements and conduct and track verification, the process, capturing CONOPs, etc

#### Ambiguity
I live in ambiguity like I'm part of it or something. To expand on what I wrote in the application particularly for a role like this where I'm assuming (and correct me if I'm wrong), there aren't plans to do anything crazy certified yet- which I can also speak to. But based on that assumption, ambiguity is a space that I am comfortably uncomfortable with. I live it and I think I deal with it well, from developing code in it at my last job that interfaced with hardware and FSW to what I do now literally defining non-existent applications with SMEs that know way more than I do. 

Our requirements and verification are always ambiguous, at least for one program. They were written before must of us joined by someone who's no longer here. I verify those in an environment where we don't even have pumps to do the campaign I'm conducting verification for. Whereas on the other program, I work with NASA to resolve the ambiguity directly for human rated flight. 

#### Failure


#### Conflict



#### Why GNC and GNC experience

GNC has been an interest of mine for as long as I've been in this industry. I love the technical rigor, the measurable results, the scope of the problems. I specialized in it in undergrad. I could not imagine a more interesting scenario for a small company to work with, this is very high technical complexity for the size of the company. And I would love to do more than just write algorithms and code but to roll up my sleeves and get in a test bed and measure data and interpret it and make corrections and break things. 


## Technical Questions

#### How would you design a some kind of simulation
I would start with the requirements of the program or needs or some basis that defines fidelity and fundamentals as a start is this monte-carlo, or is this for basic development? For me, I'd also start with a basic testing framework as well, I believe in test-driven development. Not that the CI needs to come absolutely first but it would be high priority. Oh and one more thing is the interfaces- they don't necessarily need to be done early IMO but they absolutely can shape the simulation development especially depending on fidelity. Interfacing with a complicated actuator EM will take much more time than say giving FSW state estimates. 

For standing up something basic, I'd start with a MVP truth model then and add sensors and actuators (dynamics, attitude dynamics, mass prop, etc). I'd probably start with C/C++ or something like trick to keep it lightweight and in house but that depends on a few factors as opposed to something like matlab. 

Over time I would add fidelity, with guidance and controls, then add navigation. Ideally I'd structure the architecture so that each piece can be solved independently and unit testable. 

The whole time, not at the end, I would be testing and adding fidelity for testing as the system matured. 

#### How would you test the algorithms and simulations
I would unit test and CI the basic functionality. Do the core algorithms pass nominal and off nominal inputs and error injection at the function level and compared against truth models such as STK. Then I would focus on requirements verification to ensure the system does what's needed, and add validation testing on top including robustness testing and monte carlo simulation. Finally I would conduct integration tests with other systems and hardware. 

#### What would you put in a state vector
Position, velocity, attitude, dynamics, potentially state dependent filter values like bias, state dependent actuator values like RW rates, slosh, bending modes, etc. 

A state is a variable that carries information forward in time — something with its own differential equation and its own initial condition, whose current value you cannot reconstruct from the other states at the present instant.

The formal version: the state vector is the minimal set such that, given `x(t₀)` and the inputs from `t₀` onward, the entire future is determined. Nothing about the past matters beyond what's in `x`. If you can compute a quantity right now from the other states, it's an **output**

#### Controller stability

#### KF, LQR, Robust, MPC 

#### Questions

* * What kind of tooling are you guys using and do you prefer to develop in something like Matlab/SL or to write the code in C/C++?
	* C++/Trick ish
* What is the biggest hurdle or challenge you guys are facing right now?
* What would you say you spend most of your time doing right now? 
* Last time, it was mentioned that there are dedicated HIL environments, how much of that is owned by this team compared to other teams like dedicated sim or FSW team?
* Tell me about how you interact with other teams, what's the relationship? 
* How much of the code is written in house vs imported? 

Katalyst is a startup, build robotic spacecraft to enable dynamic space operations, revive and service and upgrade spacecraft. Maneuvering, relocation, refuel, upgrade. SWIFT mission going on right now. 

Mid 50s, looking at add 40

Currently 5 looking to take it to 10
All in the same office
Lean towards HIL testing
Flat sat with cameras, HW EMs, actual
Capture is the biggest issue, some missions won't be easy
Some kind of arm that can grab a target. Floater bots have flight like hardware to test capturing 
Pros/Cons
* Own GNC system, small team
* Time and resources are biggest need
* Future contracts are over a year so not super short
Team building - build up more is a want. Mostly have lunches and HH as a company
Next steps: take notes, go to team, debrief, next steps would be to go out and meet the team, see hardware. Take home project- pptx presentation of previous experience

Presentation proto-script

At the top:
* My name is Andrew, thank you for giving me the time to share a little about myself
* my educational background is in GNC-focused aerospace applications
* I'm currently a MSE at Blue Origin focusing on writing requirements and conducting verification of software-intensive systems
* My previous role was a simulations engineer at Ball developing models and conducting testing with integrated systems 
* I've kind of done a little bit of a lot of things, so today I'm going to walk you all through
	* a project I did early in my career that was GNC-focused
	* discuss how I'd apply that to a relative attitude simulation
	* how I'd use everything I've learned since then to apply to a GNC system and discuss what I would do differently today with the experience I’ve gained since.

Opening for TREL
* Focus on 
	* feasibility
	* early trades
	* standing up simulation and test environment
	* making sure we had a closed-loop, stable system throughout the flight profile
* Continued
	* Architected the design
	* Created post-processing analysis and visualization scripts
		* (note about trick with Nolan)

Architecture
* The focus was, again, on standing up a simple but modular and robust closed-loop but fully representative system that could be refined over time. 

Dynamics
* Prioritize high impact effects including
	* Atmospheric
		* Wind 
		* Air density
	* Aerodynamic
		* Fin actuation
		* Lift 
		* Drag
	* Engine effects and major perturbations
		* Thrust profile
		* Engine misalignment
* Ignored things for
	* Too little information to properly design a model for
	* Things that were too complex for the time
	* Didn't really ignore anything based on empirical results
		* Because at that time everything we modeled was higher fidelity
		* But we almost ignored wind models
		* But we did model stability over the flight profile, focusing on worst-case 

Trade Study
* Took at face value- costing for engine development so TVC was pretty much out
* I did a trade study regarding RCS and fin actuation
	* We determined that given the fin and body aerodynamics, over the flight profile we had sufficient torque to control the vehicle through powered ascent and likely much further after
	* It's also why we had such a large focus early on for fin models and any kind of rocket perturbation forces including thrust misalignment and wind

Sensor/Stability
* Used multiple IMUs 
	* Voting, averaging
	* Filter out structural noise
* GPS was limited by speed and altitude legally to low values (18km, 350m/s ish)
* We tracked cg/cp as a major metric of our stability and compared that, with the control authority study I mentioned before to determine vehicle stability, roughly throughout a set of known disturbance situations
	* Wind
	* Engine
	* Fin error

Outcome
* We built a successful closed loop rocket model used to inform decisions like actuation methods, payload deploy altitude and timing, dynamic forces on the vehicle, etc. 

Project overview
* Note requriements and constraints
* System definition - nod to what I do now

High level architecture
* Focus on the fact that it's similar to what I did before just with some updates

GNC Design choices
* A bulk of project ideas, I want to focus on what I chose, why, and how I might test it
* Use my experience with modeling and testing to prove that everything works by stability, simulation, monte-carlo, and HIL/flat-sat

Verification
* Space is hard and even through rigorous testing things can still go wrong which is why it's important to test as much as you can and as hi-fi as you can
* Especially since with this mission the goal is to be interfacing with other people's stuff
* Which is in large part where I can use a lot of my experience
* When selling to customers, being able to prove safety will be paramount

Ending and thank you
* The thread I'm getting at with this is that I'm trying to approach this from a complete system problem: I've defined systems, I understand the physics, can and have defined architecture and solutions for these types of problems, and built the kind of frameworks needed to prove and achieve confidence in those systems. 


Corrections
* Dotted box shouldn't include actuator models
* Didn't necessarily use PID, we also had PD
	* Also had phase-plane controller at disposal

Questions/Actions
* What is qSC
* How do you fuse sensors coming in at different frequencies
* Does everything live in the EKF? 
* Low pass and band stop filters
* How to generate attitude trajectory for a maneuver
* multiplicative errors for attitude vs additive 


Final meeting
* Background
	* CTO Gavin, been at the company a few years, worked in industry a lot at SpaceX
	* He worked in thermal fluids and energy systems.
* Potential Lunar Mission
	* Move a satellite from A to B
	* Address geo-servicing, going to the moon, potential to be installing site units on gov asset. Expect in the future for more markets to open up, Lunar infrastructure, potentially upgrade data centers, assemble stuff in space, in orbit assembly, want multi-planetary missions. 
	* GNC, robotics, RPOD, is the edge. 
* Why- want to work for a smaller company and move into more direct GNC role while leveraging my previous experience. I'm looking for a role that I can own significant technical rigor and end to end system development, learn and grow as an engineer, and meaningfully contribute to vehicle builds. 
* Questions
	* So I've talked to the GNC team on the technical side, I want to know what your vision and the leadership's vision is for the company over the next few years and beyond into the long run, and what you think the edge is for Katalyst
	* What do you see as the biggest bottlenecks
	* What are the biggest risks you're most focused on over the next 12-24 months?
	* What is your approach to retention and team building over time? What might my role look like in 2-3 years? 
	* What should I expect to do in the first 6-12 months
	* What's the biggest problem I could help solve right now?
* Funding
	* Could you walk me through how you think about the companies funding position today and the amount of runway that exists? Is that a concern in the next 24 months? How much is conrete, how much leway under the current hiring plan, and what constraints exist? I've never worked so prepared for a startup so I want to know what I'm signing up for, particularly if the swift mission has had any impact. 
* What would it take to get me here
	* I'm very interested in the role. Given the scope of the role and my experience I bring, and the fact that I'm leaving a very stable position, I'd feel comfortable about making the move for a base compensation around 200 plus appropriate equity. 
	* I'd also like to understand flexibility around signing bonuses or some reasonable downside protection if the role were eliminated, but that's something I'm happy to work through those details at a later time. 
* If they counter
	* Given all the reasons I've laid out, I'd really prefer to stick with the numbers I've stated. For the right other incentives I could be flexible, such as larger options grants, a higher signing bonus, or more material downside protections. 
* Just finished a venture round in June for $12m to go through the motions and bring on VCs, have kicked off series A, looking for $50-$75m, a lot of traction from the last mission, have $45m with potential revenue, series B level booking, term sheet with major GO customer. Only thing in writing is beaming mission, runway through Q1 if not at least Q2. Need to grow the team. 





### Do you have any experience with safety products like a FMECA or an FHA?
Kind of?  I'm currently writing documents (software verification and requirements plan for example) for mission ops that covers a lot of 7150.2D requirements, including things like safety-critical processes. In addition, I've written requirements and verification events for safety products that trace up to findings from the FHA/HEA/FMECA/etc, but I haven't written those safety products directly. 

### What is one way you think a star tracker might fail?
A star tracker functions by outputting an attitude, attitude estimate, or a picture (since they're just highly specialized cameras- I believe the shuttle used them as such for long range docking). 

I can imagine a star tracker could fail by regular hardware or software failures as well as by controllable scenarios such as looking at a keep out object (sun) or maybe overheating from radiators (or cooling too much by other failures), etc just to name a few. I figure manifestations of failure could show up as:
1. not outputting anything, switch to backup
2. outputting overly noisy data, compare against expected empirical dispersion and decide to accept/reject
3. outputting stale data, detect the lack of change and switch to backup
4. Outputting wrong data, compare against recent state estimates, other sensor readings (IMU, sun sensors like we talked about, etc)

### Do you have any experience with a GN&C phasing test?  What does a GN&C phasing test do?
I have to be honest, no I do not. I can guess (without looking it up), that a phasing test is a large-scale validation scenario of a larger GN&C "phase", so maybe something like steady-state cruise, docking, landing, etc. Bounded large scenarios that may involve integrated systems or just larger aspects of the GN&C suite. 

To give a bit of my test background (google wasn't actually super helpful for what a phasing test is, promise I only looked it up after writing the above), I've kind of run the whole gamut. I do a lot of interface/integration testing, leading those efforts on the MSE team e.g. space to ground ICD verification or working with NASA on designing interface tests between our MCCs. 

On the isolated dynamics testing side, I did a lot of that at my last job, testing out things like RWA, IMU models in a larger scenario writing unit tests, integration tests, and eventually integrating hardware in the lab. One of those big tests was something we called "the point test" (without getting too specific), which was essentially "do we maintain attitude with XYZ updates". 

### If you were to set up a Monte Carlo analysis, what would you need to know?

A monte carlo analysis generally tests some unit under test across a range of values of something, usually involving an amount of randomization (otherwise it's just a parameter sweep). 

Generally I need:
* My UUT or a model of the UUT (e.g. TVC control system)
* Real-world or models of the environment (e.g. earth gravity)
* The dispersion of whatever it is that I'm assessing the monte-carlo against (e.g. RCS performance errors)
* Success criteria e.g. is my system stable, do we get to such-and-such attitude, etc across the dispersion range or within some subsection of it. 


Call with Steph

- Title change

- What does it mean? What would I own, report to, expectations, growth?
- How much would I still be doing controls, autonomy, GNC, flight-vehicle engineering?

- Comp and package

- Base

- I think given my experience, scope of the role, and the risk I'm assuming I'm targeting a base around 200 in the range.

- Bonus
- Sign-on
- Equity - need it in an email with the actual strike price, valuation, vesting terms, and dilution numbers

- ISOs vs NSOs

- 401k and vesting
- Review and raise cycle

- Finances

- One of the things I'm weighing is leaving a fairly stable position for an early stage company, I'm very comfortable taking some risk for the right opportunity, but I'd like to understand that risk.
- What's the cash runway at the expected planned hiring rate, and how much is given assumed financing vs on-hand cash?
- I heard discussion earlier that I didn't completely understand, so I'm hoping to work through that
- Funding

- Contracts through the next 18 months for building Nexus, CEO out fundraising right now for series A for $50m. Funded for future work.

- Growth

- What's driving the growth right now?


GNC Systems Engineer

- Systems and GNC engineer

- Work through systems problems that someone needs to do for GNC
- Ensure that GN&C all integrate with each other

- Vehicle, subsystems
- Focus on analysis - simulation

- Q: Is this writing analysis problems or just writing high level stuff

- Higher level integrated analysis

- What architecture exists

- There is a systems RE currently
- Someone just left in May
- Another one as a different rec reporting to a different manager

- L2 rec is joe kidwell (Denver)

- (Vince Meyer)
- Might be a better fit
- Could potentially finagle a better fit
- Same program, helping person who's level 4 and difference is focus on simulation more and software-heavy

- Internal process

- First part - go to manager and say interest in particular rec
- Apply through workday
- Set up mock tech screen with Eva in a little bit of time
- Other thing to consider - go through all the steps, if there's a decision to offer, before you even know, current manager has to approve a transition date

# Denver space company

Vehicle engineer roll
* Proven ownership of managing budgets in terms of physical stuff like link budgets
* High bay execution - leading qualification campaigns
* Interface management - write and negotiate ICDs 

Small startup looking for teams of 1