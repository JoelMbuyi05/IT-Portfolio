# Wi-Fi Configuration and Troubleshooting

## Standards to Know (exam)
802.11n  — 2.4GHz + 5GHz, up to 600Mbps
802.11ac — 5GHz, up to 3.5Gbps (Wi-Fi 5)
802.11ax — 2.4GHz + 5GHz, up to 9.6Gbps (Wi-Fi 6)

## Security Standards
WEP  — broken, never use
WPA2 — current standard, AES encryption
WPA3 — newest, required for Wi-Fi 6 devices

## Key Commands
netsh wlan show profiles               → list saved networks
netsh wlan show profile name="X" key=clear → reveal password
netsh wlan delete profile name="X"    → delete saved profile
netsh int ip reset                    → reset TCP/IP stack (nuclear)

## Troubleshooting Flow
1. Verify Wi-Fi enabled → correct SSID selected
2. Forget and reconnect
3. Delete profile → reconnect fresh
4. ipconfig /release + /renew
5. ipconfig /flushdns
6. netsh int ip reset → restart
7. Update Wi-Fi driver
8. Test other devices to isolate

## Defend question: "A user's laptop connects to Wi-Fi but shows 'No Internet' even though other devices on the same network work fine. What's your process?"

## Answer out loud: Since other devices work, the network is fine — the issue is isolated to this laptop. I'd run ipconfig /all — check if it has a valid IP (not 169.254.x.x which means DHCP failed) and a correct DNS server. Then ping 8.8.8.8 — if that works, it's a DNS issue not connectivity. Then ping google.com — if that fails but 8.8.8.8 works, flush DNS and set DNS manually to 8.8.8.8. If both pings fail, try ipconfig /release and /renew. If still nothing, reset TCP/IP with netsh int ip reset and restart.