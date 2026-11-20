# netscanner

Checking ports across hosts helps identify which network services accept connections. netscanner scans **TCP and UDP** ports and reports whether they are open or closed.

## Features

- Scan one TCP or UDP port on a hostname.
- Scan the first 1023 ports on a host.
- Scan all ports or a chosen port range.
- Scan one port across the IP addresses in a `/24` or `/32` subnet.
- Save results to a file for supported scan commands.

## Installation

Install Go, check out the repository, and build the executable from its root directory:

```shell
go build -o netscanner .
```

The command creates a `netscanner` executable in the current directory.

## Usage

Scan a single TCP port:

```shell
./netscanner sp tcp 127.0.0.1 80
```

Example output:

```text
 Port     status   service

 80/tcp,  Closed,  http
```

Available scan commands:

```text
sp,scanport       scan one port
in,initscan       scan the first 1023 ports
cs,completescan   scan all ports
sft,scanfromto    scan a port range
msp,maskscanport  scan one port across a subnet
```

Use `tcp` or `udp` as the protocol. Range scans take a start port and an end port. Initial, complete, range, and subnet scans also accept `true` or `false` to control whether the results are saved to a file. Subnet targets must include `/24` or `/32`.

Examples:

```shell
./netscanner in tcp 127.0.0.1 false
./netscanner sft tcp 127.0.0.1 80 443 true
./netscanner msp tcp 127.0.0.1/24 true
```

Use `h` or `help` for help, `v` or `version` for the version, and `info` or `information` for project information.

## License

This project is licensed under the MIT License. It is based on [R4yGM/netscanner](https://github.com/R4yGM/netscanner), with attribution retained in accordance with that license.

