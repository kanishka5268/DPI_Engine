# Deep Packet Inspection (DPI) Engine

A lightweight Deep Packet Inspection (DPI) engine developed in C++17 for analyzing network traffic stored in PCAP files. The project parses network packets, extracts protocol information, identifies HTTPS applications using TLS Server Name Indication (SNI), and applies configurable packet filtering rules before generating traffic statistics.

This project demonstrates practical concepts in computer networks, packet parsing, protocol analysis, and systems programming using modern C++.

Features
--------
• Reads offline PCAP capture files
• Parses Ethernet, IPv4, TCP and UDP packets
• Extracts payload from network packets
• Performs TLS Client Hello inspection
• Extracts Server Name Indication (SNI)
• Identifies common web applications (YouTube, Google, Facebook, GitHub, etc.)
• Tracks network flows using Five-Tuples
• Supports rule-based packet filtering
• Generates application-wise traffic statistics
• Writes filtered packets to a new PCAP file

Architecture
------------
Input PCAP --> PCAP Reader --> Packet Parser --> Protocol Analysis --> TLS SNI Extraction --> Application Classification --> Filtering Rules --> Output PCAP + Statistics

Tech Stack
----------
C++17
STL
CMake
File I/O
Object-Oriented Programming
Computer Networks
Packet Parsing

Folder Structure
----------------
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

Core Components
---------------
PCAP Reader/
Reads raw packet data from PCAP capture files and validates file headers before sequential packet processing.

Packet Parser/
Decodes protocol headers including
• Ethernet
• IPv4
• TCP
• UDP
and extracts payload information for further inspection.

TLS SNI Extractor/
Inspects TLS Client Hello packets to extract the Server Name Indication (SNI), allowing encrypted HTTPS traffic to be classified without decrypting packet contents.

Flow Tracker/
• Maintains network flows using the standard Five-Tuple:
• Source IP
• Destination IP
• Source Port
• Destination Port
• Protocol

Rule Engine/
Supports filtering packets based on
• Source IP
• Application Type
• Domain Name

Example
-------
Input:

capture.pcap

↓

Detected

Google
YouTube
GitHub
Facebook

↓

Blocked

YouTube

↓

Output

filtered_output.pcap

Build
-----
mkdir build

cd build

cmake ..

make

Run
---
./dpi_engine input.pcap output.pcap

Example/
./dpi_engine traffic.pcap filtered.pcap --block-app YouTube

Future Improvements
-------------------
• Live packet capture support
• IPv6 parsing
• DNS packet analysis
• HTTP Host header extraction
• Multi-threaded packet processing
• QUIC protocol support
• Real-time dashboard

Concepts Demonstrated
---------------------
• Packet Parsing
• File Processing
• Object-Oriented Design
• Network Protocols
• TLS Handshake Analysis
• Hash Maps
• Rule-Based Filtering
• Modern C++ Programming
