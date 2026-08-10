# Remote Desktop Tools

## RDP (Remote Desktop Protocol)
Port: 3389
Enable: Settings → System → Remote Desktop → On
Connect: Win+R → mstsc → enter IP
Best for: Corporate devices on same network, servers
Limitation: Needs port 3389 open, same network or VPN

## Quick Assist (Built into Windows)
No port configuration needed
Search "Quick Assist" → Help someone → get code
User enters code on their end → you see their screen
Best for: Quick support sessions, works through most firewalls
Limitation: User must be present, session is temporary

## TeamViewer
Download from teamviewer.com, free for personal use
Both sides need the app running
Connect using ID and password
Best for: Home users, through NAT, no network access needed
Limitation: Free version has time limits for commercial use

## AnyDesk
Similar to TeamViewer, lighter and faster
Increasingly preferred in smaller companies

## Intune Remote Help
Enterprise version of Quick Assist
Managed through Intune admin center
Full audit trail — who connected, when, what they did
Required in compliance-heavy environments

## When to Use Which
User on corporate network → RDP
User at home, quick fix → Quick Assist
User at home, no Quick Assist → TeamViewer or AnyDesk  
Corporate with audit requirements → Intune Remote Help