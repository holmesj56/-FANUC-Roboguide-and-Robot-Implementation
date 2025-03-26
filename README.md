
# 🦾 FANUC Roboguide Digital Workcells -  Project 
This repository documents the creation of three digital robotic workcells designed and simulated in **FANUC Roboguide** for different industrial automation applications: **palletizing, machine tending, and assembly (kitting)**. Each cell was developed to meet specific cycle time and safety requirements, with realistic robot and EOAT (End of Arm Tooling) selections, proper I/O integration, animated gripper and part movements, and cell status indicators. The video demonstration of the palletizing task is included at the end.

---
## 📦 CAD Files Used

The following `.IGS` CAD files were imported into **FANUC Roboguide** to construct and simulate the digital workcells:

| File Name | Description | Usage |
|-----------|-------------|-------|
| **Cube.IGS** | Uniform cube part | Used for the **palletizing** task; picked from conveyor and placed into a box. |
| **Box.IGS** | Container for palletized parts | Represents the destination container for cubes in the palletizing cell. |
| **Kitting opperation.IGS** | Full kit tray layout | Base model used in the **kitting** operation where 5 distinct parts are placed. |
| **Tray.IGS** | Part tray for components | Used for organizing parts during **kitting** or **machine tending**. |
| **Circle.IGS** | Circular part | One of the components placed during **kitting**. |
| **Square.IGS** | Square part | One of the components placed during **kitting**. |
| **Hexagon.IGS** | Hexagonal part | One of the components placed during **kitting**. |
| **Triangle.IGS** | Triangular part | One of the components placed during **kitting**. |

These files were essential in building accurate simulations and validating robot path planning, gripper actions, and part placements within each cell.

## 1️⃣ Palletizing Cubes from Conveyor

**Application**: Automated palletizing of uniform small cube parts from a conveyor into a larger box.

**Specifications**:
- A new cube part is presented every **10 seconds**
- Each large box holds **270 parts**
- Cubes were sourced from the Canvas folder (`Cube` part file)
- Box is placed on a separate conveyor for collection

**Robot Selection**:
- **FANUC M-20iA**: Chosen for its high-speed handling and precision for small, uniform parts.
- _Justification_: Excellent payload-to-weight ratio, ideal for high-speed pick-and-place; supports I/O expansion for gripper and sensors.

**EOAT**:
- **Vacuum Gripper**
- _Justification_: Reliable suction on flat surfaces, reduced mechanical complexity, and faster actuation for high cycle time tasks.

**I/O Implementation**:
- Sensors detect cube presence on the conveyor
- Gripper suction feedback
- Light bar status:
  - 🟢 **Green**: Running
  - 🟡 **Yellow**: Waiting
  - 🔴 **Red**: Stopped/Error

**Safety Measures**:
- **Software Interlocks**: Emergency stop, conveyor sync checks
- **Mechanical**: Light curtains, fencing around cell

---

## 2️⃣ CNC Lathe Machine Tending Cell

**Application**: Machine tending for a CNC lathe (`CNCTurningmachine1`) with autonomous operation for 24 hours.

**Specifications**:
- Operation cycles: **350**, **600**, **1000**
- Separate raw part and finished part areas
- All parts must be processed during operation

**Robot Selection**:
- **FANUC R-2000iC/165F**
- _Justification_: Robust for loading/unloading heavy parts, good reach into lathe, fast cycle time for sustained 24-hour ops.

**EOAT**:
- **Pneumatic Gripper**
- _Justification_: Strong, fast, and safe for cylindrical metal components; integrated sensors for open/close feedback.

**I/O Implementation**:
- Part-present sensors at raw and finished zones
- Gripper open/close control via digital outputs
- Light bar status:
  - 🟢 **Green**: Robot in operation
  - 🔵 **Blue**: Waiting for part
  - 🔴 **Red**: Machine stop or error

**Safety Measures**:
- **Mechanical**: Guarded cell with interlock doors
- **Software**: CNC interface checks, robot-lathe synchronization, collision zones defined in Roboguide

---

## 3️⃣ Kitting Assembly Operation

**Application**: Assemble a kit of 5 distinct non-uniform parts into specific locations within a container.

**Specifications**:
- Parts are placed in specific orientations and angles
- Kit CAD files were imported from Canvas

**Robot Selection**:
- **FANUC LR Mate 200iD**
- _Justification_: Excellent dexterity, ideal for small part handling and tight working areas.

**EOAT**:
- **Electric Gripper**
- _Justification_: Needed for precision gripping, repeatability, and force control on distinct part shapes.

**I/O Implementation**:
- Color sensors and position feedback for correct part pickup
- Gripper angle control and status
- Light bar status:
  - 🟢 **Green**: Kitting in progress
  - 🟠 **Orange**: Part missing/misaligned
  - 🔴 **Red**: Error or emergency

**Safety Measures**:
- **Software**: Part detection logic, container full checks
- **Mechanical**: Clear operator space, emergency stop

---

## 🎥 Final Demo Video – Palletizing Task

The video below showcases the **palletizing task**, where the FANUC M-20iA robot picks small cubes from a conveyor and places them into a larger box on a second conveyor. The simulation shows animated gripper behavior, part handling, light bar feedback, and I/O operation.

👉 **[Watch the Demo Video on YouTube](https://youtu.be/xdYfMPTStSg)**

---

Explore the `workcells/` directory for Roboguide simulation files and CAD models used in this project. Contributions, suggestions, and forks are welcome!
