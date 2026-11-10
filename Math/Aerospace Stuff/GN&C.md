# Attitude Dynamics

# The Transport Theorem

## What it says

The transport theorem (also called the **rotating frame derivative theorem** or Euler's derivative transformation) relates the time derivative of _any_ vector as observed from two frames that are rotating relative to each other:

$$\boxed{\left.\frac{d\mathbf{v}}{dt}\right|_{\mathcal{N}} = \left.\frac{d\mathbf{v}}{dt}\right|_{\mathcal{B}} + \boldsymbol{\omega}_{\mathcal{B}/\mathcal{N}} \times \mathbf{v}}$$

where $\mathcal{N}$ is typically an inertial frame, $\mathcal{B}$ a rotating (body) frame, and $\boldsymbol{\omega}_{\mathcal{B}/\mathcal{N}}$ is the angular velocity of $\mathcal{B}$ relative to $\mathcal{N}$.

## The conceptual core

A vector $\mathbf{v}$ is a frame-independent geometric object — but **its derivative is not**. Two observers in relatively rotating frames watching the same vector disagree about how fast it's changing, because one of them is spinning.

The notation $\frac{d}{dt}\big|_{\mathcal{B}}$ means: _differentiate the components of $\mathbf{v}$ while treating the $\mathcal{B}$ basis vectors as fixed._ The $\boldsymbol{\omega}\times\mathbf{v}$ term is exactly the correction for the fact that those basis vectors are _not_ actually fixed in $\mathcal{N}$.

## Derivation

Write $\mathbf{v}$ in the body basis ${\hat{\mathbf{b}}_1,\hat{\mathbf{b}}_2,\hat{\mathbf{b}}_3}$:

$$\mathbf{v} = v_1\hat{\mathbf{b}}_1 + v_2\hat{\mathbf{b}}_2 + v_3\hat{\mathbf{b}}_3$$

Differentiate as seen from $\mathcal{N}$, applying the product rule to both components _and_ basis vectors:

$$\left.\frac{d\mathbf{v}}{dt}\right|_{\mathcal{N}} = \underbrace{\sum_i \dot{v}_i,\hat{\mathbf{b}}_i}_{\text{= } \frac{d\mathbf{v}}{dt}\big|_{\mathcal{B}}} + \sum_i v_i \left.\frac{d\hat{\mathbf{b}}_i}{dt}\right|_{\mathcal{N}}$$

The first sum is precisely the body-frame derivative (components changing, basis held fixed). For the second, we need how a rotating frame's basis vectors move.

### Why $\dot{\hat{\mathbf{b}}}_i = \boldsymbol{\omega}\times\hat{\mathbf{b}}_i$

The basis vectors have constant unit length and constant mutual angles — the frame is rigid. Take the DCM $[BN]$ mapping $\mathcal{N}$ to $\mathcal{B}$ components. Orthonormality gives $[BN][BN]^\top = \mathbf{I}$. Differentiating:

$$\dot{[BN]}[BN]^\top + [BN]\dot{[BN]}^\top = 0 ;;\Longrightarrow;; \dot{[BN]}[BN]^\top = -\left(\dot{[BN]}[BN]^\top\right)^\top$$

So $\dot{[BN]}[BN]^\top$ is **skew-symmetric** ( $\mathbf{M}^\top = -\mathbf{M}$​ is the definition of skew-symmetric). Every $3\times3$ skew-symmetric matrix is a cross-product operator, and we _define_ the angular velocity as the vector generating it:

$$\dot{[BN]} = -[\boldsymbol{\omega}^\times][BN] \qquad \text{(Poisson's kinematic equation)}$$

Equivalently, in vector form: $\left.\frac{d\hat{\mathbf{b}}_i}{dt}\right|_{\mathcal{N}} = \boldsymbol{\omega}_{\mathcal{B}/\mathcal{N}} \times \hat{\mathbf{b}}_i$.

Substituting back:

$$\sum_i v_i\left(\boldsymbol{\omega}\times\hat{\mathbf{b}}_i\right) = \boldsymbol{\omega}\times\sum_i v_i\hat{\mathbf{b}}_i = \boldsymbol{\omega}\times\mathbf{v}$$

which completes the theorem. Note that angular velocity isn't assumed here — it _emerges_ as the skew-symmetric generator of rigid frame rotation.

## Application 1: Euler's rotational equations of motion

This is the theorem's most important use in attitude dynamics. Newton/Euler's law holds in an **inertial** frame:

$$\left.\frac{d\mathbf{H}}{dt}\right|_{\mathcal{N}} = \mathbf{L}$$

But the inertia tensor is only constant in the **body** frame — which is why we want to work there. Apply the transport theorem to $\mathbf{H}$:

$$\left.\frac{d\mathbf{H}}{dt}\right|_{\mathcal{B}} + \boldsymbol{\omega}\times\mathbf{H} = \mathbf{L}$$

With $\mathbf{H} = [I]\boldsymbol{\omega}$ and $[I]$ constant in $\mathcal{B}$ (rigid body, body frame at the center of mass):

$$\boxed{[I]\dot{\boldsymbol{\omega}} + \boldsymbol{\omega}\times[I]\boldsymbol{\omega} = \mathbf{L}}$$

**The transport theorem is the entire origin of the gyroscopic term** $\boldsymbol{\omega}\times[I]\boldsymbol{\omega}$. That single term is responsible for:

- Nonlinear coupling between axes (why attitude dynamics isn't a set of three decoupled double integrators)
- Precession and nutation
- Torque-free motion having nontrivial behavior at all
- Intermediate-axis instability

Useful special case: since $\boldsymbol{\omega}\times\boldsymbol{\omega} = 0$,

$$\left.\frac{d\boldsymbol{\omega}}{dt}\right|_{\mathcal{N}} = \left.\frac{d\boldsymbol{\omega}}{dt}\right|_{\mathcal{B}}$$

Angular acceleration is the one vector both frames agree on — which is why writing $\dot{\boldsymbol\omega}$ without a frame label is unambiguous.

## Application 2: Reaction wheels — closing the loop on your earlier question

For a spacecraft with wheels, total angular momentum is $\mathbf{H} = [I]\boldsymbol{\omega} + \mathbf{h}_w$. Applying the theorem:

$$[I]\dot{\boldsymbol{\omega}} + \dot{\mathbf{h}}_w + \boldsymbol{\omega}\times\left([I]\boldsymbol{\omega} + \mathbf{h}_w\right) = \mathbf{L}_{\text{ext}}$$

The $\boldsymbol{\omega}\times\mathbf{h}_w$ term is the gyroscopic stiffening from stored wheel momentum — it's why momentum-biased spacecraft resist off-axis disturbances, and why CMGs produce large output torque from small gimbal rates.

It also makes the desaturation logic precise: **only external torque $\mathbf{L}_{\text{ext}}$ can change total $\mathbf{H}$.** Wheels merely shuffle momentum internally ($\dot{\mathbf{h}}_w$ trades against $[I]\dot{\boldsymbol\omega}$). So dumping momentum _requires_ magnetorquers or thrusters — no internal actuator can do it. That's the structural reason the desaturation problem exists at all.

## Application 3: Translational kinematics in rotating frames

Apply the theorem twice to a position vector $\mathbf{r}$ (measured in the rotating frame):

$$\left.\frac{d^2\mathbf{r}}{dt^2}\right|_{\mathcal{N}} = \underbrace{\ddot{\mathbf{r}}\big|_{\mathcal{B}}}_{\text{relative}} + \underbrace{2,\boldsymbol{\omega}\times\dot{\mathbf{r}}\big|_{\mathcal{B}}}_{\text{Coriolis}} + \underbrace{\boldsymbol{\omega}\times(\boldsymbol{\omega}\times\mathbf{r})}_{\text{centrifugal}} + \underbrace{\dot{\boldsymbol{\omega}}\times\mathbf{r}}_{\text{Euler}}$$

Coriolis, centrifugal, and Euler terms aren't "forces" — they're artifacts of differentiating in a rotating frame, and they all fall out of the transport theorem mechanically.

## Summary

| Aspect              | Statement                                                                                           |
| ------------------- | --------------------------------------------------------------------------------------------------- |
| **Theorem**         | $\dot{\mathbf{v}}$                                                                                  |
| **Applies to**      | _Any_ vector — momentum, velocity, magnetic field, LOS vector, anything                             |
| **Physical origin** | Body basis vectors rotate: $\dot{\hat{\mathbf{b}}}_i = \boldsymbol{\omega}\times\hat{\mathbf{b}}_i$ |
| **Math origin**     | Orthonormality of DCM ⟹ $\dot{[BN]}[BN]^\top$ skew-symmetric                                        |
| **Why we need it**  | Physics laws are inertial; inertia tensor & sensors are body-fixed                                  |
| **Key consequence** | Gyroscopic term $\boldsymbol{\omega}\times\mathbf{H}$ in Euler's equations                          |
| **Sign convention** | Going _body → inertial_ adds $+\boldsymbol{\omega}\times$; reverse it going the other way           |

**One practical warning:** the most common error in using this is mixing frames within a single equation. The theorem is a statement about _vectors_, but the moment you write it in components, every term must be expressed in the same basis. Track which frame each component set lives in — most sign errors in attitude dynamics trace back to this.

---

Happy to go further into any of these: torque-free motion and the intermediate-axis theorem, the CMG gimbal torque amplification that falls out of Application 2, or how the transport theorem shows up in Hill/Clohessy-Wiltshire relative motion equations.

$\boldsymbol{\alpha} \mapsto [BN]$
# Estimation

## Kalman Filter

### Average Filter  

The Kalman filter is a recursive expression for the average. For example,

$$
\bar{x}_k = \frac{x_1 + x_2 + x_k}{k}
$$
Calculating a new one might be expensive if the equation is large and space vehicles might have limited computing power. To find the previous step,

$$
\bar{x}_{k-1}=\frac{x_1 + x_2 + x_{k-1}}{k-1}
$$
Multiplying by k we can get, from the whole equation
$$
k\bar{x}_{k-1}=x_1 + x_2 + x_{k-1} + x_k
$$

or 
$$
k\bar{x}_{k-1}= (k-1)\bar{x}_{k-1} + x_k
$$

And dividing by k-1 we get
$$
\frac{k}{k-1}\bar{x}_k = \bar{x}_{k-1} + \frac{x_k}{k-1}
$$

Such that 
$$
\bar{x}_k = \frac{k-1}{k}\bar{x}_{k-1} + \frac{1}{k}x_k
$$
Which is the basic Kalman filter. You use the previous state and spit out the new average without needing to recompute everything. Note: k here is the number of measurements, so this is really basic. 



Define alpha such that

$$\alpha === \frac{k-1}{k} = 1 - \frac{1}{k}$$ 
such that 
$$\frac{1}{k}=1-\alpha$$ 

And reworking the expression
$$
\bar{x}_k = \alpha\bar{x}_{k-1} + (1-\alpha)x_k
$$
Currently, alpha is constrained with averages to the number of data points. This is really helpful when data is noisy, for example measuring voltage. If a signal is changing, one can use a moving average over the last $n$ data points, but of course that comes with lag. 

$$
\bar{x}_k = \frac{x_{k-n+1} + x_{k-n+2} + ... + x_k}{n}
$$

Computes the average over the last n data points. Rewriting this

$$
\bar{x}_k = \bar{x}_{k-1} + \frac{x_{k} - x_{k-n}}{n}
$$
So we can pick n to be however many data points, which may be appropriate for applications like sonar on slow moving vessels. 

### First Order Low Pass Filter

This improves on the moving average to allow low frequencies (the actual signal), and filters out high frequencies (the noise), based on the assumption that the noise is high frequency. 

$$
\bar{x}_k = \frac{x_{k-n+1} + x_{k-n+2} + ... + x_k}{n}
$$
And it can be expanded in a way that makes the problem more apparent, each measurement has the same weighting of $\frac{1}{n}$. Measurements can be weighted such that more recent data is weighted more heavily. 

$$
\bar{x}_k = \alpha\bar{x}_{k-1} + (1-\alpha)x_k \space,\space  0<\alpha<1
$$

Which is the exact same thing as the average before, but here alpha can be anything. At this point, $\bar{x}_k$ is the estimate: take the noisy data and estimate the true value. But does it solve the problem with a moving average? Can solve for previous terms to find that yes the weightings decrease as the measurements get older. It also removes some of the lag as alpha is decreased. 

## Kalman Filter

A Kalman filter is basically a low pass filter where the alpha is changed for each step. A rough outline of the process looks like 

1. Set initial values of 
2. Predict state and error covariance
	1. Represented by $x^-_k$, where the minus represents the prediction
	2. Also predict the error covariance, $P^-_k$, a prediction of noise
	3. There's an $A$ and a $Q$ that show up only here, related to whatever process we're interested in. e.g. estimate velocity from position or vice versa.
3. Compute the Kalman gain
	1. Take in a bunch of matrices and find out the gain
	2. Kind of alpha
4. Compute the estimate from measurement data
	1. KF gives best estimate of the state given the data
5. Compute the error covariance

The error covariance sometimes takes some tuning from empirical data. Based on that data, the Kalman filter outputs a normal distribution about the estimate based on the uncertainty
$$
x_k \sim N(\hat{x}_k, P_k)
$$
Then given measurements, spit out an output and covariance (how the normal distribution changes over time). 
#### Typical Values
*Note: In all of this, k represents time at k* 

| Variable                 | Representation                 | Note                             |
| ------------------------ | ------------------------------ | -------------------------------- |
| External Input           | $z_k$ (measurement)            | From sensors                     |
| Final Output             | $\hat{x}_k$ (estimate)         |                                  |
| System Model             | $A, H, Q, R$                   | Specific to a physical situation |
| For internal computation | $\hat{x}^-_k, P^-_k, P_k, K_k$ |                                  |
$\mathbf{P} = \mathbb{E}[(\mathbf{x} - \hat{\mathbf{x}})(\mathbf{x} - \hat{\mathbf{x}})^\top]$ 

### Estimation Step

$$
\hat{x}_k=\hat{x}^-_k + K_k(z_k - H\hat{x}^-_k)
$$
Where 
$$
H\hat{x}^-_k
$$
is the predicted measurement and $z_k$ is the measurement. So what this is saying is our estimated state is the predicted state with some amount of correction applied. Rewriting we get
$$
\hat{x}_k=\hat{x}^-_k + K_kz_k - K_kH\hat{x}^-_k
$$
$$
=(I-K_kH)\hat{x}^-_k + K_kz_k 
$$

For now if we assume $n=1$ and $H=1$ then
$$
\hat{x}_k=(1-K_k)\hat{x}^-_k + K_kz_k 
$$
And if we substitute $\alpha$ for $1-K_k$ we get

$$
\hat{x}_k = \alpha\hat{x}^-_{k} + (1-\alpha)z_k
$$
Which shares a striking resemblance to the low pass filter, just with a dynamically changing gain/weighting. The KF also picks the gain so we don't have to tune it; it gets updated at each time, k, according to 
$$
K_k=P^-_kH^T(HP^-_kH^T+R)^{-1}
$$
Where $^T$ here indicates the transpose and $^-1$ the inverse. Then the error covariance gets updated for the next step.
$$
P_k=P^-_k - K_kHP^-_k
$$
The error covariance is a measure of the <u>inaccuracy</u> of the estimate. The understanding is that measurements contain noise, and they're assumed to be gaussian noise (normally distributed) and that the true state at that timestep is given by 
$$
x_k \sim N(\hat{x}_k, P_k)
$$
Or a normal distribution with a mean of $\hat{x}_k$ with a covariance $P_k$ as the spread of the bell curve. If $P_k$ is "large", the error is large, and if it's small, error is small; indicating size of distribution about the mean. 

Note here a few matrices involved. $H$ comes from the system model and $R$ does as well, and the Kalman Gain, $K$. 

### Prediction Step

Assuming we have $\hat{x}_k$ at time $t_k$ we want to predict $\hat{x}_{k+1}$ at time $t_{k+1}$. Here, we find the *a priori* estimate, or the estimate before we take a measurement. Once we've taken a measurement it becomes the *a posteriori* estimate. 
$$
\hat{x}^-_{k+1}=A\hat{x}_k
$$
where $A$ is some $n$x$n$ matrix. The predicted covariance is
$$
P^-_{k+1}=APA^T + Q
$$
Note that $Q$ is process noise or state transition noise. 
Second note that $A$ and $Q$ only show up in the prediction step. 

### Putting it all together

$$
\hat{x}_k = \hat{x}^-_k + K_k(z_k-H\hat{x}^-_k)
$$
where 
$$
\hat{x}^-_k=A\hat{x}_{k-1}
$$
Substituting the two together we get 
$$
\hat{x}_k = A\hat{x}_{k-1} + K_k(z_k-HA\hat{x}_{k-1})
$$
Our unknowns remaining not specified are variables we call the system model, or the problem expressed with math, in particular those matrices $A$, $H$, $Q$, $R$. The Kalman filter deals with a linear state model, that's this
$$
x_{k+1}=Ax_k + w_k
$$
Where $w_k$ is the process noise or the uncertainty of the world; it's the unknown unknowns. It's a linear combination of the state and process noise. The measurement shows up as 
$$
z_{k+1}=Hx_k+v_k
$$
Where this is linear plus the measurement noise. Dimensionally, they are the following
* $x_k$ is the state vector ($n$ x 1 column vector)
* $z_k$ is the measurement vector ($m$ x 1 column vector). Note it doesn't need to be the same dimensions as x
* $A$ is the state transition matrix or the linear process matrix ($n$ x $n$ square matrix)
* $H$ is the state to measurement matrix ($m$ x $n$)
* $w_k$ is the state transition noise ($n$ x 1 column vector - same as state vector)
* $v_k$ is the measurement noise, usually provided by manufacturer ($m$ x 1 column vector)
* $Q$ is the covariance matrix of $w_k$ ($n$ x $n$ diagonal matrix)
* $R$ is the covariance matrix of $v_k$ ($m$ x $m$ diagonal matrix)

If $n$ > 1, we can write $w_k$ as
$$ 
w_k = \begin{bmatrix} w_k^1 \\ w_k^2 \\ ... \\ w_k^n \end{bmatrix}
$$
where $n$ is the number of state transition noise entries. The entries are expressed in $\sigma^2$ variances where $\sigma$ is the standard deviation. With this understanding we would write $Q$ as 
$$
Q = \begin{bmatrix} \sigma_1^2 & 0 & ... & 0 \\ 0 & \sigma_2^2 \\ ... \\ 0 & ... & 0 & \sigma_n^2 \end{bmatrix}
$$
And the same thing applies for $R$ for sensor $\sigma$ values. Typically these values are found by trial and error, and by calibration; in other words empirically. Trust vendor specs at your own risk. The sensor error metrics may be different for each sensor and may change over time. For example if sensors errors are bounded as a percent of the measurement value. 

##### Simple Example - Voltage from a Battery

* $z$ measurement is voltage and has noise
* $x$ state is also voltage (assume no noise)

This means $m$ = $n$ = 1. Our model would look like 
$$
\begin{gathered}
x_{k+1} = Ax_k \\
z_k = Hx_k + v_k
\end{gathered}
$$
Translating into matrices, $A=1$, $H=1$. Assume Process noise, $Q$ is zero, and assume measurement noise, $\sigma=2$ so $R=4$. Seeding the system with an initial guess of something arbitrary such as 14v we start with $x_0^- = 14$ and $P_0^- = 6$. 

##### Example - Estimating Velocity from Position

Assume still one dimensional, but $n$ is 2 now. We can model the system as 
$$
x_k = \begin{bmatrix} position \\ velocity \end{bmatrix}_k
$$
$$
\begin{gathered}
x_{k+1} = Ax_k + w_k \\
z_k = Hx_k + v_k
\end{gathered}
$$
$A$ will be a 2x2 matrix. 
$$
A = \begin{bmatrix} 1 & \Delta t \\ 0 & 1 \end{bmatrix}
$$
and $H$ is
$$
H=\begin{bmatrix} 1 & 0 \end{bmatrix}
$$
So
$$
x_{k+1} = \begin{bmatrix} position \\ velocity \end{bmatrix}_{k+1} =\begin{bmatrix} 1 & \Delta t \\ 0 & 1 \end{bmatrix} \begin{bmatrix} position \\ velocity \end{bmatrix}_{k}
$$
$$
=\begin{bmatrix} position_k & \Delta t*velocity_k \\ 0 & velocity_k \end{bmatrix}
$$
For something basic $\Delta t$ might be small, like 0.02. Measurements look like
$$
z_k = Hx_k + v_k = \begin{bmatrix} 1 & 0 \end{bmatrix} \begin{bmatrix} position \\ velocity \end{bmatrix}_k + v_k
$$
Assume Q is something like 
$$
Q =\begin{bmatrix} 1 & 0 \\ 0 & 3 \end{bmatrix}
$$
Which would indicate that we know the position with more accuracy; and assume $R$ is 10. 


# Notes

Estimation is helpful to get a smoother curve to get a best estimate of the state, but also to make it smoother so we can take a derivative if necessary. 

In global algorithms, include fault detectors to track sensor standard deviation over time. 