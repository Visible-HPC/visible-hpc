# Cluster requirements

The planned training cluster will have two core uses:

1. To support training in the use of High Performance Computing (HPC) clusters with a variety of access methods, but with a primary focus on batch job submission. The target audience of this training will be researchers and Research Technical Professionals (RTPs) with no prior HPC experience.

2. To provide a resource to support training in cluster design and deployment. This will require that the cluster can be easily broken down if a second set of hardware is not avialable.

### Specification

The portable training cluster specification needs to balance the aims of providing something that can be used to demonstrate key properties and hardware design of a full-size HPC cluster while also being portable and having low power requirements to ensure sustainability and to demonstrate green computing principles.

The **performance of individual nodes** is not critical since we envisage the resource being used primarily for relatively small-scale example computations. However, some level of computational capability will be useful in support of other possible future use cases.

Likewise, **network performance** between nodes is not critical although reasonable performance to support diskless compute nodes is likely to be important. We'd expect to have Gigabit networking between nodes but nothing beyond this is considered to be necessary or practical.

Key anticipated hardware requirements include:

 - x86_64 or ARM-based CPUs on compute nodes
 - 4 or more cores per node.
 - 24-64 compute nodes - anticipating 32 compute nodes to be realistic
 - 4GB minimum, 8GB+ RAM per compute node preferred
 - Gigabit wired ethernet networking
 - PCIe capability for connecting devices such as NVMe storage
 - ...

Other preferred poroperties include:

 - **19-inch rack-based hardware mounting:** This will enable demonstration of the way that regular HPC hardware is mounted in data centres.
 - **Enterprise networking hardware:** To demonstrate the type of switches that are used to support full-size clusters and, potentially, the type of management interfaces they use.
 - **PoE support:** Power-over-Ethernet to provide power to the compute nodes to simplify cabling and power distribution infrastructure.


### Existing work

We are aware of various existing activities building and using similar hardware for various purposes within the research community:

 - University of Edinburgh's "[Wee Archie](https://www.archer2.ac.uk/community/outreach/materials/wee_archie)" is an 18 node Raspberry Pi cluster (16 compute nodes, 2 controller nodes) that is used to demonstrate the principles of HPC clusters at a range of national and international events, with a focus on highlighting the capabilities and structure of the UK's national supercomputer, [ARCHER2](https://www.archer2.ac.uk/).

 - [CarpentriesOffline](https://carpentriesoffline.org/) has been set up to provide a way to run [Carpentries](https://carpentries.org/) training workshops in environments that have poor Internet connectivity. The project provides a specification for a small Raspberry Pi cluster and also maintains a bootable USB image that can be used to set up a server as a wireless access point hosting materials for running a Carpentries course.
