##########################GPU############

WHAT IT IS:The GPU is a specialized electronic circuit designed to rapidly manipulate and alter memory to accelerate the creation of images in a frame buffer intended for output to a display device.

WHAT IT DOES:
Function: It renders 2D and 3D graphics, processes video encoding/decoding, and handles parallel computing tasks like AI processing or 3D modeling.
What stops working: Monitor displays will go blank (unless the CPU has integrated graphics), games will refuse to launch, and video editing or rendering software will slow down significantly.

WHAT HAPPENS IF IT FAILS:
Symptoms: Screen visual artifacts (lines, weird shapes, flashing blocks), screen flickering, video freezing while audio continues, or the PC crashing specifically when launching a 3D game.
Errors: Motherboard VGA debug LED stays lit, "Display driver stopped responding and has recovered" Windows notifications, or a 1-long, 2-short motherboard beep code.
Boot status: The PC will usually boot fully into the operating system in the background, but you will see a completely blank screen or your monitor will display a "No Signal" message.

WHAT UPGRADES ARE POSSIBLE:
Upgradable: Yes, provided it uses a standard PCIe slot on the motherboard.
Limits: The physical length/thickness clearance inside the computer case, and the maximum power delivery capacity of your existing power supply.
Compatibility: Check for an available PCIe x16 slot, the required power connectors (e.g., 8-pin or 12V-2x6 cables), and that your power supply has enough total wattage headroom.
Improvements: Higher frame rates in video games, support for higher monitor resolutions (like 4K), faster video rendering times, and access to modern features like hardware ray tracing.

HOW DO I TROUBLESHOOT IT:
Step 1: Verify the display cable is plugged directly into the horizontal ports on the GPU itself, and not into the vertical ports on the motherboard.
Step 2: Reseat the card firmly into its PCIe slot and ensure all external PCIe power cables are clicked tightly into place.Tools needed: Phillips screwdriver, DDU (Display Driver Uninstaller) software utility, a spare known-working monitor cable, and a secondary test PC.
Confirmation: Confirm it is dead if the card displays visual distortion (artifacts) in the motherboard BIOS screen before any drivers load, or if it produces no display output on a completely separate, known-working computer.

INTERVIEW QUESTIONS:
Q: What is the difference between integrated graphics and a dedicated GPU?
A: Integrated graphics are built directly into the CPU chip and share the computer's system RAM, whereas a dedicated GPU sits on its own separate expansion card and has its own ultra-fast Video RAM (VRAM).
Q: A user states that their screen displays strange flickering green dots and horizontal lines only when playing games. What is likely wrong?
A: This is called "artifacting," which typically points to failing VRAM or an overheating GPU core that is reaching the end of its operational life.
Q: Why is it recommended to use Display Driver Uninstaller (DDU) when upgrading from an AMD graphics card to an NVIDIA graphics card?
A: Leftover driver files and registry entries from the old card can conflict with the new card's software, leading to system instability, crashes, or lower-than-expected performance.

#########################COOLING SYSTEMS(Air & Liquid)####################################

WHAT IT IS:A cooling system is a combination of hardware components—such as heatsinks, fans, thermal paste, pumps, and radiators—designed to dissipate thermal energy away from heat-generating components like the CPU and GPU.

WHAT IT DOES:
Function: It pulls extreme heat away from computer chips and expels it outside the case to maintain safe internal operating temperatures.
What stops working: The computer will thermal throttle (slow down dramatically) or abruptly shut down within seconds to minutes of heavy use to protect itself from physical destruction.

WHAT HAPPENS IF IT FAILS:
Symptoms: Fans spinning violently at max speed with extreme noise, a burning smell, immediate system lag after booting, or a computer that shuts off completely without warning after running a heavy program for a short period.
Errors: "CPU Fan Error" or "CPU Over Temperature Error" displayed on the motherboard splash screen during startup.
Boot status: Partially; the PC will boot into the BIOS or even Windows initially, but it will abruptly shut down or freeze within a few minutes as heat builds up to dangerous levels.

WHAT UPGRADES ARE POSSIBLE:
Upgradable: Yes, you can replace a stock CPU cooler with a high-end air tower or an All-In-One (AIO) liquid cooler.
Limits: The physical height clearance inside the case side panel, RAM clearance underneath the cooler, and available fan mounting points on the case chassis.
Compatibility: Check the specific CPU socket mounting bracket layout (e.g., AM5 vs LGA 1700), case radiator size support (120mm, 240mm, 360mm), and available motherboard fan/pump headers.
Improvements: Drastically lower operating temperatures, quieter system operation under load, and increased headroom to safely overclock components.

