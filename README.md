# Network Scanner

A Python command-line project for checking host availability, scanning TCP ports, and discovering devices on a local network with ARP.

This is a learning project for networking and security fundamentals. Use it only on systems and networks you own or have explicit permission to test.

## Features

- **ICMP scan** — check whether a target responds to ping.
- **TCP port scan** — check selected ports or a port range.
- **ARP scan** — discover devices on a local network.
- **Flexible targets** — accept an IP address or CIDR network.
- **Configurable timeout** — set how long each scan waits for a response.

## Requirements

- Python 3
- Dependencies listed in `requirements.txt`
- Administrator/root privileges may be required for raw packet operations, depending on your operating system and scan type.

## Setup

Clone this repository:

```bash
git clone https://github.com/mohammadowais16/Network-Scanner.git
cd Network-Scanner
```

Create and activate a virtual environment (recommended):

```bash
python -m venv .venv
```

On Windows:

```powershell
.venv\Scripts\Activate.ps1
```

On macOS/Linux:

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
python -m pip install -r requirements.txt
```

## Usage

Run the scanner from the repository root:

```bash
python src/main.py <target> [options]
```

Examples:

```bash
# Scan a single host using the default scan types
python src/main.py 192.168.1.1

# Run an ICMP scan
python src/main.py 192.168.1.1 --type icmp

# Scan selected TCP ports
python src/main.py 192.168.1.1 --type tcp --ports 80,443,8080

# Scan a port range
python src/main.py 192.168.1.1 --type tcp --ports 1-1000

# Discover devices on a local subnet with ARP
python src/main.py 192.168.1.0/24 --type arp
```

Replace the example addresses with targets you are authorized to scan.

## Options

| Option | Description |
| --- | --- |
| `target` | Target IP address or network in CIDR notation |
| `-t, --type` | Scan type: `all`, `icmp`, `tcp`, or `arp` (default: `all`) |
| `-p, --ports` | TCP ports, such as `80,443` or a range such as `1-1000` |
| `-T, --timeout` | Timeout in seconds (default: `2`) |

Show all command-line options with:

```bash
python src/main.py --help
```

## Notes

- Some scan types may require elevated privileges.
- Firewalls and network configuration can affect scan results.
- Only scan systems and networks for which you have permission.

## Project layout

```text
Network-Scanner/
├── src/
│   ├── main.py
│   └── scanner.py
├── tests/
├── docs/
├── requirements.txt
└── README.md
```

## License

See [LICENSE](LICENSE) for license details.
