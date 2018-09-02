## LIFT Challenge 2018: Open-Storm Detroit Dynamics

**Team Members**
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
settings) are accessed via [PySWMM](https://github.com/OpenWaterAnalytics/pyswmm),
a Python language SWMM wrapper.

The control algorithm employed here is Market-Based Control in which decisions
are made in a virtual marketplace where a commodity is bought and sold by
system agents. In this case, the commodity is volumetric capacity within the
sewer system, the buyers of this commodity are upstream storage agents
(e.g., pump stations, storage basins, inflatable storage dams), and the sellers
are downstream points within the sewer network, more specifically the water
resources recovery facility. Price of the commodity fluctuates through time and
is based on the current state of the system: how much capacity is available and
how greatly it is demanded by upstream agents. Water is moved throughout the
system via ''purchases'' of capacity by upstream agents, which dictate how much
stored water each upstream agent can release to the downstream agents. Because
the system considered here is so large and spatially distributed, we divide the
system into sub-markets, each with its own price of capacity.

Each buyer/upstream agent has a particular wealth with which to ''purchase''
capacity which is based on its current volume normalized to its maximum volume
capacity; thus, if a storage agent is close to using all of its available
volume, it poses more wealth to ''purchase'' more capacity from downstream,
that is release more water to avoid flooding locally. The wealth for upstream
agent $i$ is computed via

$P_{wealth,i} = uparam \times V_{up,i}$

where $uparam$ is a weighting parameter describing priority toward mitigating
local upstream flooding, $V_{up,i}$ is the normalized volume at upstream agent
$i$.
