##################Switches, Routers, Access Points#####################################

COMPONENT: Network Switch

Date studied: 31 July 2026

WHAT IT IS: A switch is a Layer 2 network device that acts as a central hub to intelligently connect multiple wired devices together within the same Local Area Network (LAN).

WHAT IT DOES:
It learns physical MAC addresses to securely forward data packets exclusively to the destination device.
It creates dedicated collision domains for each individual port to eliminate data collisions.
It can provide electrical power to connected devices like IP phones using Power over Ethernet (PoE).
Without it: Wired computers in the same office or room cannot talk to each other or share resources.
Without it: A single router port could not scale up to support dozens of wired desktop connections.

WHAT HAPPENS IF IT FAILS:
Every single device wired into that specific switch instantly loses local and internet connectivity.
System link lights next to the physical cable ports turn completely off or turn solid amber.
Network traffic drastically slows to a crawl if a loop occurs due to a failure in Spanning Tree Protocol (STP).
Beep codes: None; enterprise units flash a blinking orange "STAT" or "SYST" fault LED on the faceplate.
Boot status: All connected PCs boot perfectly fine to Windows but show a "Network cable unplugged" or "No Internet" tray icon.

WHAT UPGRADES ARE POSSIBLE:
Upgradability: Physical hardware cannot be upgraded; you must completely replace the unit to get more ports.
Limits: Limited by the fixed internal backplane switching bandwidth and total Power over Ethernet (PoE) wattage budget.Compatibility: Verify if your network layout requires a Plug-and-Play (Unmanaged) or a configurable (Managed) model.Improvements: Upgrading moves your network speeds up from standard Gigabit (1 Gbps) to multi-gigabit speeds (2.5, 5, or 10 Gbps).

HOW DO I TROUBLESHOOT IT:
Step 1: Verify the unit has a solid green power light and check if the link lights flash when a cable is plugged in.
Step 2: Isolate the problem by plugging a known-good computer directly into a different port using a fresh patch cable.
Tools needed: A physical network cable tester, a laptop for console cable connection, and a spare Ethernet cable.
Dead vs. Misconfigured: Power cycle the switch; if a managed switch boots but blocks traffic, clear its configuration via the console port.

INTERVIEW QUESTIONS:
Q: What is the fundamental operational difference between an older network hub and a modern network switch?
A: A hub is a dumb device that broadcasts all incoming data packets out to every single port, whereas a switch tracks MAC addresses to forward data packets strictly to the intended recipient port.
Q: What features do you gain by choosing a Managed Switch over a cheaper Unmanaged Switch?
A: Managed switches allow you to configure Virtual LANs (VLANs), monitor traffic metrics, prioritize voice traffic via QoS, and protect against loops using Spanning Tree Protocol.
Q: A user's desktop computer suddenly loses its network connection. You notice the switch port link light is completely dead. What are your immediate troubleshooting steps?
A: I would first swap out the patch cable with a known-good one, then try moving the connection to an adjacent empty port on the switch, and finally verify that the workstation’s network card is enabled.


#################Network Router##############################

COMPONENT: Network Router

Date studied: 31 July 2026

WHAT IT IS: A router is a Layer 3 network device that acts as a gateway to connect completely separate networks together, intelligently forwarding data packets between them using IP addresses.

WHAT IT DOES: 
It routes data packets safely between your private local network (LAN) and the public external internet (WAN).
It hides your internal devices by translating private IP addresses into a single public IP address using NAT.
It runs an internal firewall to block unauthorized inbound connections from accessing your network.
Without it: Your internal office devices could talk to each other but could never access the internet or outside web pages.Without it: Data packets would have no path map to leave your local building subnet.

WHAT HAPPENS IF IT FAILS:
All local network devices completely lose connection to the internet, cloud apps, and external email.
Local internal devices can still print to local network printers and transfer files locally to each other.
Remote workers can no longer log in via VPN, and external customers cannot access hosted web servers.
Beep codes: None; front panel internet/WAN indicator lights will turn off or change to a solid warning red.
Boot status: Computers boot normally but display the browser error page "DNS_PROBE_FINISHED_NO_INTERNET".

WHAT UPGRADES ARE POSSIBLE:
Upgradability: Home models cannot be physical upgraded; enterprise models allow you to slide in extra interface cards.
Limits: Limited by its internal CPU processing limits, firewall packet-inspection speeds, and total routing throughput capacity.
Compatibility: You must match the router's physical WAN interface ports with the delivery method of your ISP provider (Ethernet, Fiber, Coax).
Improvements: Upgrading provides faster Wi-Fi standards (like Wi-Fi 7), higher VPN handling capacity, and faster multi-gigabit internet support.

