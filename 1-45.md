# CN

---

## 1. The Network Edge: Access Networks & Physical Media

The **network edge** is where end systems (computers, phones, servers) connect to the internet. This connection is facilitated by an **Access Network**, which links an end system to its first router, known as the **edge router**.

### 1.1 Access Networks: The On-Ramp to the Internet 🚗

#### **Home Access**
* **Digital Subscriber Line (DSL)**:
    * **Description**: Internet access over existing telephone lines. Your telephone company (telco) becomes your ISP.
    * **Technology**: Uses a **DSL modem** at home and a **DSLAM** (Digital Subscriber Line Access Multiplexer) at the telco's central office. It employs **Frequency-Division Multiplexing (FDM)** to carry voice and data on the same line at different frequencies.
    * **Key Feature**: **Asymmetric**, meaning download speeds are significantly faster than upload speeds. Performance degrades with distance from the central office.

* **Cable Internet**:
    * **Description**: Internet access over existing cable TV infrastructure.
    * **Technology**: Uses a **Cable Modem** at home and a **CMTS** (Cable Modem Termination System) at the cable company's headend. The physical infrastructure is **Hybrid Fiber Coax (HFC)**.
    * **Key Feature**: It's a **shared broadcast medium**. Bandwidth is shared among all users in a neighborhood, so speeds can slow down during peak usage times.

* **Fiber to the Home (FTTH)**:
    * **Description**: The fastest residential access, providing a direct optical fiber connection to the home.
    * **Technology**: The most common architecture is a **Passive Optical Network (PON)**, which uses passive splitters to serve multiple homes from a single fiber.
    * **Key Feature**: Capable of gigabit speeds, offering superior performance.

#### **Enterprise & Local Access**
* **Ethernet**: The dominant **wired** technology for Local Area Networks (LANs) in companies, universities, and homes. Users connect via twisted-pair copper wire to an **Ethernet switch**.
* **WiFi**: The dominant **wireless** technology for LANs (based on the IEEE 802.11 standard). Users connect wirelessly to an **Access Point (AP)**, which is wired into the larger network.

#### **Wide-Area Wireless Access**
* **Cellular (4G/5G)**: Provides mobile internet access over large distances (tens of kilometers) by connecting devices to a provider's **base station**.

### 1.2 Physical Media: The Wires and Waves 🌐

Physical media carry the actual signals (bits) between transmitter-receiver pairs.

* **Guided Media** (Signal confined to a physical path):
    * **Twisted-Pair Copper Wire**: Most common and inexpensive. Used for DSL and Ethernet.
    * **Coaxial Cable**: Better shielding than twisted-pair, allowing for higher data rates. Used for cable internet.
    * **Fiber Optic Cable**: Transmits data as pulses of light. It's the highest-speed medium, immune to interference, and forms the backbone of the global internet.
    

* **Unguided Media** (Signal propagates wirelessly):
    * **Terrestrial Radio**: Used for WiFi, cellular networks, and Bluetooth.
    * **Satellite Radio**: Provides connectivity in remote areas but suffers from high latency (delay) due to the vast distances signals must travel.

---

## 2. The Network Core: Moving Data Across the Globe

The network core is the mesh of interconnected routers that links all the access networks together.

### 2.1 Packet Switching (The Internet's Method) 📦

* **Core Concept**: Long messages are broken into smaller chunks called **packets**. Each packet travels independently through the network. Network resources are shared on demand.
* **Store-and-Forward**: A fundamental principle where a router must receive an **entire packet** before it can begin transmitting (forwarding) it to the next link in the path. This introduces a small delay at every router.
* **Queuing Delays & Packet Loss**: Since links are shared, if packets arrive at a router faster than they can be sent out, they are placed in a line (**queue** or buffer). This wait time is the **queuing delay**. If the queue is full, newly arriving packets are dropped, which is called **packet loss**.
* **Forwarding Tables & Routing**:
    * **Forwarding**: The local action a router takes to send a packet to the next hop. It uses the packet's destination IP address to look up the appropriate outbound link in its **forwarding table**.
    * **Routing**: The global process of determining the best paths for packets to take. **Routing protocols** are the algorithms routers use to collectively build their forwarding tables.

### 2.2 Circuit Switching (The Traditional Telephone Method) ☎️

* **Core Concept**: A dedicated end-to-end path (**circuit**) is established before any data is sent. Resources (bandwidth, processing) along that path are **reserved** for the entire duration of the session, whether they are being used or not.
* **Multiplexing**:
    * **Frequency-Division Multiplexing (FDM)**: The link's frequency spectrum is divided into dedicated bands for each circuit.
    * **Time-Division Multiplexing (TDM)**: Time is divided into frames, and each circuit gets a dedicated time slot in every frame.

### 2.3 Packet vs. Circuit Switching: A Comparison

| Feature               | Packet Switching (Internet)                                | Circuit Switching (Telephone)                          |
| --------------------- | ---------------------------------------------------------- | ------------------------------------------------------ |
| **Resource Allocation** | On-demand, shared resources.                               | Resources are reserved and dedicated.                  |
| **Efficiency** | Highly efficient for "bursty" traffic (e.g., web browsing). | Inefficient; reserved resources are wasted during idle periods. |
| **Performance** | Not guaranteed; can have variable delays and packet loss.  | Guaranteed, constant performance once the circuit is established. |
| **Setup** | No connection setup required; packets are sent immediately. | Requires an initial delay to set up the end-to-end circuit. |

---

## 3. The Internet's Structure: A Network of Networks 🌍

The internet isn't a single network but a massive interconnection of thousands of separate networks run by **Internet Service Providers (ISPs)**.

* **The ISP Hierarchy**:
    1.  **Access ISPs**: Your local provider that connects you directly (e.g., Comcast, your university).
    2.  **Regional ISPs**: Larger networks that connect access ISPs in a specific region.
    3.  **Tier-1 ISPs**: The massive, global backbone networks (e.g., AT&T, Level 3). They are at the top of the hierarchy and can reach every other network on the internet without paying for transit.

* **How Networks Interconnect**:
    * **Customer-Provider Relationship**: A smaller ISP (the customer) pays a larger ISP (the provider) to carry its traffic to the rest of the internet.
    * **Peering**: When two ISPs at the same level (e.g., two Tier-1 ISPs) agree to connect their networks directly and exchange traffic between their customers for free. This is often **settlement-free**.
    * **Internet Exchange Point (IXP)**: A physical location (like a large data center) where multiple ISPs can meet to efficiently set up peering connections.
    * **Multi-homing**: A strategy for reliability where an ISP connects to two or more provider ISPs. If one link fails, traffic can flow through the other.


* **Content Provider Networks**:
    * **Who**: Large companies like **Google, Netflix, and Amazon**.
    * **What**: They have built their own massive, private global networks to host and deliver their content.
    * **Strategy**: They try to **bypass the upper tiers** of the internet by connecting directly to lower-tier ISPs (often at IXPs). This reduces their costs (by not paying Tier-1 ISPs) and gives them more control over the user experience, resulting in faster and more reliable service.
