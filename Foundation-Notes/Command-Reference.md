# [Clear Windows Print Spooler Queue]

net stop spooler : Stops the Windows Print Spooler service
del /Q /F /S "%systemroot%\System32\spool\PRINTERS\*.*" : Deletes the queued print-job files
/Q: Quiet mode (no confirmation)
/F: Force deletion
/S: Inlcudes files in subdirectories
net start spooler : Starts the Print Spooler service again

## Purpose: 
Clears stuck/pending print jobs by stopping the Print Spooler, deleting the printer queue files, and starting the Spooler again.

## When to use: 
When a printer is stuck on "Printing," "Deleting," "Pending," or jobs won't clear from the print queue.

Run as an Admin

## Quick Reference: Stop Spooler → Clear Queue → Start Spooler


# [Wi-Fi Troubleshooting]

1. Wi-Fi ON + correct network
2. Forget → reconnect
3. Troubleshooter
4. Delete Wi-Fi profile:
   netsh wlan delete profile name="WiFi_Name"
5. Renew IP:
   ipconfig /release
   ipconfig /renew
6. Flush DNS:
   ipconfig /flushdns
7. Reset TCP/IP:
   netsh int ip reset
   → Restart
8. Check/update Wi-Fi driver
9. Test other devices → isolate PC vs network


# [Network Review & Troubleshooting]

[ BASIC CONNECTIVITY ]

ping 127.0.0.1
→ Tests local TCP/IP stack.
→ Fails = TCP/IP / adapter issue.

ipconfig /all
→ View IP, subnet, gateway, DNS, DHCP.

ping <Default-Gateway>
→ Tests local network/router.
→ Fails = adapter / cable / switch / router.

ping 8.8.8.8
→ Tests Internet connectivity by IP.
→ Fails = router / ISP / Internet issue.

ping google.com
→ Tests DNS + Internet.
→ 8.8.8.8 works but this fails = DNS issue.

nslookup google.com
→ Tests DNS resolution.
→ Shows DNS server + returned IP.

tracert google.com
→ Traces route/hops to destination.
→ Shows where connectivity may stop.

netstat -an
→ Shows active connections + listening ports.
→ Check for HTTPS (443) connections.
