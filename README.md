## LIFT Challenge 2018: Open-Storm Detroit Dynamics

#### Team Members
* **Wendy Barrot**, Program Director R&D, GLWA
* **Christopher Nastally**, Manager, GLWA
* **Branko Kerkez**, Assistant Professor, University of Michigan
* **Sara Troutman**, Ph.D. Student, University of Michigan
* **Abhiram Mullapudi**, Ph.D. Student, University of Michigan
* **Gregory Ewing**, Research Scientist, University of Michigan

In a collaboration between the GLWA (Great Lakes Water Authority) and Real-Time
Water Systems Lab at the University of Michigan, we investigate the application
of dynamic control to existing infrastructure in real-time to:
* Maximize current storage utilization
* Reduce combined sewer overflows
* Equalize flow to the water resources recovery facility
We aim to deliver a web-based decision support tool to be used by operators of
the sewer network during wet-weather events. The tool is informed by control
algorithms developed through the LIFT Challenge.

Within this repository are functions that execute the control algorithms used
to inform the decision support tool. While we do not share the underlying
GLWA system model, those interested will be able to apply the control functions
to their own system. The underlying model is an EPA SWMM input file; system
states and control actions for system assets (e.g., gate positions, pump target
setting) are accessed via [PySWMM](https://github.com/OpenWaterAnalytics/pyswmm),
a Python language SWMM wrapper.
