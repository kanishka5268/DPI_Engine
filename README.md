# Deep Packet Inspection (DPI) Engine

A lightweight Deep Packet Inspection (DPI) engine developed in C++17 for analyzing network traffic stored in PCAP files. The project parses network packets, extracts protocol information, identifies HTTPS applications using TLS Server Name Indication (SNI), and applies configurable packet filtering rules before generating traffic statistics.

This project demonstrates practical concepts in computer networks, packet parsing, protocol analysis, and systems programming using modern C++.

---

## Features

- Reads offline PCAP capture files
- Parses Ethernet, IPv4, TCP and UDP packets
- Extracts payload from network packets
- Performs TLS Client Hello inspection
- Extracts Server Name Indication (SNI)
- Identifies common web applications (YouTube, Google, Facebook, GitHub, etc.)
- Tracks network flows using Five-Tuples
- Supports rule-based packet filtering
- Generates application-wise traffic statistics
- Writes filtered packets to a new PCAP file

---

## Architecture

Input PCAP --> PCAP Reader --> Packet Parser --> Protocol Analysis --> TLS SNI Extraction --> Application Classification --> Filtering Rules --> Output PCAP + Statistics

## Tech Stack

- C++17
- STL
- CMake
- File I/O
- Object-Oriented Programming
- Computer Networks
- Packet Parsing

---

## Folder Structure

include/
    pcap_reader.h
    packet_parser.h
    sni_extractor.h
    types.h

src/
    main.cpp
    pcap_reader.cpp
    packet_parser.cpp
    sni_extractor.cpp
    types.cpp

---

## Core Components

### PCAP Reader
Reads raw packet data from PCAP capture files and validates file headers before sequential packet processing.

---

### Packet Parser
Decodes protocol headers including
- Ethernet
- IPv4
- TCP
- UDP
  
and extracts payload information for further inspection.

---

### TLS SNI Extractor
Inspects TLS Client Hello packets to extract the Server Name Indication (SNI), allowing encrypted HTTPS traffic to be classified without decrypting packet contents.

---

### Flow Tracker
- Maintains network flows using the standard Five-Tuple:
- Source IP
- Destination IP
- Source Port
- Destination Port
- Protocol

---

## Features

- Reads offline PCAP capture files
- Parses Ethernet, IPv4, TCP and UDP packets
- Extracts payload from network packets
- Performs TLS Client Hello inspection
- Extracts Server Name Indication (SNI)
- Identifies common web applications (YouTube, Google, Facebook, GitHub, etc.)
- Tracks network flows using Five-Tuples
- Supports rule-based packet filtering
- Generates application-wise traffic statistics
- Writes filtered packets to a new PCAP file

---

## Architecture
```
Input PCAP --> PCAP Reader --> Packet Parser --> Protocol Analysis --> TLS SNI Extraction --> Application Classification --> Filtering Rules --> Output PCAP + Statistics

```

---

## Folder Structure

```
Deep-Packet-Inspection-Engine/

├── include/
│   ├── pcap_reader.h
│   ├── packet_parser.h
│   ├── sni_extractor.h
│   └── types.h
│
├── src/
│   ├── main.cpp
│   ├── pcap_reader.cpp
│   ├── packet_parser.cpp
│   ├── sni_extractor.cpp
│   └── types.cpp
│
├── test_dpi.pcap
├── generate_test_pcap.py
├── CMakeLists.txt
├── README.md
└── LICENSE
```

---

## Core Components

### PCAP Reader

Reads packets from a PCAP file, validates the file format, and sequentially loads packet data for further processing.

---

### Packet Parser

Parses protocol headers including:

- Ethernet
- IPv4
- TCP
- UDP

and extracts relevant metadata such as IP addresses, ports, protocol type, and payload.

---

### TLS SNI Extractor

Inspects TLS Client Hello packets to extract the **Server Name Indication (SNI)** field, enabling HTTPS application identification without decrypting encrypted traffic.

---

### Flow Tracking

Maintains active network flows using the standard **Five-Tuple**:

- Source IP Address
- Destination IP Address
- Source Port
- Destination Port
- Transport Protocol

---

### Rule Engine

Supports configurable filtering based on:

- Source IP Address
- Application Type
- Domain Name

Packets matching configured rules are filtered before being written to the output PCAP.

---

## Build Instructions

### Clone the repository

```bash
git clone https://github.com/yourusername/Deep-Packet-Inspection-Engine.git

cd Deep-Packet-Inspection-Engine
```

### Build

```bash
mkdir build

cd build

cmake ..

make
```

---

## Usage

```bash
./dpi_engine input.pcap output.pcap
```

### Block an application

```bash
./dpi_engine input.pcap output.pcap --block-app YouTube
```

### Block a domain

```bash
./dpi_engine input.pcap output.pcap --block-domain google.com
```

### Block an IP address

```bash
./dpi_engine input.pcap output.pcap --block-ip 192.168.1.50
```

---

## Sample Output

```
======================================================
                Deep Packet Inspection Engine
======================================================

Input File      : traffic.pcap
Output File     : filtered_output.pcap

Processing packets...

================ DPI REPORT ================

Packets Processed : 12456

TCP Packets       : 9871
UDP Packets       : 2585

Detected Applications
---------------------
Google            : 2310
YouTube           : 1421
GitHub            : 386
Facebook          : 271

Forwarded Packets : 11863
Blocked Packets   : 593
Active Flows      : 542

Output Saved To
---------------
filtered_output.pcap

============================================
```

---

## Technologies Used

- C++17
- Standard Template Library (STL)
- CMake
- Object-Oriented Programming
- PCAP File Processing
- Packet Parsing
- TLS SNI Inspection

---

## Concepts Demonstrated

- Deep Packet Inspection (DPI)
- Network Packet Parsing
- Ethernet / IPv4 / TCP / UDP Protocols
- TLS Client Hello Analysis
- HTTPS Traffic Classification
- Five-Tuple Flow Tracking
- Rule-Based Packet Filtering
- Modular Software Design

---

## Future Improvements

- IPv6 support
- DNS packet inspection
- HTTP Host header analysis
- Live packet capture
- Configuration file for filtering rules
- Export traffic statistics as JSON
- Multi-threaded packet processing
- Interactive command-line interface

This project is intended for educational and learning purposes.
