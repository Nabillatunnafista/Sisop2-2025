# Sistem Operasi Nabillatun Nafista (27)
Tugas mata kuliah Sistem Operasi pertemuan kedua yang disusun oleh Nabillatun Nafista dengan NRP 3124521027 dari kelas 1 TI-A
## Practice Exercises

## 1.1 What are the three main purposes of an operating system?
**Answer:**
1. **Resource Management**: Allocating and managing CPU, memory, I/O devices, and storage efficiently.
2. **User Interface**: Providing an environment for users to run programs.
3. **Program Execution**: Loading, running, and terminating processes in a safe and controlled manner.

## 1.2 When is it appropriate for the operating system to forsake efficiency and "waste" resources? Why is such a system not really wasteful?
**Answer:**
- If it improves the user experience, for example, with a more interactive GUI even though it uses more memory.
- In virtualization, the OS uses more resources for security and process isolation.
- A more flexible and modular system can be more resource-intensive but easier to adapt to different needs.
- It is not always wasteful if the increased performance and convenience are worth the cost of the additional resources.

## 1.3 What is the main difficulty in writing an operating system for a real-time environment?
**Answer:**
The main challenge is ensuring that the system meets strict time constraints. In a real-time system, tasks must be executed within a certain time limit to ensure timely responses to events. This requires careful task scheduling and prioritization based on urgency and importance.

## 1.4 Should an operating system include applications such as web browsers and mail programs? Argue both sides.
**Answer:**

### Arguments for including these applications:
1. **Better Integration**: These applications will be more integrated with the OS, making it easier to interact with the network and other resources.
2. **Ease of Use**: Users will not have to download additional applications, resulting in a smoother experience and fewer compatibility issues.
3. **Consistency and Standardization**: The user experience will be consistent across platforms, and security updates can be applied simultaneously.

### Arguments against including these applications:
1. **Focus on Basic OS Tasks**: The OS should focus on hardware and resource management, not additional applications.
2. **Updates and Security**: These applications often require rapid updates, which can be hampered by OS dependency.
3. **User Freedom**: Users can choose applications according to their needs without being restricted by OS applications.

An operating system should focus on basic tasks and allow additional applications provided by third parties. However, if the goal is a smoother user experience, including basic applications in the OS can be beneficial.

## 1.5 How does the distinction between kernel mode and user mode function as a rudimentary form of protection (security)?
**Answer:**
- **Kernel mode** has full access to the hardware and all system resources.
- **User mode** restricts access so that applications cannot directly access the hardware. This prevents malicious applications from damaging the system by separating OS functions from user programs.

## 1.6 Which of the following instructions should be privileged?
a.	Set value of timer.
b.	Read the clock.
c.	Clear memory.
d.	Issue a trap instruction.
e.	Turn off interrupts.
f.	Modify entries in device-status table.
g.	Switch from user to kernel mode.
h.	Access I/O device.
 
**Answer:**

### Privileged:
- a. Set value of timer  
- c. Clear memory  
- d. Issue a trap instruction  
- e. Turn off interrupts  
- f. Modify entries in device-status table  
- g. Switch from user to kernel mode  
- h. Access I/O device  

### Not privileged:
- b. Reading the clock (because reading the time does not change the system state)  

## 1.7 Some early computers protected the operating system by placing it in a memory partition that could not be modified by either the user job or the operating system itself. Describe two difficulties that you think could arise with such a scheme.
**Answer:**
1. **Less Flexible**: If the OS memory is too small, it is difficult to perform updates or expand features.
2. **Complex Memory Management**: Separating OS and user memory requires additional mechanisms that can slow down the system.

## 1.8 Some CPUs provide for more than two modes of operation. What are two possible uses of these multiple modes?
**Answer:**
1. **Supervisor Mode**: Used for debugging or limited access to kernel features.
2. **Virtualization Mode**: To run multiple OS simultaneously in a virtual environment.

## 1.9 Timers could be used to compute the current time. Provide a short description of how this could be accomplished.
**Answer:**
- The OS initializes the timer with an initial value.
- The timer counts down and generates an interrupt when it reaches zero.
- The OS catches the interrupt and records the current time.
- By comparing it to the previous time, the OS can calculate the elapsed time.

## 1.10 Give two reasons why caches are useful. What problems do they solve? What problems do they cause? If a cache can be made as large as the device for which it is caching (for instance, a cache as large as a disk), why not make it that large and eliminate the device?
**Answer:**

### Advantages of cache:
- Faster access compared to RAM or secondary storage.
- Reduces the load on main memory by storing frequently used data.

### Problems that cache can solve:
- Reduces access time to frequently accessed data.

