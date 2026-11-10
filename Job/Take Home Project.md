Pick a project that I worked related to GNC and explain the problem, the approach I took, and the outcome. Then bridge the work to in-space spacecraft servicing GNC problem of my choosing. 

Then prepare a pptx to go through it. 20-30 minutes

Keep in mind
* Dynamics- what was kept, what was ignored, how I convinced myself the terms were negligible.
* Sensor and actuator sizing and selection- how their selection drove design and not the other way around. Explain how they interfaced with other components and subsystems
* Stability and performance margins, and how I verified the system
* Where the software met flight software - sample rates, discretization, faults, saturation, etc
* Trade-offs and anything I would do differently or on a different budget. 

Options
* Reaction wheel/sensor models
* College attitude control projects, Trick sim for TREL
* Verification and validation in current role

## Preface


## Rocket Sim 

I worked in a lab attempting to deploy a rocket launch for a competition. I lead the architecting, design, and early development of the project. I stood up a 6-dof simulation in Trick from the ground-up. 

### Dynamics

Early on, the dynamics model revolved around dominating physics affects and a minimum set of truth models to close the loop on a basic feedback control system to deliver a system capable of interfacing with other teams including FSW, CDH, etc. This was also to aid in early design of the system and trades for our team and other teams. 

I started with a set of basic physics models to stand up an initial 6-DOF closed-loop control system. This consisted of a basic thruster model, mass properties, and gravity. I layered additional models and affects over time including higher fidelity mass-property modeling, atmospheric affects, aerodynamic affects, and more in-depth control physics. 

Here seems like a good time to note that this was very early development, so everything we were building was designed to be flexible by parameterizing and monte-carlo wherever possible. 

Things I explicitly modeled
* Aerodynamic affects including lift and drag force and torque, fin torque, and wind affects. 
* Changing mass rate
* Changing cg, particularly relative to cp (initial guess, TBR once additional data was discovered in CFD/models from vehicle team)
* Propulsion uncertainty in alignment and angle
* Fin actuation force as a function of altitude, velocity, fin angle
	* Which was used to discuss broader vehicle design aspects such as attitude control at apogee, on descent, off the rail, and to inform preliminary worst-case design cases for vehicle teams

Fins became the primary actuating force and were continually refined in the models until I left the project. For example I put together a presentation to determine fin actuation force over the profile of the vehicle to verify we could control sufficiently. 

We chose our state to be position, velocity, attitude, attitude rate, and mass properties. 

We chose to ignore certain affects for several reasons. For example, 
* Coriolis affect was ignored because 
* Launch rail flexiblity
* Earth oblateness
* Local weather (our models used atmospheric values from a textbook)

We were in the process of adding bending modes and slosh when I left the project, and I believe that was the last of the major affects we were planning to model. 

Other decisions were more difficult such as 

### Sensors and Actuation

Sensors were chosen based on timescale, government regulations, force magnitudes, and industry consultations. Due to the nature of the project, GPS was prohibited for certain flight profiles so we relied on IMUs, and I worked with industry leaders nearby to discuss methods of sensing and sensor synthesis. 

Ultimately we settled on (at least) 3 IMUs as a redundancy and fault detection measure. We could smooth and average the signal, and use the third IMU to break a disagreement in the sensors, becoming 1-fault redundant at the sensor level. 

A simple, low-pass filter was chosen as the early estimation model to keep the estimation function lightweight but still remove volatile IMU noisy measurements. 

## Stability and Performance

Performance was measured in a few ways:
* Peak altitude
* Peak distance from the ground (the primary function)

And was verified mostly by Monte Carlo analysis, Software-in-the-Loop (SIL) simulation, industry consultation, and data processing analysis. I actually built tools specifically designed to post-process data so that we could analyze any state or simulation-propagated value. 

## Where Design Meets Reality

Unfortunately, we weren't able to get very far in this with my time in the project. However, I was able to do a lot of this in future roles so I hope I can compensate my lack of experience with this project by using experience from another project. 

That being said, we were able to add in a few things, namely discretization into the simulation models, and sample rates for the sensors being used in the filters. 

Had I continued in the project I would have absolutely added at a minimum
* Integration with flight software
* Integration with the flight operating system
* Sensor failure detection based on disagreement between the sensors, static, or stale values
* Sensor filtering based on three-sigma value-rejection
* Event logging to the flight recorder
* 

## Trade-Offs

With more time or budget. 

TESTING
* Generate a list of rough requirements to verify 
* Test each sensor
* Test each actuator
* Test the interfaces
* Test the control algorithms with real-world data
* Test it on a small-er-scale rocket

