Controls are generally described in modern systems by a state space model. 

## States

States are characterized as something that contains the minimum information to determine the future state of a system at any given future time, given the initial conditions. 

## State Space Equation

The state space equation is a function of A, B, C, D matrices that relate the rate of the state to the current state of the system. Essentially it says that because we chose states that comply with teh above statement, that we *can* know the future of the state based on the current values and that happens through finding the rate of change of the state. 

$$
\dot{x}= Ax + Bu
$$
$$
y=Cx + Du
$$

$Ax$ captures the dynamics of the system and $Bu$ is how the system responds to inputs. 

## Pole Placement Control

Pole placement is a super basic method to implement controls for a state. The goal is to drive the state output from the plant to a given model and drive the feedback control error to zero. 

The state is fed back into the system and multiplied by a gain, K, to guarantee system stability. The reference signal AND the feedback values are both scaled. The latter for steady state stability and the former that steady state performance is acceptable.

The eigenvalues of A represent the poles of the system, and the location of the poles dictate the stability of the system. Move the poles to ensure system stability. 

When the controls (via feedback) become a function of $x$ they can get worked into the A matrix as manipulatable values and that allows us to move the poles. 

This is based on the fact that a system, A, assumed linear, can be characterized based on a set of first order differential equations that result in a solution of $e^{\lambda t}$. If we make the exponent negative it will converge to zero over time, even with oscillations.    