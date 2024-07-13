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
  <figcaption>Figure 2: Fig.2.  Torque Vs Current angle
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
<figure style="text-align: center;">
  <img src="https://github.com/Apeksha-113/Maximum-Torque-Per-Ampere-Control-of-Interior-Permanent-Magnet-Synchronous-Machine/blob/MTPA/MTPA_Pic/Blockdiagram%20of%20proposed%20scheme.png?raw=true">
  <figcaption>Figure 3: Block Diagram of PMSM</figcaption>
</figure>

Figure 3 is the complete schematic of our proposed solution. The parameters of the PMSM are listed in the table below.

### Parameters Used for the Model
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


### Proposed Scheme: MTPA Controller
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
  <figcaption>Figure 5: </figcaption>
</figure>

---

## Result and Analysis
- **Torque-Speed Characteristics:** To verify the modeling of the PMSM, we created a plot showing the relationship between torque and speed by setting the load torque to 70N-m and varying the speed starting from 0.

![Modelled Torque vs Speed](path_to_image)
![Theoretical Torque vs Speed](path_to_image)

### Performance Assessment
We observed the output of the proposed system under four different scenarios:
1. Constant Speed and Torque
2. Constant Speed and Variable Torque
3. Variable Speed and Constant Torque
4. Variable Speed and Variable Torque

---

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

*Note: Replace `path_to_image` with the actual path to the images in your repository.*
