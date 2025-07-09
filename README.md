# Wireshark Traffic Analysis: RDP Login Simulation

## Objective
Capture and analyze Remote Desktop (RDP) traffic using Wireshark in a simulated attack lab environment.

## Environment
- **Attacker**: Kali Linux using `xfreerdp3`
- **Target**: Windows 11 VM (192.168.1.26)
- **Monitoring Tool**: Wireshark

## Simulation
Ran an RDP login attempt from Kali to the Windows machine using the following command:

```bash
xfreerdp3 /u:pentest /p:"wrongpass" /v:192.168.1.26 +auth-only /cert:ignore
```

## Wireshark Capture

Filter using 
```bash
ip.addr == 192.168.1.26 && tcp.port == 3389
```

### Observations
TCP handshake visible (SYN, SYN-ACK, ACK)

Encrypted RDP session follows

Source and destination IPs clearly identified

### Screenshots
Packet Capture

Follow TCP Stream

## Summary
This lab showed how Wireshark reveals network-level RDP activity. Even though payloads are encrypted, connection patterns help detect suspicious login attempts.
