# Network Scanner

A Python command-line tool for learning network discovery and basic host/port scanning with Scapy.

It supports ICMP host checks, TCP port scans, and ARP discovery on a local network. Use it only on systems and networks you own or have explicit permission to test.

## Features

- **ICMP** — check whether a host responds to an echo request.
- **TCP** — check selected ports and report open, closed, or filtered results.
- **ARP** — discover responding devices on a local network.
- **Target validation** — accept an IP address or CIDR network.
- **Timeout control** — configure how long each packet operation waits.

## Requirements

- Python 3
- Dependencies from `requirements.txt`
- Administrator/root privileges may be needed for raw packet operations, depending on your operating system.

## Setup

Clone the repository and enter its directory:

```bash
git clone https://github.com/mohammadowais16/Network-Scanner.git
cd Network-Scanner
python -m venv .venv
```

Activate the environment.

**Windows (PowerShell):**

```powershell
.venv\Scripts\Activate.ps1
```

**macOS/Linux:**

```bash
source .venv/bin/activate
```

Install the dependencies:

```bash
python -m pip install -r requirements.txt
```

## Usage

Run commands from the repository root:

```bash
python src/main.py <target> [options]
```

Check whether one host responds to ICMP:

```bash
python src/main.py 192.168.1.1 --type icmp
```

Scan selected TCP ports:

```bash
python src/main.py 192.168.1.1 --type tcp --ports 22,80,443
```

Scan a TCP port range:

```bash
python src/main.py 192.168.1.1 --type tcp --ports 1-1000
```

Discover devices on a local subnet with ARP:

```bash
python src/main.py 192.168.1.0/24 --type arp
```

Replace example addresses with targets you are authorized to scan.

## Command-line options

| Option | Description |
| --- | --- |
| `target` | Target IP address or network in CIDR notation |
| `-t, --type` | Scan type: `all`, `icmp`, `tcp`, or `arp` (default: `all`) |
| `-p, --ports` | TCP ports, e.g. `80,443` or a range such as `1-1000` |
| `-T, --timeout` | Timeout in seconds (default: `2`) |

For a TCP scan, pass `--ports`; no TCP ports are scanned when this option is omitted. The `all` scan type runs ICMP, TCP, and ARP checks, so specifying ports is recommended. ARP discovery is intended for a local network and defaults to a `/24` subnet if you pass a single IP address.

View the built-in help:

```bash
python src/main.py --help
```

## Project files

```text
Network-Scanner/
├── src/
│   ├── main.py       # CLI arguments and output
│   └── scanner.py    # ICMP, TCP, and ARP scan logic
├── requirements.txt
├── .gitignore
└── README.md
```

## Limitations

- Results depend on firewall rules, network configuration, and packet permissions.
- A timeout does not necessarily mean a host or port is offline.
- This project is intended for learning and authorized testing, not as a substitute for a maintained network security product.
