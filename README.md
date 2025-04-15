# basic-flow-of-physical-design


# basic-flow-of-physical-design

# Interface Block – Physical Design Project 

Peripheral Controller – Physical Design Project (14 nm) *(jun 2023 – may 2024)

This repository presents a detailed breakdown of a physical design project implemented at the  14nm and technology node. The block-level implementation spans from initial floorplanning to final signoff. The project involved handling high macro density and multiple critical timing paths, pushing for both performance and physical design efficiency.

##  Project Details
- **Technology Node**: 14nm 
- **Standard Cell Count**: 380K 
- **Number of Macros**: 86
- **Clock Frequency**: 1.2 GHz
- **Role**: Block-level Physical Design Engineer (RTL2GDS)
- **Tools**: ICC2_SHELL , PRIMETIME , DESIGN COMPAILER 

---

##  Physical Design Stages

### 🔹 Floorplanning
Defines the physical layout boundary and initial macro placement to ensure routability and optimal timing.

**Tasks Performed:**
- Defined aspect ratio and die size after area analysis.
- Placed 86 macros considering connectivity, IO pin locations, and blockage strategy.
- Created soft blockages to guide placement tools and avoid clustering.
- Partitioned the design logically for better congestion control.

**Fixation Methods:**
- Manual macro reordering to minimize routing congestion.
- Channel creation between macro rows to ease signal routing.

**Challenges:**
- High macro count led to dense channel areas.
- Congestion observed near IO ports required multiple iterations of macro movement 

---

### 🔹 Power Planning
Ensures robust power delivery network and mitigates IR drop issues across the layout.

**Tasks Performed:**
- Created grid-based power distribution across the die using top metal layers.
- Dropped power stripes in vertical and horizontal orientations based on IR drop map.
- Connected macros and standard cells to the power grid using vias and M1 taps.

**Fixation Methods:**
- Added secondary stripes on higher metals to reduce resistance.
- Increased via counts and optimized tap cell locations

**Challenges:**
- Initial IR analysis showed hot spots around macro clusters.


---

### 🔹 Placement
Arranges standard cells in legal locations while minimizing congestion and preserving timing quality.

**Tasks Performed:**
- Optimized placement using congestion-driven algorithms.
- Maintained placement blockages around high-fanout regions.
- Used soft guide regions to steer standard cell spreading.

**Fixation Methods:**
- Applied cell padding around congested zones.
- Used partial placement blockage over macros to prevent spillovers.

**Challenges:**
- Buffer insertion caused overlap violations.


---

### 🔹 Clock Tree Synthesis (CTS)
Distributes the clock signal with minimal skew and optimal insertion delay.

**Tasks Performed:**
- Built H-tree based clock tree balancing strategy.
- Inserted clock buffers to meet skew targets under 200ps.
- skew grouping and latency optimization 
- desifined some exeption for macro pins with some letency

**Fixation Methods:**
- Manual push-pull of buffers to align skew across critical endpoints.

**Challenges:**
- CTS induced extra congestion around macro corners.


---

### 🔹 Routing
Connects all logic nets adhering to DRC and signal integrity constraints.

**Tasks Performed:**
- Completed global and detailed routing.
- Performed short fixing, antenna correction, and DRC checks.
- Guided critical nets manually to avoid detours.

**Fixation Methods:**
- Applied routing blockages in congested zones.
- Used non-default rules for clock nets.

**Challenges:**
- Signal detours near dense regions led to increased delay.
- Needed timing rebalancing post-routing.

---

### 🔹 Static Timing Analysis (STA) & ECOs
Analyzes timing constraints and performs incremental changes to close violations.

**Tasks Performed:**
- Ran STA in multiple PVT corners.
- Performed setup/hold ECOs using tool-based and manual strategies.
- Balanced data paths using cell sizing and logic restructuring.

**Fixation Methods:**
- Applied late-stage hold fixes via buffer and  delay cells.
- Used functional ECOs to avoid full re-synthesis.

**Challenges:**
- Timing margin tight near IO and scan chains.

---

### 🔹 Physical Verification & Signoff
Final stage ensuring DRC/LVS clean and IR-safe layout before tapeout.

**Tasks Performed:**
- Ran full DRC and LVS with Calibre.
- Fixed base-layer and via violations using updated rules.
  

**Fixation Methods:**
- Fixed metal width violations with cells.
- Reworked power mesh and switching cells for IR safety.

**Challenges:**
- Baselayer DRCs due to over-buffed areas.

---

## ✅ Conclusion
This 14nm block presented a rich learning experience with real-world constraints in timing closure, IR drop, and physical congestion. It sharpened my hands-on capabilities across the RTL2GDS flow and enhanced my debug instincts across signoff challenges.

---

## 📌 Disclaimer
This repo is a knowledge showcase based on real experience and does not contain confidential or proprietary data.
