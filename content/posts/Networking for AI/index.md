---
title: "Networking for AI"
date: 2024-03-02T13:12:33-04:00
draft: false
toc: false
#cover: "img/cover.png"
#coverCaption: "image created with chatGPT"
tags:
  - networking
  - AI
---
{{< image src="/img/RDMA.png" alt="Image created by ChatGPT" position="center" style="border-radius: 8px;" >}}

AI has become a significant force in the market, reshaping how people perceive technology. While I enjoy using AI models to craft images and descriptions for my D&D group, immortalizing our adventures, my interaction with AI has been limited to this recreational use. Professionally, as a network engineer, my involvement with AI models is mostly limited to drawing inspiration from them for new ideas, or getting help rewording my emails and other communications. However, recently, I’ve delved into understanding how network design differs for AI farms and the rationale behind using different technologies or hardware setups.

#### RDMA

Let me introduce you to **RDMA**, which stands for Remote Direct Memory Access. RDMA bypasses the CPU and other traditional data access methods, pulling information directly from memory and transmitting it to the server array for model training. This technology is crucial as AI models are highly sensitive to packet loss, hence requiring a lossless approach. InfiniBand is another approach to this problem. While it’s intriguing, it relies on proprietary hardware not commonly found in most companies’ existing infrastructure. Consequently, setting up an AI deployment becomes significantly more expensive due to the need to acquire specific network hardware.

#### RoCE

Fortunately, there’s a solution: **RoCE (RDMA over Converged Ethernet)**. Essentially, RoCE offers the benefits of RDMA, such as bypassing the CPU and reducing latency, but can be implemented using existing Ethernet infrastructure. While this is an appealing option, there isn’t a standardized industry framework for it as far as I know. It remains to be seen which technology will prevail and steer the direction of the industry.

#### Comparing Technologies and Connectivity Requirements

- **InfiniBand (IB)**: 
  - **Connectivity Requirement**: Layer 2
  - **Description**: InfiniBand is a high-performance, low-latency networking technology primarily used in high-performance computing (HPC) environments.

- **RoCE Versions**:
  - **RoCE v1**:
    - **Connectivity Requirement**: Layer 2
    - **Description**: RoCE v1 relies on Ethernet frames and requires the network devices to be within the same Ethernet broadcast domain (i.e., the same VLAN/subnet).
  
  - **RoCE v2**:
    - **Connectivity Requirement**: Layer 3
    - **Description**: RoCE v2 encapsulates the RDMA traffic within UDP/IP packets, allowing it to traverse IP networks. This version supports layer 3 connectivity, meaning it can operate across different subnets and routed networks.

### Final Thoughts

I’m particularly interested in the infrastructure aspect of AI, which aligns closely with my career experiences. I’ll be closely monitoring developments in this area in the future. I’m looking forward to the day when I can set up a miniature version of these setups in my homelab and conduct real-world tests comparing the benefits of RoCE versus the classic Spine and Leaf design without AI-specific protocols. Given the rapid pace of industry evolution, that day might arrive sooner than expected.

