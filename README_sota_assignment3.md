# 🤖 Sota Basic Control Project - Assignment 3 (COMP 4060)

This project implements forward and inverse kinematics, joint mapping, and motion control for the Sota humanoid robot as part of **COMP 4060: Robotics for Human-Robot Interaction**.

Most of the implementation is located in the `src/AS3/` directory.

---

## 📁 Key Folder: `src/AS3/`

This directory includes all major components of the assignment:

```
src/
└── AS3/
    ├── AS3_1.java              # Task 1: Motor mapping and ServoRangeTool
    ├── AS3_2.java              # Task 2: Test motor ranges and neutral pose
    ├── AS3_3.java              # Task 3: Motor-to-radian conversion
    ├── AS3_4.java              # Task 4: Forward Kinematics
    ├── AS3_5.java              # Task 5: Inverse Kinematics (Jacobian-based)
    ├── ServoRangeTool.java     # Serializable tool to track joint limits
    ├── SotaForwardK.java       # Core class for FK computation
    ├── SotaInverseK.java       # Newton-Raphson based IK solver
    └── MatrixHelp.java         # Utility matrix operations (T, R, print, etc.)
```

---

## 🧪 Tasks Summary

### Task 1: Map Motor Ranges (`AS3_1.java`)
- Maps servo joint limits by reading live positions during manual manipulation.
- Stores min, max, and neutral positions to a file using `ServoRangeTool`.

### Task 2: Test Motor Ranges (`AS3_2.java`)
- Loads saved servo ranges and tests each joint through its range of motion.
- Returns robot to neutral pose after min/max testing per joint.
- Observes "dead zones" in elbow due to gear backlash.

### Task 3: Convert to Radians (`AS3_3.java`)
- Maps motor positions to radian space using linear transformation.
- Based on URDF-defined min/max radians and observed servo ranges.
- Supports both forward and inverse radian-to-position conversion.

### Task 4: Forward Kinematics (`AS3_4.java`)
- Builds transformation matrices for each robot joint.
- Calculates global frame positions using matrix chaining.
- Special handling for elbow frame due to missing rotation in URDF.

### Task 5: Inverse Kinematics (`AS3_5.java`)
- Implements numerical Jacobian using finite differences.
- Uses pseudoinverse to calculate joint updates.
- Newton-Raphson solver iterates to minimize end-effector error.

---

## 🧠 Concepts Applied

- Frame translation and URDF analysis
- Matrix algebra and transformation chains
- Numerical Jacobians and optimization
- Real-time servo control and state validation
- Data serialization and robot kinematic modeling

---

## 📝 Reflections and Observations

- Minor mechanical and sensor tolerances lead to different joint readings per run.
- Gear backlash introduces dead zones, especially in the elbow.
- Accurate FK depends on compensating missing URDF rotations with manual corrections.
- Small deltas in Jacobian computation yield accurate inverse kinematics, large ones fail.

---

## ▶️ How to Run

1. Navigate to the `src/AS3/` folder.
2. Compile and run each file based on the task you're working on:

```bash
javac AS3_1.java
java AS3_1
```

---

## 👨‍💻 Authors

- Cuong Ta - 7900562  
- Het Patel - 7972424  
- Dipesh Shah - 7882947

---

## 📄 License

Academic project under University of Manitoba’s COMP4060 course. Educational use only.