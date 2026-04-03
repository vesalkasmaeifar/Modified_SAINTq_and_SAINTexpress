# **Modifications to SAINTq & SAINTexpress**

## **Overview**
This repository contains **modifications** to SAINTq and SAINTexpress, originally developed for identifying high-confidence protein-protein interactions in BioID and AP-MS datasets.

The **original SAINT software** can be found here:  
[SAINT Official Page](https://saint-apms.sourceforge.net/Main.html)

## **Status of this Work**
- A **full evaluation of these modifications** is currently in preparation by **Kasmaeifar et al.**, in collaboration with the **original SAINT developers**.
- The results provided here are **preliminary** and subject to further validation.

## **What Changes Were Made?**
In both SAINTq and SAINTexpress, the **hardcoded minimum threshold** for intensity differences between baits and controls was removed:

- **SAINTq:** `log2(4) → log2(1)`
- **SAINTexpress:** `log(4) → log(1)`

### **Impact of This Modification**
✅ **Higher Sensitivity**  
- More interactors detected under the same Bayesian False Discovery Rate (BFDR).

✅ **More Accurate Intensity-Based Scoring**  
- Small but real intensity differences are preserved.
- Preys with lower intensity differences are no longer excluded.

❌ **Potential Increase in False Positives**  
- In datasets with **noisy controls**, this modification may lead to **higher FDR**.
- Performance depends on **instrument type, control design, and preprocessing**.

### **Example Dataset**
Using a dataset with baits **ACTB, KRT8, LMNA, and MAPRE3**:
- **Original SAINTexpress:** Detected fewer than 2 interactors per bait at **1% BFDR**.
- **Modified SAINTexpress:** Detected ,~50 interactors per bait aligning with known biology.
