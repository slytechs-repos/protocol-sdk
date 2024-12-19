# Network Protocol SDK Architecture

## 1. Introduction
This document details the architecture of the Network Protocol SDK suite, comprising multiple specialized SDKs for packet capture, protocol analysis, blockchain protocols, and network intelligence. The architecture emphasizes modularity, clear separation of concerns, and extensibility while maintaining consistent interface patterns across all components.

## 2. SDK Families

### 2.1 Core SDK Components
```
jnetpcap-sdk              (com.slytechs.jnet.jnetpcap)
protocol-network-sdk      (com.slytechs.jnet.protocol)
blockchain-protocol-sdk   (com.slytechs.jnet.protocol.blockchain)
network-intelligence-sdk  (com.slytechs.jnet.intelligence)
```

Each SDK provides independent yet interoperable functionality, with clear boundaries and well-defined interfaces. The modular design allows for independent versioning, licensing, and deployment while maintaining consistent architectural patterns.

## 3. Detailed Module Structure

### 3.1 jnetpcap-sdk
```
jnetpcap-sdk
├── jnetpcap-api                         # JNetPcap API
│   └── com.slytechs.jnet.jnetpcap
        ├── NetPcap                      // Main pcap interface
        ├── PacketHandler                // Packet processing
        └── PcapHeader                   // Packet headers
├── jnetpcap-wrapper                     # Native Wrapper
│   └── org.jnetpcap                     
├── jnetpcap-examples                    # Examples
└── jnetpcap-tests                       # Tests
```

### 3.2 protocol-network-sdk
```
protocol-network-sdk
├── protocol-api                         # Common Protocol API
│   └── com.slytechs.jnet.protocol.api
        ├── stack                        # Protocol Stack Framework
        │   ├── ProtocolStack            // Main stack abstraction
        │   ├── LayerProcessor           // Layer processing
        │   │   ├── L2Processor          // Link layer
        │   │   ├── L3Processor          // Network layer
        │   │   └── L4Processor          // Transport layer
        │   ├── StackPipeline            // Stack pipeline
        │   │   ├── StackProcessor       // Stack processor
        │   │   ├── StackContext         // Processing context
        │   │   └── StackEvent           // Stack events
        │   └── features                 // Stack Features
        │       ├── Reassembly           // IP reassembly
        │       ├── Fragmentation        // IP fragmentation
        │       └── Checksums            // Checksum validation
        ├── common                       # Common Components
        │   ├── Header                   // Base header interface
        │   ├── HasHeader                // Header presence
        │   ├── HeaderSupplier           // Header factory
        │   ├── HeaderFactory            // Creation factory  
        │   ├── HeaderLookup             // Protocol lookup
        │   └── HeaderInfo               // Header metadata
        ├── packet                       # Packet Processing
        │   ├── Packet                   // Packet abstraction
        │   ├── PacketFactory            // Packet creation
        │   ├── PacketBuffer             // Raw data management
        │   ├── PacketDescriptor         // Packet metadata
        │   └── PacketFormat             // Formatting
        ├── meta                         # Metadata Framework
        │   ├── MetaContext              // Protocol metadata
        │   ├── MetaField                // Field metadata
        │   ├── MetaFormat               // Format metadata
        │   └── MetaValue                // Field values
        └── pipeline                     # Processing Pipeline
            ├── Pipeline                 // Main pipeline
            ├── Processor                // Protocol processor
            ├── ProcessorContext         // Process context
            └── ProcessorChain           // Processor chain

├── protocol-tcpip                       # TCP/IP Implementation
│   └── com.slytechs.jnet.protocol.tcpip
        ├── link                         # Layer 2
        │   ├── ethernet                 // Ethernet II
        │   ├── vlan                     // VLAN
        │   └── arp                      // ARP
        ├── network                      # Layer 3
        │   ├── ip                       // IPv4/IPv6
        │   └── icmp                     // ICMP
        └── transport                    # Layer 4
            ├── tcp                      // TCP
            └── udp                      // UDP

[Additional protocol modules with similar structure]
├── protocol-telco                       # Telecom Protocols
├── protocol-web                         # Web Protocols
├── protocol-microsoft                   # Microsoft Protocols
├── protocol-database                    # Database Protocols
└── protocol-media                       # Media Protocols
```

### 3.3 blockchain-protocol-sdk
```
blockchain-protocol-sdk
├── blockchain-common                    # Common Blockchain
│   └── com.slytechs.jnet.protocol.blockchain.common
        ├── consensus                    # Consensus Protocols
        └── p2p                         # P2P Network

[Blockchain implementations]
├── blockchain-bitcoin                   # Bitcoin Protocol
├── blockchain-ethereum                  # Ethereum Protocol
├── blockchain-ripple                    # Ripple Protocol
└── blockchain-litecoin                  # Litecoin Protocol
```

### 3.4 network-intelligence-sdk
```
network-intelligence-sdk
├── protocol-analytics                   # Protocol Analysis
├── security-analytics                   # Security Analysis
├── blockchain-analytics                 # Blockchain Analysis
├── telco-analytics                      # Telecom Analytics
│   ├── voip                            # VoIP Intelligence
│   │   ├── quality                     // Call quality
│   │   ├── fraud                       // Fraud detection
│   │   └── performance                 // Performance
│   ├── signaling                       # Signaling Analytics
│   ├── subscriber                      # Subscriber Analytics
│   └── roaming                         # Roaming Analytics
├── mobile-analytics                     # Mobile Analytics
│   ├── radio                           # Radio Network
│   ├── core                            # Core Network
│   └── service                         # Service Analytics
└── intelligence-common                  # Common Components
```

## 4. Key Architecture Changes

### 4.1 Naming Changes
- Renamed 'core' to 'common' across all modules
- Standardized '-sdk' suffix for major components
- Unified protocol package naming

### 4.2 Package Reorganization
- Moved shared interfaces to protocol-api
- Consolidated stack interfaces
- Unified pipeline architecture

### 4.3 New Components
- Enhanced telco analytics modules
- Expanded blockchain support
- Added intelligence capabilities

### 4.4 Integration Patterns
- Consistent pipeline architecture
- Standard event model
- Unified descriptor system
- Common metadata framework

## 5. Usage Guidelines

### 5.1 Dependencies
- protocol-api required by all modules
- Intelligence modules optional
- Protocol implementations independent

### 5.2 Extension Points
- Protocol processors
- Stack features
- Analytics engines
- Custom protocols

## 6. Conclusion
This architecture provides a flexible, modular framework for network protocol analysis and processing, with clear extension points and consistent patterns across all components.