HOW DO I TROUBLESHOOT IT:
Step 1: Visually check if all internal fans are spinning when the PC is powered on, and listen carefully for a faint humming/gurgling sound from a liquid cooling pump.
Step 2: Open a hardware monitoring utility (like HWMonitor) to check if CPU temperatures are immediately spiking past 90°C–100°C while doing simple tasks.
Tools needed: Thermal paste, isopropyl alcohol (90%+), microfiber cloth, and compressed air canister.
Confirmation: Confirm a component is failing if a liquid pump motor reports 0 RPM in the BIOS, or if the CPU instantly overheats even after you have wiped off the old thermal paste, applied a fresh layer, and verified the cooler is mounted with proper pressure.

INTERVIEW QUESTIONS:
Q: What is the primary function of thermal paste between a CPU and its heatsink?
A: It fills in the microscopic air gaps and imperfections between the metal surfaces of the CPU lid and the heatsink base, maximizing heat transfer efficiency.
Q: What are the symptoms of a failing All-In-One (AIO) liquid cooling pump compared to a failing fan?
A: A failing pump will cause immediate, extreme CPU overheating within seconds even if the radiator fans are spinning, often accompanied by a rattling or grinding sound from the CPU block area.
Q: How do positive and negative air pressure configurations differ inside a computer case?
A: Positive pressure means there are more intake fans than exhaust fans, which pushes air out of case gaps and helps keep dust out; negative pressure means more exhaust fans, which pulls air (and dust) in through random un-filtered gaps.

##################INPUT/OUTPUT PORTS & CABLES#################################

WHAT IT IS:I/O ports are physical connection interfaces located on the exterior of a computer that allow external peripheral devices—such as monitors, keyboards, storage drives, and networks—to exchange data with the internal motherboard components.

WHAT IT DOES:
Function: They serve as the standardized entry and exit points for data packets, video signals, audio feeds, and electrical power between the PC and the outside world.
What stops working: Specific external devices (like a mouse, printer, or external drive) will lose connection, stop transferring data, or fail to receive power.

WHAT HAPPENS IF IT FAILS:
Symptoms: External devices randomly disconnecting when the cable is touched, a specific port failing to register any plugged-in hardware, or a single port sparking or causing the entire PC to shut down instantly due to a short circuit.
Errors: Windows pop-up notifications saying "USB Device Not Recognized" or "Power Surge on the USB Port."
Boot status: Fully; a failing peripheral port will rarely stop a computer from booting unless the physical pins inside the port are bent and touching each other, creating an electrical short that triggers the power supply's safety cut-off.

WHAT UPGRADES ARE POSSIBLE:
Upgradable: Yes, by adding PCIe expansion cards or external hubs.Limits: Available open PCIe slots on the motherboard, and the maximum bandwidth limits of your system's motherboard chipset.
Compatibility: Check for an empty PCIe slot (usually x1 or x4) for expansion cards, or ensure you are plugging external hubs into the fastest available USB type (like matching a USB 3.2 hub to a USB 3.2 port).
Improvements: Adding modern ultra-fast Thunderbolt or USB4 ports to an older machine, increasing the total number of USB connections, or adding high-speed 10Gbps Ethernet capabilities.

HOW DO I TROUBLESHOOT IT:
Step 1: Plug the external device into a completely different port on the same PC (preferably switching from the front case ports to the rear motherboard ports) to isolate whether the port or the device is broken.
Step 2: Inspect the inside of the problem port with a flashlight to look for lint, dirt, dust, or bent/broken gold pins.
Tools needed: Flashlight, non-conductive wooden/plastic toothpick, can of compressed air, and a known-working USB flash drive with an integrated activity LED.
Confirmation: Confirm a port is physically dead if multiple known-good devices fail to receive power or data from it, while device manager shows all controllers are healthy and no software or driver changes resolve the issue.

INTERVIEW QUESTIONS:
Q: A user complains that the USB ports on the front of their desktop case do not work, but the USB ports on the very back of the PC work perfectly. What should you check first?
A: Check inside the PC case to ensure that the front panel USB header cable is securely connected to the correct pins on the motherboard.
Q: What is the main structural and capability advantage of a USB Type-C connector over a USB Type-A connector?
A: Type-C is completely reversible so it cannot be plugged in upside down, and it supports much higher data transfer speeds, video output signals (Alt Mode), and high-wattage Power Delivery (PD).
Q: What is the maximum data transfer rate of a standard USB 3.0 port, and how can you typically identify one visually?
A: USB 3.0 has a maximum speed of 5 Gbps and is traditionally colored bright blue inside the connector to distinguish it from black USB 2.0 ports.