# **Modified SAINTq & SAINTexpress**

## **Overview**
This repository contains **modified versions of SAINTq and SAINTexpress**, originally developed for identifying high-confidence protein-protein interactions in BioID and AP-MS datasets.

The **original SAINT software** can be found here:  
[SAINT Official Page](https://saint-apms.sourceforge.net/Main.html)

### **What This Repository Includes**
- **Modified SAINTq and SAINTexpress source code**
- **Build instructions** for compiling on Linux (Ubuntu)
- **Documentation on modifications and impact**

---

## **Modifications Made**
In both SAINTq and SAINTexpress, the **hardcoded minimum threshold** for intensity differences between baits and controls was removed:

- **SAINTq:** `log2(4) → log2(1)`
- **SAINTexpress:** `log(4) → log(1)`

These changes allow **smaller but biologically meaningful differences** to be preserved, leading to higher sensitivity in detecting interactors.

For more details, see [`docs/modifications.md`](docs/modifications.md).

---

## **Build Requirements**
This repository contains **all required libraries**, and only **GCC and G++ (versions 4.4 to 9)** need to be installed.

To check your GCC version:
```bash
gcc --version
g++ --version
```
For more details, see [`docs/build_requirements.md`](docs/build_requirements.md).

---

## **How to Compile**
Once the repository is cloned, compiling is as simple as running:

### **Compile SAINTq**
```bash
cd SAINTq
make -j
```
The compiled binary will be in `SAINTq/bin/`.

### **Compile SAINTexpress**
```bash
cd SAINTexpress
make -j
```
The compiled binary will be in `SAINTexpress/bin/`.

For troubleshooting, refer to [`docs/compilation.md`](docs/compilation.md).

---

## **Using the Modified SAINTq & SAINTexpress**
To run SAINTq:
```bash
./SAINTq/bin/saintq param_file
```
To run SAINTexpress:
```bash
./SAINTexpress/bin/SAINTexpress-int interaction_file.dat prey_file.dat bait_file.dat
```

---

## **Status of this Work**
- A **full evaluation of these modifications** is currently in preparation by **Kasmaeifar et al.**, in collaboration with the **original SAINT developers**.
- The results provided here are **preliminary** and subject to further validation.


## **Citing This Repository**
If you use this modified version of SAINTq/SAINTexpress, please cite this paper:

[_Optimizing Proximity Proteomics on the EvoSep-timsTOF LC–MS System_](https://doi.org/10.1002/pmic.70010)


---

## **Additional Notes**
- **This work builds on SAINTq and SAINTexpress; refer to the original license in SAINT documentation.**
- **Precompiled binaries are available under [GitHub Releases](https://github.com/vesalkasmaeifar/Modified_SAINTq_SAINTexpress/releases/tag/v1.0).**
