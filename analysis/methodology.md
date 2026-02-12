## Objective
Check basic reachability, round-trip time, and network path to three hosts using Ping and Traceroute (Windows tracert). 

## Tools
- Windows 11
- Command Prompt
- `ping`
- `tracert`

## Test Setup
- Ran tests from a Windows 11 PC in Command Prompt.
- Ping sent 20 probes per host (`-n 20`).
- Ping payload sizes:
  - 1 byte (`-l 1`)
  - 9000 bytes (`-l 9000`)
- Traceroute used Windows defaults (up to 30 hops) and saved output to text files.

## Commands
```bash
# Ping: 1-byte payload, 20 probes
ping www.ufl.edu -n 20 -l 1
ping www.uq.edu.au -n 20 -l 1

# Ping: 9000-byte payload, 20 probes
ping www.ufl.edu -n 20 -l 9000

# Traceroute (Windows tracert): save results to files
tracert www.ufl.edu > uflTrace.txt
tracert www.uq.edu.au > uqTrace.txt
tracert www.uwi.edu > uwiTrace.txt