At the time, the thing I was singularly most concerned about was the atmospheric affects, and the vehicle performance and behavior in the real world. In no particular order
* Hot fire thrust force and alignment data
* CFD fin and vehicle atmospheric models across 
	* Mach regimes
	* angle of attack
	* fin deflection
* High-speed aerodynamics testing for empirical data for above but at a minimum for boundary layer separation as a boundary to the control laws
* CFD fluid slosh dynamics
* High fidelity bending mode models and resonant frequencies

With more money
* TVC control instead of fins and uncertainty about payload deployment attitude control. 
* A hardware-in-the-loop simulator



## Note about project state
The program did not reach flight during my tenure, so my ownership was concentrated on architecture, modeling, early closed-loop development, and design trades rather than hardware flight-test correlation. In subsequent roles, I've had much deeper exposure to integration and verification, and I'd apply those lessons here in the following ways
## Second Half

Bridge the work to an in-space service oriented GNC application of my choosing:
* Attitude control during RPOD



## Project and Role - Slide 1/2

I worked in a lab attempting to deploy a rocket launch for a competition. I started as a student and worked in it until I moved to Colorado to support simulation development at Ball. 

I lead the early development of the project. I stood up a 6-dof simulation in Trick, and it was very early in the project so I was concentrating on architecture, modeling, early closed-loop development, and design trades.

That was my focus rather than hardware flight-test correlation for this particular project, however I've had much deeper exposure to integration and verification in subsequent roles and I'll talk about how I'd apply those lessons learned at the end of this. 

## Architecture - Slide 3

(Sorry, had to lighten the slide to get the graphic to show up)

Architecture wise, it was a basic 6-dof simulation with closed loop control. There were a few things I had in mind as we were doing this
* In particular I wanted to distinguish the flight-code from the truth model so that we could plug directly into FSW as seamlessly as possible when that was ready
* Intense focus on aerodynamic and atmospheric modelling once the basics were stood up
* Modularity so that we could experiment with design choices as we went along

## Dynamics - Slide 4

In the dynamics we chose to prioritize low fidelity but functional models to get closed loop control working, and from there to focus efforts on expected high impact models such as aerodynamic models and their uncertainty since that was going to be the main method of control and the largest impact outside of the engine. 

In addition, I wanted to focus on disturbances early to build in as much robustness up front, such as engine misalignment, wind, fin aero design uncertainty, etc. This was all stuff that we knew had huge design maturity to push through, but that would ultimately affect the dynamics, and crucially it allowed us to tune variables and see how different things would affect our system. 

There were a few things we deliberately deferred, mainly due to expected magnitude of effect, complexity, available data, and program maturity. And really it became a choice of consciously defer to later such as engine transience because we simply had no idea what any of that data would look like for a long time.

One big uncertainty element we didn't model was transonic regime affects on fins and the vehicle. We knew very well that it could do weird things, but at the end of the day we pushed it off and instead modeled static margin over the flight profile, so that in the worst case scenario we knew the vehicle would remain stable in the worst case scenario we changed state to uncontrolled through that profile. 

One interesting thing we almost ignored was actually wind, gusts high in the atmosphere we calculated to be very small on the flight profile relative to the dynamic pressure. 

## Fin-control authority trade - Slide 5

One thing I want to highlight that we used our GNC models for was this particular trade study we were conducting on how we actually wanted to control the rocket on ascent, and it partly played into our static analysis with fins (or vise versa), particularly after MECO. 

Background: So MECO was actually fairly low and we coasted up in low atmospheric pressure so there was appetite to discuss if we need some sounding rocket logic to maintain attitude for a small payload deploy at apogee. Our maximum disturbance in that regime was expected to be wind forces and any disturbance from MECO. Ee took empirical wind data, did an analysis against cg to find a rough torque reference (and we could monte carlo with it) against our control authority to see if it really was feasible to use fins the whole flight and the answer was that generally yea we expected control authority to be sufficient to maintain attitude throughout the rest of the flight profile. 

## Sensing Regime and Stability - Slide 6

After settling on the actuation architecture, naturally we wanted to determine how observable and stable the vehicle was through the flight profile. 

Our primary measure of stability, as I've hinted at before, was to estimate the static margin for any given phase of the flight profile and that's what we parameter swept against most consistently. 

In addition, we demonstrated controller convergence by including initial condition offsets and simulation disturbances, which remained stable. 

I would have preferred to develop better performance analysis tools, but at this point we were focused on demonstrating feasibility 

Sensor modelling and filtering was something we took a different approach to, in that we 

- Servicing problem definition
- Servicing dynamics + architecture
- Sensors / actuators / estimator
- Monte Carlo / safety / abortability
- Rocket → servicing lessons / conclusion

