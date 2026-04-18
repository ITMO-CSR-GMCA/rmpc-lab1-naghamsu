[README_Nagham_Sleman476937.md.md](https://github.com/user-attachments/files/26853770/README_Nagham_Sleman476937.md.md)
[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/L0glmnMn)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23564520&assignment_repo_type=AssignmentRepo)
# RMPC-lab1

First laboratory work for course Robot Motion Planning and Control.

Assignment

1. For the selected robot option, load the manipulator model from the toolbox **different then Puma560** and output the Denavit-Hartenberg parameters.
2. Specify the masses of the links, the positions of their centers of mass, the tensors of inertia, the moments of inertia of the drives, the coefficients of viscous friction of the drives, the coefficients of Coulomb friction of the drives, the gear ratios of the reducers and the constraints on the generalized coordinates. It is recommended to refer to the data sheets of the manipulators used.
3. Specify and display arbitrary initial and final configurations of the robot.
4. Plan a trajectory between the specified configurations.
5. Solve the inverse dynamics problem using the Newton-Euler method for the following scenarios: <br>
+ non-zero velocities and accelerations $\dot{q} \neq 0, \ddot{q} \neq 0$;
+ non-zero velocities and negligible accelerations $\dot{q} \neq 0, \ddot{q} \approx 0$ - quasi-statics;
+ zero velocities and accelerations $\dot{q} = 0, \ddot{q} = 0$ - maintaining a given position;
6. Determine the numerical values ​​of the elements of the matrices $M(q), C(q, \dot{q}), G(q)$ at each calculated moment of time.
7. Plot graphs of the moments of the manipulator links along the trajectory for each scenario (see point #5).






  # Lab 1: Dynamic Model of a Multi-Link Manipulator (UR5)
## Nagham Sleman  ISO:476937


## 1. Objective
The objective of this lab is to study and analyze the dynamic behavior of a multi-link robotic manipulator using Python and the Robotics Toolbox.  
The UR5 robot is selected as the study case.

---

## 2. Robot Model
The UR5 manipulator is a 6-degree-of-freedom (6-DOF) robot with revolute joints.  
It is modeled using the Denavit–Hartenberg (DH) convention, which describes the geometry of the robot links.

Each link is defined by:
- θ (joint angle)
- d (link offset)
- a (link length)
- α (link twist)

---

## 3. Dynamic Parameters
The dynamic properties of the robot are defined manually, including:

- Link masses (m)
- Centers of mass (r)
- Inertia tensors (I)
- Motor inertia (Jm)
- Viscous friction (B)
- Coulomb friction (Tc)
- Gear ratios (G)
- Joint limits (qlim)

Some values are taken from available data, while others are approximated due to missing detailed datasheet information.

---

## 4. Initial and Final Configurations
Two configurations are defined:

- Initial position:
  q_start = [0, 0, 0, 0, 0, 0]

- Final position:
  q_end = [π/4, -π/3, -π/4, π/3, -π/3, π/4]

The robot is visualized in both configurations using plotting functions.

---

## 5. Trajectory Planning
The trajectory between the initial and final configurations is generated using:

### 5.1 jtraj (Polynomial Trajectory)
- Smooth interpolation
- Continuous velocity and acceleration

### 5.2 mtraj (Trapezoidal Trajectory)
- More realistic motion
- Includes acceleration, constant velocity, and deceleration phases

---

## 6. Inverse Dynamics
The Newton–Euler method is used to compute joint torques for three cases:

1. Full dynamics:
   (q̇ ≠ 0, q̈ ≠ 0)

2. Quasi-static case:
   (q̇ ≠ 0, q̈ ≈ 0)

3. Static case:
   (q̇ = 0, q̈ = 0)

The torque is calculated using:
tau = robot.rne(q, qd, qdd)

---

## 7. Dynamic Model Components
The equation of motion is:

                  τ = M(q)q̈ + C(q, q̇)q̇ + G(q)

Where:
- M(q): inertia matrix
- C(q, q̇): Coriolis and centrifugal effects
- G(q): gravity vector

These matrices are computed numerically along the trajectory.

---

## 8. Results
- Joint torques change depending on motion conditions.
- Higher torques are observed in joints closer to the base.
- Static case shows only gravity effects.
- Quasi-static case is close to full dynamics when acceleration is small.
- mtraj produces smoother torque profiles than jtraj.

---

## 9. Conclusion
This lab demonstrates the importance of dynamic modeling in robotics.  
Different trajectories and motion conditions significantly affect torque requirements.

The Newton–Euler method is effective for solving inverse dynamics.  
Using realistic trajectories improves simulation accuracy.
8. Create a report in .ipynb format, with detailed comments.
9. All steps and conclusions are formulated based on the results of the work in README.md
  
