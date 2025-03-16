# Mini-HPC Cluster Hardware

In this file we look at some of the various hardware options that have been considered in terms of building the "visibleHPC" cluster
and also highlight the final choices made for the hardware.

### Hardware options

#### Single board computers

There are a number of widely available, small, low-power single-board computers which could provide the basis for this cluster. Candidates include:

 - [**Raspberry Pi**](https://www.raspberrypi.com/) - the latest Raspberry Pi, version 5, is powerful with a very strong supporting ecosystem of hardware.
 - [**OrangePi**](http://www.orangepi.org/) - The OrangePi 5 is based on the Rockchip RK3588 and potentially offers a number of performance benefits over the RPi 5.
 - [**BananaPi**](https://banana-pi.org/) - A set of boards based on a range of different form factors and processors. The BPI-M5 Pro is powered by the Rockchip RK3576 and provides eMMC storage. The BPI-M4 Berry is based around the Allwinner H618 SoC.
 - [**Okdo Rock 5**](https://uk.rs-online.com/web/c/raspberry-pi-arduino-development-tools/rock-sbc-shop/rock-sbc-boards/) - Another Rockchip-based device (RK3588S) offering a potential performance benefit to the Pi5 with more cores and an onboard TPU. Model A has an RPi-like format.
 - [**Jetson Nano**](https://developer.nvidia.com/embedded/jetson-nano) - Targeted more towards AI use-cases, combining quad-core ARM CPU and GPU with 128 CUDA cores.
 - [**BeagleY-AI**](https://www.beagleboard.org/boards/beagley-ai) - One of several devices from beagleboard.org. The BeagleY-AI comes in form-factor compatible with a wide range of existing add-ons and accessories. In addition a quad-core, 1.4GHz ARM-based CPU within its TI AM67A SoC, it also provides accelerated AI support including a 4TOPS matrix multiply accelerator.
 - [**ZimaBlade**](https://www.zimaspace.com/products/blade-personal-nas) - An x86-based single board computer - rather different to some of the other options here but a potential candidate for a cluster.
 - [**LattePanda**](https://www.lattepanda.com/) - Another x86-based SBC with onboard eMMC storage.

#### Storage

Working from regular SD/MicroSD cards is fine for booting devices at startup but reading from / writing to SD cards is too slow to support the sort of workloads and training activities we hope to use the Mini-HPC cluster for. Some of the boards listed above provide built-in eMMC units providing storage of 32, 64 or even 128GB onboard that offers much better performance than a removable SD card interface. Since almost all the above devices also provide USB3 support, there is the option to connect external spnning hard disks or SSDs, or via one of the increasingly low cost USB-to-NVMe converters, an M.2 PCIe NVMe drive can also be connected. In addition, some of the above boards have PCIe connectors that can support the add on of an M.2 NVMe board, or even have an on board M.2 NVMe SSD connector. This is considered to be the preferred form of storage for the planned cluster due its performance.

Since providing M.2 NVMe drives for each cluster node will significantly increase costs, we are also interested to investigate the potential for having diskless compute nodes and running everything via network storage. It is currently unclear how feasible this is and whether some form of local scratch or temporary storage will be necessary. In this context, the boards that provide eMMC storage offer a benefit here.

#### Casings and mountings

We need to decide how to mount our compute nodes and how the Mini-HPC cluster might be moved around if we are aiming for something that is flexible and portable. A key aim is to ensure that the cluster can be used as a teaching resource and therefore making it as easy as possible to transport is important. Some of the following options have been considered:

 - **Custom casing:** One option would be to design and build our own custom casing. This provides the ultimately flexibility and there are also many existing open hardware designs available for mounting SBCs for mini clusters - many of these consist of parts that can be 3D printed.
 - **19-inch rack mounting:** - This option builds on the standard 19-inch rack structure used for mounting computing hardware in data centres, as well as for mounting specialist hardware in a number of other environments including video and audio studios and research labs.

An initial aim was to have something that was similar to a wheeled suitcase making it practical to transport easily. Investigations highlighted a number of wheeled equipment boxes, some also including 19-inch rack-mounting capability. These are being investigated as one possible option.

Building on the interest of rack mounting, there are a number of different approaches for mounting single board computers in a rack-based environment. The RaspberryPi has the best developed set of products in this context but there are several designs for simple, 3D printable brackets that can be used to attach a range of different SBCs in various layouts within a 19-inch rack. The most common approaches are having boards mounted side-by-side, via a 1U-height mounting bracket (1U being the smallest unit of height in a 19-inch rack - standard computer servers are generally built to a 1U or 2U height specification depending on features and expandability. A 1U SBC mounting bracket can generally support up to 4, 5 or even 6 SBCs side-by-side. An alternative approach is to turn the SBCs on their side, requiring greater height, but then allowing far more units to be placed side-by-side. This results in some 2U SBC mounting brackets being able to accommodate as many as 12 SBCs. This of course dependends on the model and associated dimensions of the devices being used.

One particular aim of the Mini-HPC cluster is to be able to have some sort of very small display associated with each node so that it's possible to show key node statistics such as temperature and CPU load.

#### Power

Options for power ultimately come down to two possibilities:

- **USB power:** Most recent SBCs take power via a USB-C or similar small power port. An external PSU is generally required to power the devices since they require more power than a regular USB port can offer. Modern SBCs can often use a maximum of 25-30W so where an official PSU is provided by the board maker, this will generally be 5V at either 4A, 5A or possibly more. Note that not all boards use a 5V power supply so you must check the board specifications if you are not using a PSU designed specficially for the board you are using.
- **Ethernet power:** An alternative for powering some SBCs is to use "Power over Ethernet" (PoE). This generally requires the use of an add-on board that can convert the power sent over the Ethernet connection from a PoE-supporting switch to a voltage that can be used by the SBC. The standard PoE specification which can provide a maximum of around 15W is likely to be insufficient for modern high-power SBCs but PoE+ which can provide up to approximately 30W of power is likely to be suitable for some modern SBCs including the latest Raspberry Pis.

Powering a single board computer cluster therefore comes down to either using one wall-socket PSU per node, providing a custom power setup based on a larger power supply (e.g. an ATX or SFX computer PSU) and cabling to distribute power to the individual SBCs, or using Power-over-Ethernet.

Using lots of wall-socket PSUs is likely to be inefficient in terms of both space and power, even though modern PSUs can be very power efficient. SFX power supplies are used for small form-factor computers - they tend to be the most space efficient option in terms of a high-power computer PSU. SFX PSUs are now available with power ratings of up to around 1300W. Higher power PSUs can be obtained in the large ATX format. Using a computer PSU is a great option but it will require extensive custom cabling to distribute the power to all the SBCs. Power over Ethernet is likely to be the cleanest solution in terms of cabling. It makes the cluster easier to manage and should reduce the number of areas for failures. Nonetheless, PoE+ switches can be expensive, espcially where a high "power budget" is required. Consider, a cluster with 32 nodes, each based on an SBC that can draw up to 30W. This already requires a power budget of at least 960W. PoE+-capable switches that can provide this sort of power tend to be large, enterprise-grade switches that are costly. To use PoE, some form of decide is also likely ot be required to be added to the SBCs to handle the incoming power.
