☁️ Hybrid Multi-Cloud Network: Availability & Performance Analysis

This repository contains the project materials developed for the Availability and Performance course unit (2025/2026) at the Coimbra Institute of Engineering (ISEC).

The primary goal of this project was to design, implement, and analyze a functional Hybrid Multi-Cloud infrastructure. By interlinking an on-premises environment with multiple public cloud providers, the project explores high-availability strategies and benchmarks network performance across distributed environments.

🎯 Project Objective

The objective was to transition from rigid local data centers to flexible, virtual "on-demand" resources while mitigating common cloud risks:

    Vendor Lock-in: Reducing dependency on a single Cloud Service Provider (CSP).

    Single Point of Failure (SPOF): Distributing resources across multiple providers to ensure that a global outage at one provider does not halt operations.

    Manual Routing Risks: Replacing human-error-prone static routing with automated, self-healing dynamic protocols.

    Quantifying Resiliance: Measuring the Recovery Time Objective (RTO) during simulated link and provider failures.

🏗️ Network Architecture

The infrastructure integrates a local on-premises site with three major cloud providers: Microsoft Azure, Amazon Web Services (AWS), and Google Cloud Platform (GCP).

The network utilizes a Full Mesh topology, where every node is connected to every other node to ensure maximum redundancy.

    On-Premises (Core): Simulated using GNS3, with a pfSense firewall acting as the central Customer Gateway (CGW).

    Cloud Nodes:

        Microsoft Azure: Utilizes Virtual Networks (VNet) and Virtual Network Gateways (VNG).

        AWS: Utilizes Virtual Private Clouds (VPC) and Virtual Private Gateways (VPGW).

        GCP: Utilizes Cloud Routers and Cloud VPN for BGP integration.

    Connectivity (Backbone):

        VPN IPsec: All connections are secured via Site-to-Site tunnels using IKEv2 and AES-256 encryption.

        Dynamic Routing: The Border Gateway Protocol (BGP) manages route exchange across four distinct Autonomous Systems (AS).

🔌 Services and Components
Services Provided

The infrastructure supports a resilient, geographically distributed application layer:

    Distributed Web Service: Nginx servers hosted on Ubuntu VMs across different clouds, providing a unified service with failover capabilities.

    Private Connectivity: All communication occurs over private IP address spaces, ensuring that traffic never touches the public internet without encryption.

    Self-Healing Mechanisms: BGP Keepalive messages automatically detect link failures and reroute traffic to available paths.

Network Components

    Active Equipment:

        pfSense: Edge router and VPN concentrator for the on-premises site.

        FRR (Free Range Routing): Protocol suite installed on pfSense to handle BGP peering.

        Ubuntu Cloud Guest VMs: Endpoint servers used for hosting web content and performance testing.

    Passive/Virtual Components: Virtual Tunnel Interfaces (VTI), Security Groups (NSG), and APIPA addressing for BGP peering.

📋 Key Standards and Metrics

Material and protocol selection focused on industry standards for cross-cloud interoperability:

    Routing Protocol: BGP with specific Autonomous System Numbers:

        On-Premises: ASN 65530

        Azure: ASN 65515

        AWS: ASN 64512

    Encryption Standard: IPsec IKEv2 with Route-based VTI.

    Performance Benchmarking:

        Latency (RTT): Cloud-to-Cloud direct latency measured as low as 2 ms via overlay networks.

        Hybrid Latency: On-Premises to Cloud latency averaged between 33 ms and 42 ms.

🛠️ Technologies and Tools

    Simulation: GNS3.

    Firewall/Routing: pfSense , FRRouting (FRR).

    Cloud Providers: Microsoft Azure , Amazon Web Services , Google Cloud Platform.

    Analysis Tools: ICMP (Ping) for latency , Nginx for service availability.

📁 Repository Contents

    DD2526-GRP02-Relatorio.pdf: The final technical report, including theoretical foundations, detailed configuration steps, and critical results.

    DD2526-GRP02-Apresentacao.pdf: Summary presentation slides used for the final project defense.

👤 Authors

    João Pedro Vila Pomar

    João Pedro Xia

    Rodolfo Miguel de Sousa Belchior Brás Oliveira
