COMPONENT: Storage(HDD,SSD,NVMe)
Date studied: 7/26/26

WHAT IT IS:
Computer storage is the hardware component used to permanently retain digital data, applications, and the operating system even when the machine is powered off.

WHAT IT DOES:
[What function does it serve in the computer?]
It holds your files, software, and system files so the processor can load them into memory when needed.
[What would stop working without it?]
The computer cannot save files, install software, or launch applications.

WHAT HAPPENS IF IT FAILS:
[Symptoms the user would experience]
Extreme system slowdowns, freezing, blue screens (BSOD), corrupted files, and clicking noises (HDDs only).
[Error messages or beep codes associated]
"Operating System Not Found", "Boot Device Not Found", or "S.M.A.R.T. Status Bad".
[Does the PC still boot? Partially or not at all?]
The PC will not boot into the OS at all, though it will still power on and display the BIOS/UEFI screen.

WHAT UPGRADES ARE POSSIBLE:
[Can it be upgraded? What limits the upgrade?]
Yes, you can replace or add drives if your motherboard has open slots.
Motherboard slot availability, physical space, and power supply connections.
[Compatibility requirements — what do you need to check first?]
Check for available SATA ports, M.2 slots (NVMe vs SATA protocol), and PCIe generation support.
[Speed/capacity improvements available]
Drastically faster boot times, quicker game loading, and increased file capacity (e.g., upgrading from a 500GB SATA SSD to a 2TB NVMe SSD).

HOW DO I TROUBLESHOOT IT:
Step 1: Verify physical connections by reseating the SATA/NVMe data cables and power cables.
Step 2: Check if the drive is recognized inside the motherboard BIOS/UEFI menu.
Tools needed: Phillips screwdriver, external drive enclosure, and a bootable USB tool (like Linux Live or Windows Installer).Confirmation: A misconfigured drive usually reappears after a BIOS reset or driver update; a dead drive fails to spin up, drops offline randomly, or refuses to show up on a known-working secondary PC.

INTERVIEW QUESTIONS:
Q: What is the practical difference between a SATA SSD and an NVMe SSD?
A: SATA SSDs use older cables and top out around 550 MB/s, while NVMe SSDs plug straight into the motherboard and can reach speeds over 7,000 MB/s by using PCIe lanes.
Q: A user reports their mechanical hard drive is making a loud, rhythmic clicking sound. What is your immediate course of action?
A: Back up critical data immediately if the drive is still readable, then replace it, because clicking indicates a mechanical failure of the read/write arm (the "click of death").
Q: How does RAID 1 differ from RAID 0 regarding storage capacity and fault tolerance?
A: RAID 0 stripes data across drives for pure speed but offers zero fault tolerance, whereas RAID 1 mirrors data across drives for total redundancy at the cost of losing half your total raw capacity.