### Problems caused by cache:
- **Data incoherence**: If the cache is not updated correctly, data can differ from that in main memory.
- **High cost**: Cache is more expensive than regular RAM.
- If the cache is as large as main memory, then its differences with RAM will disappear, making the memory hierarchy no longer efficient.

## 1.11 Distinguish between the client-server and peer-to-peer models of distributed systems.
**Answer:**

### Client-Server Model:
- **Structure**: There is a clear division between the client requesting the service and the server providing the service.
- **Centralization**: The server acts as the central provider of the service, while the client only accesses it.
- **Security**: The server controls access and management of resources.
- **Examples**: Web browsing, email.

### Peer-to-Peer (P2P) Model:
- **Structure**: All nodes (peers) act as both clients and servers.
- **Decentralization**: There is no central server; each peer can share resources and services.
- **Security**: Security is more difficult to manage because there is no central control.
- **Examples**: File sharing (BitTorrent), cryptocurrency.

## Chapter 1 Exercises
## 1.12 How do clustered systems differ from multiprocessor systems? What is required for two machines belonging to a cluster to cooperate to provide a highly available service?

**Answer:**
### Cluster System:
A cluster system consists of multiple separate machines connected to work together as a single system. These machines may have separate processors and memory, and they communicate over a network. Clusters can be used to provide high-availability services or distributed computing capabilities.

### Multiprocessor System:
A multiprocessor system refers to a computer with more than one processor sharing the same main memory. All processors work within a single physical system and share resources directly.

### What is Required for Two Machines in a Cluster to Work Together for High Availability:
1. **Data Replication**: To ensure that data is available if one node fails.
2. **Failover and Load Balancing**: So that requests can be processed by other nodes if one node fails.
3. **Time Synchronization**: So that both machines have synchronized time to ensure transactions and data remain consistent.

## 1.13 Consider a computing cluster consisting of two nodes running a database. Describe two ways in which the cluster software can manage access to the data on the disk. Discuss the benefits and disadvantages of each.

**Answer:**
### 1. Shared-Disk Architecture
In this architecture, both nodes have direct access to the same storage (e.g., SAN or NAS). The cluster software is responsible for managing access to avoid conflicts or inconsistencies.

#### Advantages:
- Fast failover: If one node fails, the other node can immediately take over without having to copy or recover data.
- Storage efficiency: No need to duplicate data across multiple nodes.

#### Disadvantages:
- Potential bottleneck: Under high load, access to shared storage can be a weak point in system performance.
- Reliance on shared storage: If a storage system fails, all nodes can be affected.

### 2. Shared-Nothing Architecture
In this approach, each node has its own copy of the database and does not share storage with other nodes. Data synchronization between nodes is done through replication or sharding mechanisms.

#### Advantages:
- No single point of failure in storage: If one node fails, the other nodes still have their own data.
- Better performance: Since there is no shared storage, each node can access its own data without queues or bottlenecks.

#### Disadvantages:
- Difficulty in maintaining data consistency: There must be a robust replication mechanism to ensure all nodes have up-to-date data.
- Longer failover time: If one node fails, other nodes may need to perform data recovery or reconciliation.

## 1.14 What is the purpose of interrupts? How does an interrupt differ from a trap? Can traps be generated intentionally by a user program? If so, for what purpose?

**Answer:**
### Purpose of Interrupts:
Interrupts are used to notify the CPU that a device or event requires attention so that the CPU can stop executing the current task and handle the more important event.

### Difference Between Interrupts and Traps:
- **Interrupts** usually come from hardware or unpredictable external events, such as a button being pressed or an I/O device being completed.
- **Traps**, on the other hand, are conditions generated by a program that cause the CPU to pause and handle the condition, such as division by zero or a system call.

### Can Traps Be Created Intentionally by User Programs?
Yes, traps can be created intentionally by user programs for specific purposes, such as to request operating system services, for example by using system calls.

## 1.15 Explain how the Linux kernel variables HZ and jiffies can be used to determine the number of seconds the system has been running since it was booted.

**Answer:**
- **HZ** is the number of timer interrupts that occur per second. The HZ value can vary depending on the system configuration.
- **Jiffies** is a count of the number of timer interrupts that have occurred since the system was booted.

### To find out how many seconds the system has been running since boot:
1. Count the number of jiffies (for example, if jiffies = 1,000,000).
2. Divide by HZ (for example, HZ = 1000 for 1000 interrupts per second).
3. The result is the time in seconds. For example, 1,000,000 jiffies ÷ 1000 HZ = 1,000 seconds since boot.

## 1.16 Direct memory access is used for high-speed I/O devices in order to avoid increasing the CPU's execution load.

### a. How does the CPU interface with the device to coordinate the transfer?
**Answer:**
The CPU configures the DMA controller with the destination memory address, data length, and source device. Once the DMA controller is set up, the CPU hands over control to the DMA controller which will perform the data transfer between the I/O device and memory without further CPU involvement.