HOW DO I TROUBLESHOOT IT:
Step 1: Ping the router's internal IP address (Default Gateway) from a local computer to verify local connectivity.
Step 2: Log into the router's web admin page to check if it has successfully pulled a valid public IP address from the ISP.Tools needed: Command Prompt (ping, tracert), a console rollover cable, and a spare modem/router unit for testing.
Dead vs. Misconfigured: If you can access the admin web page but the internet is dead, it is a misconfiguration or an ISP outage.

INTERVIEW QUESTIONS:
Q: What is the primary purpose of Network Address Translation (NAT) inside a network router?
A: NAT allows an entire local network of private devices to share a single public IP address assigned by the ISP, conserving IPv4 addresses and adding a layer of security.
Q: If a computer can successfully ping other computers in the office but cannot access external websites, what device configuration should you check first?
A: I would check the client's Default Gateway configuration to ensure it matches the exact local IP address of the network router.
Q: What routing tool or command would you use to find out exactly where data packets are getting dropped on the internet?
A: I would use the tracert (traceroute) command, which displays every single hop or router a packet passes through on its path to the destination.


##################################Wireless Access Point(WAP)###############################

COMPONENT: Wireless Access Point (WAP)

Date studied: 31 July 2026

WHAT IT IS: A WAP is a network hardware device that connects directly to a wired switch or router via an Ethernet cable to project a wireless Wi-Fi radio signal across an area.

WHAT IT DOES:
It acts as a bridge that translates wireless radio frequency traffic into wired Ethernet network frames.
It broadcasts the Service Set Identifier (SSID) so wireless devices can find and authenticate to the network.
It handles wireless encryption standards (like WPA3) to safeguard over-the-air data streams.
Without it: Laptops, tablets, and smartphones could not connect to the local business network without physical dongles.Without it: You would have to deploy hundreds of physical network drops to support mobile workers.

WHAT HAPPENS IF IT FAILS:
Wi-Fi signals instantly drop, causing wireless clients to disconnect or search endlessly for an active connection.
The specific network name (SSID) completely vanishes from the list of available Wi-Fi networks in the area.
Users sitting close to the broken unit roam onto a far-away access point, causing a massive drop in signal bars.
Beep codes: None; a status light on the dome cover changes from solid blue/white to blinking amber or turns off completely.Boot status: Mobile devices boot normally but display "No Wi-Fi networks found" or get stuck on cellular data.

WHAT UPGRADES ARE POSSIBLE:
Upgradability: Hardware cannot be physically upgraded; you must mount a brand-new access point model to upgrade.
Limits: Limited by the maximum wireless standards it supports (Wi-Fi 5 vs. Wi-Fi 6E/7) and the density of users it can handle.Compatibility: Must match your wireless network security standard infrastructure and the available PoE power limits of your switch.
Improvements: Upgrading introduces newer, clean radio bands (6 GHz) that eliminate congestion and increase data speeds.

HOW DO I TROUBLESHOOT IT:
Step 1: Verify the access point is getting PoE power by checking if its physical status light is turned on.
Step 2: Use a Wi-Fi analyzer app to see if the device is broadcasting its radio frequencies on clean, un-congested channels.Tools needed: A software Wi-Fi analyzer, a PoE injector tool (for power testing), and a tall ladder to reach the unit.
Dead vs. Misconfigured: If the unit is powered on but not broadcasting, check if its switch port was accidentally assigned to the wrong VLAN.

INTERVIEW QUESTIONS:
Q: Why do enterprise Wireless Access Points rarely ship with an AC power adapter wall plug?
A: They are designed to be powered over the network cable using Power over Ethernet (PoE) from a central PoE switch, eliminating the need for electrical outlets on ceilings.
Q: What step would you take if users complain that the office Wi-Fi is incredibly slow in one specific corner of a room?
A: I would use a Wi-Fi analyzer to map the signal strength (RSSI), inspect for physical obstructions like brick or metal, and check for channel interference from neighboring offices.
Q: What is the difference between a consumer wireless router and an enterprise Wireless Access Point?
A: A consumer router combines routing, switching, and wireless into one box for a small space, while an enterprise WAP does nothing but broadcast Wi-Fi, working alongside a separate dedicated router and switch to cover massive buildings.