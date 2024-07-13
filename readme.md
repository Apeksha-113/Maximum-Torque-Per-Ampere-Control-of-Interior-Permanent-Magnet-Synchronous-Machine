# Maximum Torque Per Ampere Control of Interior Permanent Magnet Synchronous Machine

## Table of Contents
1. [Introduction](#introduction)
2. [Literature Review](#literature-review)
3. [Problem Statement](#problem-statement)
4. [Scope and Limitations](#scope-and-limitations)
5. [Methodology](#methodology)
6. [Result and Analysis](#result-and-analysis)
7. [Conclusion](#conclusion)
8. [References](#references)

---

## Introduction
PMSM is a synchronous motor that uses permanent magnet on the rotor instead of wound field coils that takes three phase ac supply as input and produces rotational motion. The synchronous speed of motor is determined by frequency of supplied ac. Highly efficient and requires precise control for optimizing performance.
Due to compactness, wider speed range and  large overload capacity, used in various applications like electric vehicles, robotics, and so on.

<figure style="text-align: center;">
  <img src="https://github.com/Apeksha-113/Maximum-Torque-Per-Ampere-Control-of-Interior-Permanent-Magnet-Synchronous-Machine/blob/MTPA/MTPA_Pic/TvS%20Characteristics.png?raw=true">
  <figcaption>Figure 1: Torque vs. Speed Characteristics</figcaption>
</figure>

### Torque Relationship With Current Angle (Gamma)
- For a current with constant magnitude, the torque of IPMSM will be different according to the angle of the stator current(gamma). ​

- By controlling the current angle, MTPA control generates the maximum torque with a specific current.

Torque produced by PMSM,

$$
Te = \frac{3}{2} * \frac{p}{2} * ((Ld - Lq) * id * iq + λm * iq)
$$

$$
id = im * cos(γ)
$$

$$
iq = im * sin(γ)
$$

<figure style="text-align: center;">
  <img src="https://github.com/Apeksha-113/Maximum-Torque-Per-Ampere-Control-of-Interior-Permanent-Magnet-Synchronous-Machine/blob/MTPA/MTPA_Pic/TvG.jpg?raw=true">
  <figcaption>Figure 2: Torque Vs Current angle
  </figcaption>
</figure>

---

## Literature Review
1. Paper [1] proposed direct torque control of PMSM without transformation into dq axis; fast but risks torque ripple and harmonics due to hysteresis.
2. Paper [2] suggested torque optimization by nullifying d-axis current; not suited for interior-type PMSMs.
3. Paper [3] explored flux weakening through stator current adjustment for torque at speeds beyond rated speed; suitable above rated speed only and faces losses and demagnetization challenges.
4. Paper [4] suggested AI-driven neural networks for accurate torque mapping; faces dataset training real-time challenges.

---

## Problem Statement
These various problems associated with the control of the motor couldn't solve our main problem i.e., optimizing current value for the production of desired torque effectively. This higher value of stator current rises several problems like increasing copper loss and reducing the efficiency of the motor. Long-term heating effect also leads to faster demagnetization of the magnet used.

---

## Objective:
- To reduce the value of current drawn by the motor to produce the desired torque and improve the efficiency of the motor.

---

## Scope and Limitations
**Scope:**

- Precise mathematical modeling of Interior PMSM.
- Modeling of three-phase inverter along with PWM generator for its switching action.
- Modeling of speed and current controller along with the implementation of MTPA control algorithm.

**Limitations:**
- Modeling of PMSM is based on constant parameters.
- Effect of temperature and voltage fluctuation not considered.
- Magnetic saturation, eddy current loss, and hysteresis losses are not considered in the modeling.
- Project excludes combined MTPA and Field-weakening strategy for a wider range.

---

## METHODOLOGY

### Overview
The overall methodologies of the project are mentioned below:
- **Step-1**: Study of literature and basic theories related to project topics
- **Step-2**: Problem identification
- **Step-3**: Development of Simulation model of PMSM
- **Step-4**: Development of Simulation model of PWM and Inverter
- **Step-5**: Analysis of the result obtained
- **Step-6**: Development of Simulation model of MTPA controller
- **Step-7**: Run the model and observe the result
- **Step-8**: Calculation of stator current from `i_d` and `i_q`
- **Step-9**: Comparison of our proposed scheme with the existing system
- **Step-10**: Development of overall simulation model and stating the outcomes

### Proposed Scheme
Figure 3 is the complete schematic of our proposed solution. The parameters of the PMSM are listed in the table below.
<figure style="text-align: center;">
  <img src="https://github.com/Apeksha-113/Maximum-Torque-Per-Ampere-Control-of-Interior-Permanent-Magnet-Synchronous-Machine/blob/MTPA/MTPA_Pic/Blockdiagram%20of%20proposed%20scheme.png?raw=true">
  <figcaption>Figure 3: Block Diagram of PMSM</figcaption>
</figure>


### Parameters Used for the Model

Table 1: The list of the Parameters used for the model
| **Parameter** | **Value** |
| ------------- | --------- |
| Rated Power | 4.3 Kw |
| Rated Torque | 70 N-m |
| Rated Speed | 575 rpm |
| Rated Current | 16 A |
| Stator resistance | 1.1 |
| Inductance along the direct-axis | 0.032 |
| Inductance along the quadrature axis | 0.066 |
| Torque Constant | 3.462 |
| Friction Coefficient | 0.017 |
| Moment of Inertia | 0.032 kg·m<sup>2</sup> |
| No of pole pair | 4 |
| `V_dc` | 450 |
| Stator flux linkage due to PMs | 0.6 Wb |


### MTPA Controller
It is used to generate the value of reference current which results in the maximum torque. The torque signal produced by the PI controller is fed to the MTPA controller which generates the optimum angle at which the current drawn by the motor is minimum to produce the required torque. The reference current in the direct and quadrature axis based on that particular current angle is produced as the output of the MTPA controller. 

Following overall control scheme involves implementing the MTPA algorithm to minimize stator current for the required torque.

<figure style="text-align: center;">
  <img src="https://github.com/Apeksha-113/Maximum-Torque-Per-Ampere-Control-of-Interior-Permanent-Magnet-Synchronous-Machine/blob/MTPA/MTPA_Pic/Flowchart.png?raw=true">
  <figcaption>Figure 4: Flowchart of Proposed Scheme</figcaption>
</figure>





### Simulation/Modeling
Simulation/Modelling of Overall Project using the MATLAB/simulink is shown below: 

<figure style="text-align: center;">
  <img src="https://github.com/Apeksha-113/Maximum-Torque-Per-Ampere-Control-of-Interior-Permanent-Magnet-Synchronous-Machine/blob/MTPA/MTPA_Pic/simulation%20modeling%20of%20overall%20project.jpg?raw=true">
  <figcaption>Figure 5: Overall Simulation </figcaption>
</figure>

---

## Result and Analysis

### Torque-Speed Characteristics
To verify the modeling of the PMSM, we created a plot showing the relationship between torque and speed by setting the load torque to 70N-m and varying the speed starting from 0.

Table 2: Torque Produced by the Motor at Different Speeds

| **Speed (rpm)** | **Torque Produced (N-m)** |
|-----------------|---------------------------|
| 100             | 70                        |
| 200             | 70                        |
| 300             | 70                        |
| 400             | 70                        |
| 410             | 70                        |
| 500             | 70                        |
| 575             | 70                        |
| 600             | 63                        |
| 700             | 43                        |
| 800             | 21                        |
| 900             | 13                        |

The graph below illustrates the relationship between the motor's torque output and its corresponding speed. Furthermore, the theoretical torque-speed characteristics of PMSM are also shown above in Figure 1. The striking resemblance between the two figures shows the validity of our PMSM model to real-world performance.

<figure style="text-align: center;">
  <img src="https://github.com/Apeksha-113/Maximum-Torque-Per-Ampere-Control-of-Interior-Permanent-Magnet-Synchronous-Machine/blob/MTPA/MTPA_Pic/modelled%20torque%20vs%20speed.png?raw=true">
  <figcaption>Figure 6: Modelled Torque vs Speed characteristics of motor
   </figcaption>
</figure>




### Performance Assessment
We observed the output of the proposed system under four different scenarios:
1. Constant Speed and Torque
2. Constant Speed and Variable Torque
3. Variable Speed and Constant Torque
4. Variable Speed and Variable Torque

---
### Stator Current Reduction
We recorded the stator current drawn by the motor implementing MTPA and without implementing the MTPA algorithm. The table below shows the acquired value of stator current at different load and torque conditions. We provided constant speed and step load torque.

Table 3: Comparison of Motor Currents with and without MTPA Algorithm at Various Speeds and Torques
| Speed | Torque | Without MTPA (Amp) | With MTPA (Amp) | Difference | Percentage change (%) |
|-------|--------|---------------------|-----------------|------------|------------------------|
| 300   | 10     | 2.82                | 2.77            | 0.05       | 1.78                   |
| 300   | 15     | 4.21                | 4.10            | 0.11       | 2.62                   |
| 300   | 20     | 5.59                | 5.38            | 0.21       | 3.76                   |
| 300   | 25     | 6.99                | 6.63            | 0.36       | 5.16                   |
| 300   | 30     | 8.38                | 7.81            | 0.57       | 6.81                   |
| 300   | 35     | 9.76                | 8.91            | 0.85       | 8.71                   |
| 300   | 40     | 11.15               | 9.98            | 1.17       | 10.50                  |
| 300   | 45     | 12.52               | 10.79           | 1.73       | 13.82                  |
| 300   | 50     | 13.92               | 11.94           | 1.98       | 14.23                  |
| 300   | 55     | 15.31               | 12.99           | 2.32       | 15.16                  |
| 300   | 60     | 16.82               | 13.91           | 2.91       | 17.31                  |
| 300   | 65     | 18.08               | 14.81           | 3.27       | 18.09                  |
| 300   | 70     | 19.46               | 15.69           | 3.77       | 19.38                  |
| 300   | 75     | 20.86               | 16.54           | 4.32       | 20.71                  |

The figure below shows the graph of current drawn by the motor implementing MTPA and without implementing the MTPA algorithm based on the data acquired.

<figure style="text-align: center;">
  <img src="https://github.com/Apeksha-113/Maximum-Torque-Per-Ampere-Control-of-Interior-Permanent-Magnet-Synchronous-Machine/blob/MTPA/MTPA_Pic/m/currentcomparision.png?raw=true">
  <figcaption>Figure 7: Comparison of stator current drawn vs torque with and without using MTPA algorithm
   </figcaption>
</figure>


It can be observed from both the table and the graph that the percentage change in the stator current drawn is significant during high torque.

### Copper Loss Reduction Rate
Utilizing the MTPA control scheme results in a reduction in copper loss compared to scenarios without MTPA.

- At high torque levels, the reduction rate in loss is notably increased, reaching almost 37%.

- Similarly, at low torque levels, the reduction rate in loss is increased to nearly 4%.

Table 4: Copper loss reduction at various torque condition

| Torque (Nm) | \((I1)^2\) | \((I2)^2\) | Cu Loss Reduction (%) |
|-------------|------------|------------|-----------------------|
| 10          | 7.96       | 7.68       | 3.52                  |
| 15          | 17.73      | 16.81      | 5.19                  |
| 20          | 31.25      | 28.95      | 7.36                  |
| 25          | 48.87      | 43.96      | 10.05                 |
| 30          | 70.23      | 61.00      | 13.15                 |
| 35          | 95.26      | 79.39      | 16.66                 |
| 40          | 124.33     | 99.61      | 19.89                 |
| 45          | 156.76     | 116.43     | 25.73                 |
| 50          | 193.77     | 142.57     | 26.43                 |
| 55          | 234.40     | 168.75     | 28.01                 |
| 60          | 282.92     | 193.49     | 31.61                 |
| 65          | 326.89     | 219.34     | 32.91                 |
| 70          | 378.70     | 246.18     | 35.00                 |
| 75          | 435.14     | 273.58     | 37.13                 |


Above table is depicted in figure below:

<figure style="text-align: center;">
  <img src="https://github.com/Apeksha-113/Maximum-Torque-Per-Ampere-Control-of-Interior-Permanent-Magnet-Synchronous-Machine/blob/MTPA/MTPA_Pic/m/cu%20loss.png?raw=true">
  <figcaption>Figure 8: Copper loss reduction in % at various torque conditions
   </figcaption>
</figure>

### Efficiency Analysis
Evaluated the efficiency of the PMSM, with particular attention to stator losses.

- At high torque levels, there was a notable improvement in efficiency, reaching almost 24%.

- At low torque levels, efficiency was increased to nearly 2%.
Table 5: Percentage Efficiency Improvement at various torque condition
 

| Torque (Nm) | % Efficiency Improvement |
|-------------|--------------------------|
| 10          | 1.81                     |
| 15          | 2.69                     |
| 20          | 3.91                     |
| 25          | 5.43                     |
| 30          | 7.30                     |
| 35          | 9.54                     |
| 40          | 11.73                    |
| 45          | 16.04                    |
| 50          | 16.59                    |
| 55          | 17.86                    |
| 60          | 20.93                    |
| 65          | 22.08                    |
| 70          | 24.03                    |


Above table is depicted in figure below:

<figure style="text-align: center;">
  <img src="https://github.com/Apeksha-113/Maximum-Torque-Per-Ampere-Control-of-Interior-Permanent-Magnet-Synchronous-Machine/blob/MTPA/MTPA_Pic/m/efficiency_improvement.png?raw=true">
  <figcaption>Figure 9: Percentage efficiency improvement at various torque condition
  </figcaption>
</figure>


## Conclusion
- Objective is to minimize stator copper loss and increase efficiency of PMSM using MTPA control.
- Implemented MTPA control based on constant parameters of motor models.
- Results after implementation:
  - 4% stator copper loss reduction at low torque.
  - 36% stator copper loss reduction at high torque.
  - 24% increase in efficiency at high torque.
  - 2% increase in efficiency at low torque levels.

---

## References
1. L. Zhong, M. F. Rahman, W. Y. Hu, and K. W. Lim, “Analysis of Direct Torque Control in Permanent Magnet Synchronous Motor Drives,” 1997.
2. O. E. Özçiflikçi, M. Koç, and S. Bahçeci, “Maximum torque per ampere strategy in IPM drives for electric vehicles,” El-Cezeri Journal of Science and Engineering, vol. 8, no. 3, pp. 1405–1415, 2021, doi: 10.31202/ecjse.932553.
3. K. Zhou, M. Ai, D. Sun, N. Jin, and X. Wu, “Field weakening operation control strategies of PMSM based on feedback linearization,” Energies (Basel), vol. 12, no. 23, Nov. 2019, doi: 10.3390/en12234526.
4. C. H. Lin, “A PMSM driven electric scooter system with a V-belt continuously variable transmission using a novel hybrid modified recurrent Legendre neural network control,” Journal of Power Electronics, vol. 14, no. 5, pp. 1008–1027, 2014, doi: 10.6113/JPE.2014.14.5.1008.
5. S.-H. Kim, “Pulse width modulation inverters,” in Electric Motor Control, Elsevier, 2017, pp. 265–340. doi: 10.1016/b978-0-12-812138-2.00007-6.
6. “CHAPTER4 MODEL OF THREE-PHASE INVERTER.”

---