### b. How does the CPU know when the memory operations are complete?
**Answer:**
The DMA controller will notify the CPU that the transfer is complete through an interrupt or some other mechanism, such as a status register.

### c. Does this process interfere with the execution of user programs?
**Answer:**
Generally, it does not interfere with the execution of user programs. Other programs can run on the CPU while the DMA controller performs the data transfer. However, interrupts that occur during transfers can interfere with program execution time if they occur too frequently or if the CPU has to handle too many interrupts.

## 1.17 Some computer systems do not provide a privileged mode of operation in hardware. Is it possible to construct a secure operating system for these computer systems? Give arguments both that it is and that it is not possible.

**Answer:**
### Possible:
An operating system can be built using software to restrict access and control, such as separating memory spaces for user and system programs, and using software-based access controls.

### Unlikely:
Without a privileged operating mode, the operating system would have difficulty protecting itself against untrusted programs and would rely heavily on software mechanisms for scripting, which could be more prone to failure.

If the hardware does not support a privileged operating mode, very careful software techniques and strict monitoring of memory and system resource access are required, but this can still have exploitable vulnerabilities.

## 1.18 Many SMP systems have different levels of caches; one level is local to each processing core, and another level is shared among all processing cores. Why are caching systems designed this way?

**Answer:**
The caching system in SMP (Symmetric Multiprocessing) architecture is designed with multiple levels to balance performance, scalability, and efficiency.

- **Local cache** (L1 and sometimes L2) is dedicated to each processing core, allowing very fast access to frequently used data without communication overhead between cores. This reduces latency and minimizes contention for shared resources.
- **Shared cache** (often L3) is accessible to all cores, allowing efficient data sharing and reducing redundant memory fetches from main memory.
  
This hierarchical approach helps reduce performance bottlenecks caused by frequent memory accesses while ensuring that commonly used data is available across cores when needed. In addition, this approach improves overall system throughput by reducing memory access conflicts and optimizing data locality, leading to better CPU utilization and energy efficiency.

## 1.19 Rank the following storage systems from slowest to fastest:
a.	Hard-disk drives
b.	Registers
c.	Optical disk
d.	Main memory
e.	Nonvolatile memory
f.	Magnetic tapes
g.	Cache

**Answer**
The order from slowest to fastest is:

- **f. Magnetic Tape**  
- **c. Optical Disk**  
- **a. Hard Disk Drive**  
- **e. Nonvolatile Memory**  
- **d. Main Memory**  
- **g. Cache**  
- **b. Register**  

## 1.20 Consider an SMP system similar to the one shown in Figure 1.8. Illustrate with an example how data residing in memory could in fact have a different value in each of the local caches.

**Answer:**
In a Symmetric Multiprocessing (SMP) system, each processor has a local cache that can cause data inconsistencies if the same data is accessed and modified without synchronization. 

**Example:** If CPU 1 and CPU 2 read variable `X = 10` from main memory into their respective caches, then CPU 1 changes `X` to `20` without updating it in memory or notifying CPU 2, then CPU 2 still sees `X = 10`, creating a cache coherence problem. 

To prevent this inconsistency, protocols such as **MESI (Modified, Exclusive, Shared, Invalid)** are used that ensure data alignment between caches.

## 1.21 Discuss, with examples, how the problem of maintaining coherence of cached data manifests itself in the following processing environments:

### a. Single-processor systems
**Answer:**
In a single-processor system, cache coherence problems arise when the same data is stored in multiple levels of cache (e.g., L1, L2, L3) and main memory.
**Example:** If the processor changes data in the L1 cache, the changes must be updated in the L2, L3, and main memory caches to keep the data consistent.
**Solution:** Simple cache coherence protocols, such as **write-through** or **write-back**, are used to ensure data consistency.
### b. Multiprocessor systems
**Answer:**
In multiprocessor systems, the cache coherence problem is more complex because multiple processors may access and modify the same data in their local caches.
**Example:** If two processors have copies of the same data in their local caches, and one processor modifies that data, the other processors must be notified of the change in order to keep their caches consistent.
**Solution:** More sophisticated cache coherence protocols, such as **MSI, MESI, or MOESI**, are used to track the cache state and ensure data consistency among all processors.
### c. Distributed systems
**Answer:**
In distributed systems, cache coherence problems arise when the same data is stored in different caches on different nodes in the network.
**Example:** If a user changes data in a web server’s cache, the changes must be updated in the other server’s caches and the client’s caches so that all users see the latest data.
**Solution:** Distributed cache coherence protocols, such as **cache invalidation** or **cache refresh**, are used to ensure data consistency across a distributed system.

## 1.22 Describe a mechanism for enforcing memory protection in order to prevent a program from modifying the memory associated with other programs.

