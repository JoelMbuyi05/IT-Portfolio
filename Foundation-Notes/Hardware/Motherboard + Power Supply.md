############################MOTHERBOARD#################################

WHAT IT IS:The motherboard is the main printed circuit board (PCB) that serves as the central backbone of a computer, physically connecting and allowing communication between all hardware components.

WHAT IT DOES:
Function: It routes power and data traffic between the CPU, RAM, storage, GPU, and all other peripherals.
What stops working: The entire computer; without the motherboard, individual components have no way to power on or interact with each other.

WHAT HAPPENS IF IT FAILS:
Symptoms: Frequent random crashes, failure to POST (Power-On Self-Test), burning smells, or a PC that turns on for one second and immediately shuts down.
Errors: Continuous motherboard beep codes, debug LED lights illuminated on the board (CPU/DRAM/VGA/BOOT), or specific two-digit POST codes on premium models.
Boot status: The PC will not boot at all; it will either remain completely dead or spin the fans endlessly with no display or BIOS access.

WHAT UPGRADES ARE POSSIBLE:
Upgradable: Yes, but it requires rebuilding the entire PC and usually replacing the CPU as well.
Limits: PC case size limits the form factor, and the specific chipset limits what generation of hardware is supported.Compatibility: You must check the CPU socket type (e.g., LGA 1700, AM5), RAM generation (DDR4 vs DDR5), case form factor (ATX, Micro-ATX, Mini-ITX), and power connections.
Improvements: Support for faster CPUs, more PCIe expansion slots, faster USB/Thunderbolt ports, better power delivery (VRMs) for overclocking, and upgraded built-in Wi-Fi.

HOW DO I TROUBLESHOOT IT:
Step 1: Disconnect all non-essential hardware (GPU, storage, extra RAM) to test the board in a minimal "bench test" configuration outside the case.
Step 2: Clear the CMOS by removing the coin-cell battery or shorting the reset jumpers to wipe corrupt BIOS settings.
Tools needed: Phillips screwdriver, anti-static wrist strap, motherboard speaker (for beep codes), and a digital POST card.Confirmation: Confirm it is dead if it refuses to POST even with a known-good CPU, RAM stick, and power supply tested outside of the computer case (ruling out a short circuit).

INTERVIEW QUESTIONS:
Q: What is the purpose of the CMOS battery on a motherboard?
A: It keeps the volatile CMOS memory powered so the motherboard retains its customized BIOS settings, time, and date when the PC is unplugged.
Q: A customer wants to install a modern PCIe 4.0 graphics card into an older PCIe 3.0 motherboard slot. Will this work?
A: Yes, PCIe slots are backward and forward compatible, but the graphics card will be bottlenecked to the maximum speeds of the older PCIe 3.0 standard.
Q: What is a VRM, and why is its quality important on a motherboard?
A: A Voltage Regulator Module converts high-voltage power from the PSU into clean, low-voltage power for the CPU; high-quality VRMs prevent overheating and system instability under heavy loads.


################Power Supply Unit############################

WHAT IT IS:
The Power Supply Unit is the hardware component that converts alternating current (AC) from a wall outlet into regulated, low-voltage direct current (DC) power required by internal computer parts.

WHAT IT DOES:
Function: It distributes safe, stepped-down electrical power (+3.3V, +5V, +12V) via dedicated cables to the motherboard, CPU, graphics card, and storage.What stops working: The entire computer will lose power or fail to energize.

WHAT HAPPENS IF IT FAILS:
Symptoms: Spontaneous shutdowns under heavy loads, failing to turn on, a loud pop followed by smoke, or random resets.
Errors: Rarely generates soft errors; instead, you get no display, motherboard "Power Supply Surge" alerts on reboot, or a complete lack of system response.
Boot status: Usually not at all; if it fails partially, the system might power on fans but fail to deliver enough stable current to boot the OS.

WHAT UPGRADES ARE POSSIBLE:
Upgradable: Yes, easily replaced as long as it physically fits the case standard.
Limits: Physical dimensions of the case shroud, and the maximum power delivery required by power-hungry components like high-end GPUs.
Compatibility: Check the case form factor (ATX, SFX), necessary cable connectors (like the 12V-2x6 or 12VHPWR for modern GPUs), and total wattage headroom.
Improvements: Higher wattage capacity for beefier hardware, increased efficiency ratings (80 Plus Bronze vs Gold/Titanium), and modular cables to reduce interior clutter.

HOW DO I TROUBLESHOOT IT:
Step 1: Verify the rear toggle switch is set to "I" (On), the wall outlet works, and the main 24-pin cable is completely seated.
Step 2: Perform the "paperclip test" (bridging the green PS-ON pin with a black ground pin on the 24-pin connector) to see if the PSU fan spins up on its own.
Tools needed: PSU tester, digital multimeter, and a paperclip or jumper tool.
Confirmation: Confirm it is dead if a dedicated PSU tester or multimeter shows voltages dropping below or spiking above the standard +/- 5% tolerance under load, or if the unit fails to activate during a paperclip test.

INTERVIEW QUESTIONS:
Q: What is the difference between a modular and a non-modular power supply?
A: A non-modular PSU has all cables permanently attached, while a modular PSU allows you to plug in only the specific cables you need, drastically improving airflow and cable management inside the case.
Q: What does an "80 Plus Gold" certification mean on a power supply?
A: It is an efficiency rating certifying that the power supply will convert at least 80% (specifically around 87% to 90% depending on the load) of the AC wall power into usable DC power, wasting less energy as heat.
Q: If a PC powers on for a few seconds, the fans spin up, and then it suddenly shuts off completely when launching a game, what do you suspect?
A: The PSU is likely insufficient for the hardware or failing, causing its Over-Current Protection (OCP) or Over-Power Protection (OPP) to trigger when the graphics card demands a heavy power draw.