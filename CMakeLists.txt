cmake_minimum_required(VERSION 3.16)

project(DeepPacketInspectionEngine VERSION 1.0)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Header files
include_directories(${CMAKE_SOURCE_DIR}/include)

# Source files
set(SOURCES
    src/main.cpp
    src/pcap_reader.cpp
    src/packet_parser.cpp
    src/sni_extractor.cpp
    src/types.cpp
)

# Create executable
add_executable(dpi_engine ${SOURCES})

# macOS-specific settings
if(APPLE)
    # Add macOS-specific libraries here if needed
endif()
