# DPI Engine

A multithreaded Deep Packet Inspection engine implemented in C++17 that parses PCAP captures, tracks network flows using five-tuples, extracts TLS Server Name Indication (SNI), classifies applications, and applies configurable filtering rules.

Features
--------
• PCAP parsing
• Ethernet / IPv4 / TCP / UDP parsing
• TLS Client Hello SNI extraction
• HTTP Host header extraction
• Flow tracking
• Rule-based filtering
• Multi-threaded pipeline
• Traffic statistics

Architecture
------------
Reader
   ↓
Load Balancers
   ↓
Fast Path Workers
   ↓
Output Writer

Tech Stack
----------
C++17
STL
Multithreading
PCAP Parsing

Future Work
-----------
• QUIC support
• Bandwidth throttling
• Live dashboard
