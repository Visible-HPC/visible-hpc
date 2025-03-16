# Mini-HPC Cluster Specification - Version 1

Building on the [requirements](./requirements.md) and the [hardware options](./hardware.md) detailed in other files in this section, an initial cluster specification has been developed and a prototype is being built.

**Single board computer:** **Raspberry Pi 5**

At the heart of the cluster will be a series of [Raspberry Pi 5](https://www.raspberrypi.com/products/raspberry-pi-5/) nodes. While there are many different options available, the Raspberry Pi 5 wins out due to its easy availability, reasonable cost and the huge range of add-on boards and supporting hardware and software infrastructure available through the extensive online community. While some of the other boards considered do offer the potential for slightly higher performance and additional features such as an on-board TPU and/or eMMC storage, it was decided that the Raspberry Pi 5 offers by far the best trade-off for this initial protoype cluster. The version of the Pi 5 offering 8GB RAM will be used. Although there is now a 16GB RAM version, this represents a significant cost increase and is not considered to be necessary for intended use of this prototype cluster.

**Number of nodes:** The cluster will have 32+4 nodes. 32 nodes will act as compute nodes with the additional 4 nodes providing an interactive node for users to connect to and a storage server. A variety of different options exist for storage and these require further consideration. More details will be provided in the software section when this is available.

**Power:** The cluster will be powered via Power-over-Ethernet (PoE). This will significantly simply the wiring for the cluster, requiring only a single Ethernet cable to be routed from the network switch to each Raspberry Pi. This also consolidates all the connectivity and power infrastructure into one unit - the network switch. Each Raspbery Pi will be fitted with a PoE+ "HAT" to support this. It is currently anticipated that the [UCTRONICS PoE+ HAT for Raspberry Pi 5](https://www.uctronics.com/uctronics-poe-hat-for-raspberry-pi-5-power-over-ethernet-with-active-cooling-fan-aluminum-heatsink-supports-ieee-802-3af-at-network-standard-5v-4-5a-max.html) (model: U627802) will be used for this purpose. It is possible that the cluster "head node" may be powered directly from a PSU but this is yet to be determined.

**Casing:**

[19-inch rack]

[PDU]

**Rack-mount solution:**

**Network switch**:

**Additional hardware:**