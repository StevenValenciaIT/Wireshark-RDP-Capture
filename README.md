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

## Key Takeaways
- Network traffic analysis can reveal connection attempts even if payloads are encrypted.
- RDP uses TCP port 3389 by default; monitoring this port is critical for detecting brute force or lateral movement attempts.
- Wireshark’s “Follow TCP Stream” is useful for examining session flow, even when data is encrypted.
- This lab reinforced how endpoint activity translates into observable network events.