**Answer:**  
Mechanisms for enforcing memory protection aim to prevent one program from accessing or changing memory owned by another program. One of the main ways to achieve this is by using virtual memory management, which allows the operating system to provide each program with an isolated memory space. Each program is assigned a separate virtual memory address, which is mapped to a different physical address in RAM. The operating system and memory management unit (MMU) ensure that each program can only access the memory it is authorized to, while attempts to access memory outside these boundaries will trigger error handling or access violation. In this way, this mechanism protects memory integrity between programs and prevents unauthorized data changes.

---

## 1.23 Which network configuration-LAN or WAN-would best suit the following environments?

### a. A campus student union  
**Answer:** This environment is best suited to a Local Area Network (LAN). LANs are designed to connect devices within a limited geographic area, such as a single building or campus. In a campus student union, most of the devices that need to connect are located in close proximity, so a LAN will provide a fast and efficient connection.

### b. Several campus locations across a statewide university system  
**Answer:** To connect multiple campus locations spread across a state, a Wide Area Network (WAN) is the right choice. WANs cover a large geographical area and allow communication between distant locations. In this case, the WAN will allow the exchange of data and resources between different campuses.

### c. A neighborhood  
**Answer:** For the surrounding environment, this can have two answers depending on how wide the "surrounding environment" is.
- If it is the environment around the house or office, then the most appropriate answer is LAN (Local Area Network).
- However, if it is the environment on a city scale or a wider area, then the answer is WAN (Wide Area Network).

---

## 1.24 Describe some of the challenges of designing operating systems for mobile devices compared with designing operating systems for traditional PCs.

**Answer:**  
Designing an operating system for mobile devices presents different challenges than for traditional PCs. Mobile devices have limitations in terms of battery life, storage capacity, and processing power, requiring more efficient resource management. Additionally, smaller screen sizes and touch-based input controls require simple, easy-to-use interface designs. Mobile devices also need to be able to function well even in unstable network conditions, such as when switching from Wi-Fi to cellular data. Meanwhile, traditional PCs have more processing power, storage space, and are more stable in terms of connectivity, allowing the operating system to focus more on multitasking capabilities and more demanding applications.

---

## 1.25 What are some advantages of peer-to-peer systems over client-server systems?

**Answer:**  
Peer-to-peer (P2P) systems offer several advantages over client-server systems. First, P2P systems are more robust because there is no central server; each node can act as both a client and a server. This eliminates a single point of failure, making the network more fault-tolerant. Second, P2P systems can be more cost-effective because they do not require expensive infrastructure or the maintenance of a centralized server. Third, P2P networks are highly scalable—adding more devices increases the overall capacity and resources of the network. Finally, P2P systems can offer faster data transfers in some cases, because data is exchanged directly between peers without having to route it through a central server, which can reduce latency and congestion.

---

## 1.26 Describe some distributed applications that would be appropriate for a peer-to-peer system.

**Answer:**  
1. **File Sharing:** Protocols like BitTorrent allow users to share large files efficiently by distributing the download across multiple peers. This reduces the load on any single server and increases download speeds.
2. **Content Delivery Networks (CDNs):** P2P technology can be used to create distributed CDNs, where users share cached content with each other. This can improve the performance of streaming video and other content-heavy applications.
3. **Cryptocurrencies:** Many cryptocurrencies, such as Bitcoin, rely on P2P networks to validate transactions and maintain the blockchain. This decentralized approach enhances security and transparency.
4. **Online Gaming:** P2P networks can be used to reduce latency in online games by allowing players to connect directly to each other. This can improve the gaming experience, especially for fast-paced games.

---

## 1.27 Identify several advantages and several disadvantages of open-source operating systems. Identify the types of people who would find each aspect to be an advantage or a disadvantage.

### **Advantages:**
- **Free and Affordable:** Many open-source operating systems are available for free, reducing the cost of software.  
  *User Type: Individuals on a budget, non-profit organizations, and educational institutions.*
- **Flexibility and Customization:** The available source code allows users to modify and customize the operating system to their needs.  
  *User Type: Software developers, system administrators, and advanced users who need complete control.*
- **Security:** A large developer community continually reviews and fixes security vulnerabilities.  
  *User Type: Individuals and organizations for whom data security is a priority.*

### **Disadvantages:**
- **Lack of Official Support:** Unlike commercial operating systems, open-source operating systems may not have official customer support.  
  *User Type: Users who need professional technical support.*
- **Hardware and Software Compatibility:** Some hardware and software may not be fully compatible with open-source operating systems.  
  *User Type: Users who need broad compatibility with specific hardware and software.*
- **Learning Curve:** Certain open-source operating systems may have a steeper learning curve for new users.  
  *User Type: Beginner users who do not have deep technical experience.*


