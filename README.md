<p align="center">
  <a href="https://static.platzi.com/media/achievements/badge-analista-negocios-rpa-bcfb39a9-8fc2-48ce-b3c8-d789beaf70e8.png" target="_blank">
    <img alt="Industrial Robotics" src="https://static.platzi.com/media/achievements/badge-analista-negocios-rpa-bcfb39a9-8fc2-48ce-b3c8-d789beaf70e8.png" width="60" />
  </a>
</p>
<h1 align="center">
  Control of a 3DOF Anthropomorphic Robot
</h1>
<p align="center">
  <a href="https://youtu.be/8o4RfsvxuKg" target="_blank">
    Demo Video
  </a>
</p>

Project created by:
- Cesar Eduardo Monterrubio Morales A01067371
- Luis Mario Flores Campos – A01065662
- Fernando Mejía Laguna – A01246227

Supervised by Dr. Alejandro González de Alba - Tecnológico de Monterrey

* [A brief introduction to the project](#-🤖-A-brief-introduction-to-the-project)
* [Robot concepts](#-Robot-concepts)
* [Implementation details](#-Implementation-details)

# 🤖 A brief introduction to the project

This project describes the analysis and design of elements involved in controlling an anthropomorphic robot with 3 degrees of freedom. The robot was developed to be manipulated through a Human-Machine-Interface (HMI) implemented in MATLAB that communicates with Arduino to control the physical robot arm.

## 🔧 Project components

The project development was divided into multiple phases:
1. Design process - MATLAB HMI and CAD design
2. Direct Geometric Model (DGM) implementation
3. Inverse Geometric Model (IGM) implementation
4. Trajectory planning and control

### ⚙️ Robot concepts

#### 📊 DIRECT GEOMETRIC MODEL (DGM)
The Direct Geometric Model allows computation of the end-effector position using joint angle inputs. This model was implemented using Denavit-Hartenberg parameters and homogeneous transformation matrices.

#### 🔄 INVERSE GEOMETRIC MODEL (IGM)
The Inverse Geometric Model computes the required joint angles to position the end-effector at a specific coordinate. Two methods were implemented:
- Analytical method (Paul's method)
- Numerical method (using the Jacobian matrix)

#### 📈 TRAJECTORY PLANNING
The trajectory planning system allows the robot to follow predefined paths like straight lines and circles by using parametric equations and numerical approximation through the Jacobian matrix.

 <img src="https://github.com/itsluismario/Control-of-a-3DOF-anthropomorphic-robot/blob/main/diagram-of-anthropomorphic-robot-arm.png" alt="Anthropomorphic robot arm" width="500" height="200">

## 🛠️ Implementation details

### Materials used
- Arduino MEGA with cable
- SN74LS241N 
- Servo Robotis Dynamixel AX-12A (3)
- Dynamixel Cable (3)
- Various connectors (FP04-F2, FP04-F3, FP04-F4, FP04-P9, FP04-F11)

### DH Parameters
| i | a | α | d | θ |
|---|---|---|---|---|
| 1 | 0 | π/2 | L₁ | q₁ |
| 2 | L₂ | 0 | 0 | q₂ |
| 3 | L₃ | 0 | 0 | q₃ |

For the specific robot implementation: 
- L₁ = 89 mm
- L₂ = 67.5 mm
- L₃ = 98.43 mm

### Position equations
The position equations derived from the Direct Geometric Model are:
- X = cos(q₁)(L₂cos(q₂) + L₃cos(q₂ + q₃))
- Y = sin(q₁)(L₂cos(q₂) + L₃cos(q₂ + q₃))
- Z = L₁ + L₂sin(q₂) + L₃sin(q₂ + q₃)

### Trajectory implementation
The trajectory mode enables the robot to follow different paths defined by parametric equations. For example:

**Straight line:**
- X = 3n + 50
- Y = 7.5n + 75
- Z = 2n + 100

**Circular trajectory:**
- X = 40.38cos(πn/10 + 1.9514) + 65
- Y = 40.38sin(πn/10 - 1.1908) + 112.5
- Z = 2n + 100

### Results and Error Analysis
Testing showed an average positional error of about 5mm, with error sources including:
- Motor resolution (10-bit resolution providing steps of 300/1024 degrees)
- Motor torque limitations
- Measurement inaccuracies

### YouTube Demo Videos
- [Robot demonstration 1](https://youtu.be/8o4RfsvxuKg)
- [Robot demonstration 2](https://youtu.be/DBADfP6y6vM)

## 📚 References

1. Wagieh, A., & Instructables. (2019, June 14). Using Matlab app designer with Arduino.
2. Arduino support from Matlab. Hardware Support - MATLAB & Simulink.
3. Tuijthof, G. J. M., & Herder, J. L. (2000). Design, actuation and control of an anthropomorphic robot arm.
4. Duffy, B. R. (2003). Anthropomorphism and the social robot.
5. Unanyan, N. N., & Belov, A. A. (2021). Anthropomorphic arm control system with remote gesture tracking.
6. Hamerlain, M. (n.d.). An anthropomorphic robot arm driven by artificial muscles using a variable structure control.

Happy engineering!
