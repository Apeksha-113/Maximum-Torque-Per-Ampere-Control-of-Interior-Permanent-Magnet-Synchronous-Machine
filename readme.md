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
aa


<figure style="text-align: center;">
  <img src="https://github.com/Apeksha-113/Maximum-Torque-Per-Ampere-Control-of-Interior-Permanent-Magnet-Synchronous-Machine/blob/MTPA/MTPA_Pic/m/torque%20vs%20gamma.png?raw=true" alt="Torque vs. Current gamma">
  <figcaption>Figure 1: Torque vs. Current gamma</figcaption>
</figure>

![Torque vs. Speed Characteristics]()




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

## Methodology
The overall control scheme involves implementing the MTPA algorithm to minimize stator current for the required torque.

### Proposed Scheme (MTPA Control)
1. Initial \( i_m^* \) calculation with \( i_d = 0 \) assumption.
2. Actual optimized \( i_m^* \) calculation.
3. Actual \( i_d \) and \( i_q \) calculation.
4. Calculation of optimum current angle.

![Flowchart](path_to_image)
![Block Diagram of Proposed Scheme](path_to_image)

### Simulation/Modeling
- Simulation/Modeling of PMSM
- Simulation/Modeling of Torque
- Simulation/Modeling of Speed and Current Controller
- Simulation/Modeling of MTPA Control Scheme

![Simulation](path_to_image)
![Speed Calculation](path_to_image)
![Torque Calculation](path_to_image)
![Speed and Current Controller](path_to_image)
![MTPA Implementation](path_to_image)

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
