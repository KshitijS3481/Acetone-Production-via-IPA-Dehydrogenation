# Continuous Acetone Production via Isopropanol (IPA) Dehydrogenation
**CHE453: Process Design Capstone Project | Department of Chemical Engineering, IIT Kanpur**

## 📋 Project Overview
This repository contains the process simulation files, rigorous equipment sizing, heat exchanger network (HEN) designs, and techno-economic evaluations for a continuous chemical plant producing **99.9 mol% high-purity Acetone** via the catalytic dehydrogenation of Isopropanol (IPA). 

The plant processes a fresh liquid feed of **$50\text{ kmol/h}$** ($67\text{ mol\%}$ IPA, $33\text{ mol\%}$ Water) and incorporates a closed-loop unreacted IPA recycle, achieving an overall acetone yield of **~94%**. Furthermore, the facility achieves complete electrical self-sufficiency by valorizing byproduct hydrogen gas in an integrated captive power plant.

---

## ⚙️ Key Process & Design Highlights

### 1. Thermodynamic Modeling & Validation
* **Property Package:** Non-Random Two-Liquid (**NRTL**) activity coefficient model selected over UNIQUAC and Peng-Robinson to accurately capture the IPA-Water azeotrope.
* **Parameter Regression:** Fine-tuned 5 binary interaction parameters against experimental VLE (`BinaryVLE145`) and azeotropic (`AZEO013`) datasets in Aspen Plus V14.
* **Supercritical Gas Handling:** Defined Hydrogen (`HYDRO-01`) as a **Henry’s Law component** to prevent VLE convergence errors and accurately calculate trace liquid-phase solubility.

### 2. Reaction & Separation Architecture
* **Multi-Tubular Plug-Flow Reactor (`RPlug`):** Modeled with reversible power-law kinetics ($450\text{ tubes}$, $6.096\text{ m}$ length, $0.0504\text{ m}$ diameter) operating isothermally near $350^\circ\text{C}$ ($623\text{ K}$) and $2.5\text{ atm}$, achieving **>90% single-pass conversion** with built-in catalyst deactivation margin.
* **Vapor-Liquid Recovery:** Two-stage cooling followed by a Flash Drum ($20^\circ\text{C}$, $1.5\text{ atm}$) for $90\%$ liquid acetone recovery, paired with a 10-stage water-wash Absorber ($20\text{ kmol/h}$ fresh water) to scrub residual organics from the hydrogen vent.
* **Distillation & Recycle:** Two-column `RadFrac` sequence (`C1` with 34 stages at $RR = 2.5$ for $99.9\%$ Acetone distillate; `C2` with 20 stages at $RR = 0.61$ for wastewater removal and unreacted IPA recycle).

### 3. Manual Heat Integration & Mechanical Design
* **Deterministic HEN Synthesis:** Automated Pinch Analysis in Aspen Energy Analyzer proposed impractical cross-exchanges using internal distillation column traffic. To protect column hydraulics and controllability, a manual integration strategy was executed:
  * **`HEATEX2` Integration:** Recovers high-grade sensible heat from the $349.6^\circ\text{C}$ reactor effluent to pre-heat the vaporizer feed (`VAPIN` $\rightarrow$ `VAPINF`), drastically reducing external LP steam demand.
  * **Wastewater Quench Loop:** Routes $100^\circ\text{C}$ wastewater bottoms (`C2B`) backward into the primary cooling section (`HEATEX`), simultaneously cooling the discharge stream and reducing fresh cooling water consumption.
* **Rigorous Sizing:** Primary cooler (`HX1`, TEMA BES) and reboiler (`E-100`, TEMA BKU kettle) mechanically rated and sized using **Aspen Exchanger Design and Rating (EDR)**.

### 4. Innovation: Hydrogen-Fired Brayton Cycle
* Rather than flaring or selling byproduct $H_2$ at a low margin, the separated hydrogen vapor stream is combusted with compressed air in an `RGibbs` combustor to drive a captive gas turbine.
* **Power Balance:** Generates **$987.63\text{ kW}$** gross shaft work against **$241.20\text{ kW}$** compressor work, yielding **$746.43\text{ kW}$ net power**—exceeding the plant's total electrical requirement of **$614.16\text{ kW}$** by $21.5\%$ with zero direct $\text{CO}_2$ emissions.

---

## 📊 Techno-Economic Summary (APEA)

| Metric | Value |
| :--- | :--- |
| **Total Capital Expenditure (CapEx)** | $\$5,200,830\text{ USD}$ |
| **Annual Operating Cost (OpEx)** | $\$26,684,500\text{ USD/year}$ |
| **Annual Product Revenue** | $\$33,868,100\text{ USD/year}$ |
| **Gross Operating Margin** | $\$7,183,600\text{ USD/year}$ |
| **Internal Rate of Return (IRR)** | **$42.71\%$** |
| **Payout / Payback Period** | **$4.70\text{ years}$** |
| **Net Electrical Self-Sufficiency** | **$100\%$** ($+132.27\text{ kW}$ surplus) |

---

## 🛠️ Software & Tools Used
* **Aspen Plus V14:** Steady-state flowsheet simulation, VLE regression, and sensitivity analyses.
* **Aspen Exchanger Design and Rating (EDR):** Rigorous shell-and-tube thermal and mechanical design.
* **Aspen Energy Analyzer (AEA):** Composite curve generation and pinch diagnostics.
* **Aspen Process Economic Analyzer (APEA):** Equipment sizing, bare-module costing, and 10-year DCF/NPV evaluation.
  
---

## 👥 Team 5 Contributors
* **Aarnav Gupta** 
* **Khushi Khandelwal** 
* **Krish Agarwal** 
* **Kshitij Srivastava** 
* **Shagun** 
* **Shreyas Gupta** 

*Supervised by Dr. Raghavendra Ragipani, Department of Chemical Engineering, IIT Kanpur.*
