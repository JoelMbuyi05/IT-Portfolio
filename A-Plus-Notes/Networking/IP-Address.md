COMPONENT: IP Address

Date studied: 30/07/2026

WHAT IT IS: An IP (Internet Protocol) address is a unique numerical label assigned to every device on a network that identifies its location and allows it to communicate with other devices.

WHAT IT DOES:
[What function does it serve in the computer?]
It routes data packets across networks to ensure information reaches the correct destination device.

[What would stop working without it?]
All internet access, local file sharing, network printing, and online gaming will immediately cease.

WHAT HAPPENS IF IT FAILS:
[Symptoms the user would experience]
Web pages will not load, network icons will show a yellow warning or red cross, and local network folders become unreachable.

[Error messages or beep codes associated]
You will see "Destination Host Unreachable", "No Internet Access", or "DNS Probe Finished No Internet".

[Does the PC still boot? Partially or not at all?]
The PC will boot completely into the operating system normally because IP configuration does not affect hardware startup.

WHAT UPGRADES ARE POSSIBLE:
[Can it be upgraded? What limits the upgrade?]
You cannot upgrade an IP address itself, but you can upgrade the hardware handling it, like your network interface card (NIC) or router.

[Compatibility requirements — what do you need to check first?]
You must check if your hardware supports IPv6 protocols and ensure your router handles your desired network speed.

[Speed/capacity improvements available]
Moving from IPv4 to IPv6 eliminates address shortages, while upgrading network cards boosts data transfer speeds from 1 Gbps to 2.5 Gbps or 10 Gbps.

HOW DO I TROUBLESHOOT IT:
[Step 1 — first thing to check]
Run the ping 127.0.0.1 command in the command prompt to test if your computer's internal network stack is functioning.

[Step 2 — second thing to check]
Check if your device has a valid IP by running ipconfig (Windows) or ifconfig (Mac/Linux) to see if it starts with an automatic fallback address like 169.254.x.x.

[Tools needed — multimeter, POST card, spare parts]
Command Prompt, network cable tester, spare Ethernet cable, or a known-working USB-to-Ethernet adapter.

[How do you confirm it's dead vs just misconfigured?]
If you can ping your local router gateway but not website addresses, it is misconfigured (DNS issue); if the network card is not detected at all in Device Manager, the hardware is dead.

INTERVIEW QUESTIONS:
Q: What is the difference between a static and a dynamic IP address?
A: A static IP address is manually assigned and never changes, which is great for servers. A dynamic IP address is automatically assigned by a DHCP server and can change periodically, which is ideal for standard devices.
Q: What does an IP address starting with 169.254 mean?
A: It means your device could not reach the DHCP server to get an IP address, so the operating system automatically assigned itself a temporary Automatic Private IP Address (APIPA).
Q: What is the purpose of a subnet mask alongside an IP address?
A: A subnet mask splits the IP address into two parts to show which part identifies the main network and which part identifies the specific device on that network.