
# Advanced DevOps module

## System engineering

### What kind of virtualization technologies are you familiar with?

### What level of virtualization implementations are you familiar with?

### What command line text manipulation tools are you familiar with?

#### ==How would you create scheduled command command to run every sunday at midnight?==

To create a scheduled command that runs every Sunday at midnight, you can use the cron utility in Unix-like systems. Here's how you can set it up:

1. Open a terminal or shell session.

2. Type the following command to open the cron table for editing:

```bash
crontab -e
```

3. If prompted, select an editor to use for editing the cron table.

4. In the editor, add the following line to schedule the desired command to run every Sunday at midnight:

```plaintext
0 0 * * 0 command_to_run
```

In this line, the five fields represent the scheduling information:

- The first field `0` represents the minute (0-59).
- The second field `0` represents the hour (0-23).
- The third field `*` represents the day of the month (1-31).
- The fourth field `*` represents the month (1-12).
- The fifth field `0` represents the day of the week (0-7), where both 0 and 7 represent Sunday.

Replace `command_to_run` with the actual command you want to schedule.

5. Save the file and exit the editor.

The cron utility will now execute the scheduled command every Sunday at midnight. Make sure the system's time and timezone are correctly set for accurate execution.

Note: Different Unix-like systems may have slightly different cron syntax or ways to access the cron table. Consult your system's documentation or `man` pages for more specific instructions if needed.




#### ==How would you check the available free memories?==

To check the available free memory on a Unix-based system, you can use various commands depending on the specific Unix flavor. Here are a few commonly used commands:

1. `free` command:
   - Open a terminal and run the `free` command without any options.
   - This command displays the system's memory usage and availability.
   - The output provides information on total, used, and free memory in kilobytes (KB).
   - Here's an example output:

```
              total        used        free      shared  buff/cache   available
Mem:        2048000     1200000      248000       96000      600000      784000
Swap:        524288      120000      404288
```

In this example, the "free" column indicates the amount of available free memory.

2. `top` command:
   - Open a terminal and run the `top` command.
   - By default, `top` displays real-time system information, including memory usage.
   - Look for the line that starts with "Mem" or "KiB Mem" to find the memory information.
   - The "free" value represents the amount of available free memory.

3. `vmstat` command:
   - Open a terminal and run the `vmstat` command without any options.
   - This command displays virtual memory statistics, including information about memory usage.
   - Look for the "free" column, which represents the amount of available free memory.

It's worth noting that different Unix-based systems may have variations in the available commands or options. Therefore, you may need to consult the documentation or specific man pages of your Unix flavor for more detailed information on memory-related commands.



### ==How would you check the available free disk space on the computer?==

To check the available free disk space on a Linux computer, you can use the `df` command. Here's how you can do it:

Open a terminal and type the following command:

```
df -h
```

This will display the disk usage information in human-readable format with sizes in gigabytes (GB) or megabytes (MB) instead of the default kilobytes (KB).

The output will contain multiple rows, each representing a different file system or partition. The "Available" column shows the amount of free space on each partition.

Here's an example output:

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   20G   30G  40% /
/dev/sdb1       100G   50G   50G  50% /home
```

In this example, the root file system ("/") has 30 gigabytes (GB) of available space, and the "/home" partition has 50 GB of available space.

You can also use the `--total` option with `df` to get the overall summary of disk usage and free space across all partitions:

```
df -h --total
```

This will display a summary row at the bottom showing the total disk space, total used space, total available space, and the overall usage percentage.




### ==What are hard links and symbolic links?==


Hard links and symbolic links are both types of file system links used in operating systems to establish connections between files. However, they differ in how they function and the types of files they can link to.

1. Hard Links:
   - A hard link is a direct reference to a file or directory in the file system.
   - It creates a new file entry that points to the same underlying data as the original file.
   - All hard links to a file are essentially equal, and there is no concept of a "source" or "target" file.
   - Deleting a hard link does not affect the original file as long as other hard links exist.
   - Hard links cannot span across different file systems or partitions.

2. Symbolic Links (Soft Links):
   - A symbolic link, also known as a soft link, is a special type of file that references another file or directory by its path.
   - Instead of pointing directly to the original file's data, it contains the path to the target file or directory.
   - Symbolic links act as pointers or shortcuts to the target file or directory.
   - If the original file or directory is deleted or moved, the symbolic link becomes broken and cannot be resolved.
   - Symbolic links can span across different file systems or partitions.

In summary, hard links create additional file entries that reference the same underlying data, while symbolic links are files that contain references to other files or directories by their paths. Hard links cannot span across file systems, whereas symbolic links can. Additionally, deleting a hard link does not affect the original file, whereas deleting a symbolic link may break the link to the target file.


### ==How would you make a service auto-start and machine boot-up==

To make a service auto-start at machine boot-up in Linux, you generally need to perform the following steps:

1. Create a systemd service unit file: 
   - Open a text editor with root privileges (e.g., using `sudo` or `su`).
   - Create a new file with a `.service` extension in the `/etc/systemd/system/` directory. For example, `my-service.service`.
   - In this file, define the service by specifying its name, description, startup behavior, and the command to execute.
   - Here's an example of a basic service unit file:

```plaintext
[Unit]
Description=My Service
After=network.target

[Service]
ExecStart=/path/to/your/service/command

[Install]
WantedBy=default.target
```

Replace `/path/to/your/service/command` with the actual command or script that starts your service.

2. Save the service unit file and exit the text editor.

3. Enable the service:
   - In the terminal, run the following command with root privileges:

```bash
sudo systemctl enable my-service
```

Replace `my-service` with the name of your service unit file without the `.service` extension.

4. Start the service:
   - To start the service immediately, run the following command:

```bash
sudo systemctl start my-service
```

5. Verify the service status:
   - You can check the status of your service by running:

```bash
systemctl status my-service
```

This will display information about the service, including whether it is active (running) or not.

After completing these steps, your service should automatically start during the machine's boot-up process. You can also manually control the service using commands like `start`, `stop`, `restart`, and `status` with `systemctl`.


---


## Network engineering

#### ==What is a MAC address?==

A **media access control address** (**MAC address**) is a [unique identifier](https://en.wikipedia.org/wiki/Unique_identifier "Unique identifier") assigned to a [network interface controller](https://en.wikipedia.org/wiki/Network_interface_controller "Network interface controller") (NIC) for use as a [network address](https://en.wikipedia.org/wiki/Network_address "Network address") in communications within a [network segment](https://en.wikipedia.org/wiki/Network_segment "Network segment"). This use is common in most [IEEE 802](https://en.wikipedia.org/wiki/IEEE_802 "IEEE 802") networking technologies, including [Ethernet](https://en.wikipedia.org/wiki/Ethernet "Ethernet"), [Wi-Fi](https://en.wikipedia.org/wiki/Wi-Fi "Wi-Fi"), and [Bluetooth](https://en.wikipedia.org/wiki/Bluetooth "Bluetooth"). Within the [Open Systems Interconnection (OSI) network model](https://en.wikipedia.org/wiki/OSI_model "OSI model"), MAC addresses are used in the [medium access control](https://en.wikipedia.org/wiki/Medium_access_control "Medium access control") protocol sublayer of the [data link layer](https://en.wikipedia.org/wiki/Data_link_layer "Data link layer"). As typically represented, MAC addresses are recognizable as six groups of two [hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal "Hexadecimal") digits, separated by hyphens, colons, or without a separator.

MAC addresses are primarily assigned by device manufacturers, and are therefore often referred to as the **burned-in address**, or as an **Ethernet hardware address**, **hardware address**, or **physical address**. Each address can be stored in hardware, such as the card's [read-only memory](https://en.wikipedia.org/wiki/Read-only_memory "Read-only memory"), or by a [firmware](https://en.wikipedia.org/wiki/Firmware "Firmware") mechanism. Many network interfaces, however, support changing their MAC address. The address typically includes a manufacturer's [organizationally unique identifier](https://en.wikipedia.org/wiki/Organizationally_unique_identifier "Organizationally unique identifier") (OUI). MAC addresses are formed according to the principles of two numbering spaces based on extended unique identifiers (EUIs) managed by the [Institute of Electrical and Electronics Engineers](https://en.wikipedia.org/wiki/Institute_of_Electrical_and_Electronics_Engineers "Institute of Electrical and Electronics Engineers") (IEEE): **EUI-48**—which replaces the obsolete term **MAC-48**—and **EUI-64**.

---


#### ==What is the difference between binding to 127.0.0.1 or 0.0.0.0?==

**127.0.0.1 IP Address:**   
The IP address 127.0.0.1, also called loopback, is exclusively for localhost use. It is possible for computers to communicate with each other over an IP address, but this address cannot be used by computers to communicate with one another. A chance exists that the private IP address 192.168.1.115 is assigned to your computer so that it can connect to a router or networked device. A computer still has an alias of 127.0.0.1 in networking terms. Unlike loopback addresses, IP addresses are the connection between your computer and the network, not the connection between the computer and the loopback address. As an example: The web server on a particular operating system may declare 127.0.0.1 as the local hostname, so the pages can be run locally before they are deployed.

**0.0.0.0**  
In the past, it was used to indicate that there was no specific address to be directed to (a placeholder for ‘no specific address’) because the IP address is not routing. There are (IP) version 4 (IPv4) addresses ranging from 0.0.0.0 to 255.255.255.255. The IP address 0.0.0.0 has different meanings in different network environments. Addressing any device with this address, however, is not possible in general.

There is no route to the specified destination and the address is non-routable. If the message is viewed from a client or server device, its meaning may be different. Client and server devices are involved; the first is installed on the client device, while the second is embedded on the server device.

In the absence of an internet connection, the PC and other client devices usually display 0.0.0.0 as their IP address. Whenever a device is offline, it might be assigned this address by default. DHCP could also provide the address in case of failure. A device cannot be connected to any other device on the network using this address.

Devices can also be configured to use 0.0.0.0 as their subnet mask instead of their IP addresses. With this value, a subnet mask cannot be used. 0.0.0.0 is usually assigned to the IP address and network mask of a client computer.

0.0.0.0 is commonly used by firewall software and router software to block (or allow) all IP addresses.

Networking devices such as servers have a variety of network interfaces. TCP/IP software applications, which use 0.0.0.0 in their programming, analyze all network traffic on a multihomed device using all of the IP addresses assigned to the interfaces.

---


### ==What are the Layers of the OSI model?==

OSI layers “top down” from the application layer that directly serves the end user, down to the physical layer:

**7. Application Layer**

The application layer is used by end-user software such as web browsers and email clients. It provides protocols that allow software to send and receive information and present meaningful data to users. A few examples of application layer protocols are the [Hypertext Transfer Protocol](https://www.imperva.com/learn/performance/http2/) (HTTP), File Transfer Protocol (FTP), Post Office Protocol (POP), Simple Mail Transfer Protocol (SMTP), and Domain Name System (DNS).

**6. Presentation Layer**

The presentation layer prepares data for the application layer. It defines how two devices should encode, encrypt, and compress data so it is received correctly on the other end. The presentation layer takes any data transmitted by the application layer and prepares it for transmission over the session layer.

**5. Session Layer**

The session layer creates communication channels, called sessions, between devices. It is responsible for opening sessions, ensuring they remain open and functional while data is being transferred, and closing them when communication ends. The session layer can also set checkpoints during a data transfer—if the session is interrupted, devices can resume data transfer from the last checkpoint.

**4. Transport Layer**

The transport layer takes data transferred in the session layer and breaks it into “segments” on the transmitting end. It is responsible for reassembling the segments on the receiving end, turning it back into data that can be used by the session layer. The transport layer carries out flow control, sending data at a rate that matches the connection speed of the receiving device, and error control, checking if data was received incorrectly and if not, requesting it again.

**3. Network Layer**

The network layer has two main functions. One is breaking up segments into network packets, and reassembling the packets on the receiving end. The other is routing packets by discovering the best path across a physical network. The network layer uses network addresses (typically Internet Protocol addresses) to route packets to a destination node.

**2. Data Link Layer**

The data link layer establishes and terminates a connection between two physically-connected nodes on a network. It breaks up packets into frames and sends them from source to destination. This layer is composed of two parts—Logical Link Control (LLC), which identifies network protocols, performs error checking and synchronizes frames, and Media Access Control (MAC) which uses MAC addresses to connect devices and define permissions to transmit and receive data.

**1. Physical Layer**

The physical layer is responsible for the physical cable or wireless connection between network nodes. It defines the connector, the electrical cable or wireless technology connecting the devices, and is responsible for transmission of the raw data, which is simply a series of 0s and 1s, while taking care of bit rate control.

---


#### ==What is the difference between a router and switch?==

Routers and switches are both networking devices used in computer networks, but they serve different purposes and operate at different levels of the network.

1. Router:
   - A router is a networking device that operates at the network layer (Layer 3) of the OSI model.
   - It connects multiple networks (LANs or WANs) and forwards data packets between them based on IP addresses.
   - Routers determine the optimal path for data transmission using routing protocols and maintain routing tables.
   - They provide features like network address translation (NAT), firewall capabilities, and support for dynamic routing protocols.
   - Routers can perform traffic filtering, network segmentation, and handle the exchange of routing information between networks.
   - In home or small office networks, a router often combines functionalities of a router, switch, and wireless access point.

2. Switch:
   - A switch is a networking device that operates at the data link layer (Layer 2) of the OSI model.
   - It connects multiple devices within a local network (LAN) and facilitates communication between them.
   - Switches use MAC (Media Access Control) addresses to forward data packets between devices within the same network.
   - They build and maintain a MAC address table to track which devices are connected to each switch port.
   - Switches can provide multiple ports, allowing simultaneous communication between devices at wire speed.
   - They offer high-speed and low-latency data transfer within a LAN and support features like VLANs (Virtual LANs) for network segmentation.

In summary, routers connect multiple networks at the network layer and forward data based on IP addresses, while switches connect devices within a local network at the data link layer using MAC addresses. Routers operate at a higher level and are responsible for directing traffic between networks, while switches facilitate communication within a network by connecting devices together.


#### ==What is a Router?==

Routers are network connecting devices that determine the shortest path for a packet to take to get to its destination. A router's primary function is to connect multiple networks at once.

Routers work on the OSI (Open Systems Interconnection) architecture's network, physical, and data link layers.

Routers, unlike firewalls, do not encrypt networks prior to routing them. Routers do not protect the network from threats, but they do include a capability that allows many networks to share an Internet connection.


#### ==How Does a Router Work?==

Two or more data connections from distinct IP networks are linked to a router. When a data packet arrives on one of the lines, the router looks at the network address information in the packet header to figure out where it should go. Using the information in its routing table or routing policy, the packet is then directed to the next network on its path.

-   A router determines a packet's destination or target IP address, and forwarding tables and headers determine the best way for transmitting the packet.
-   A packet is passed from one router to the next via the networks that make up an internetwork (such as the Internet) until it arrives at its destination node.
-   Routers are most commonly used in the local area network (LAN) and wide area network (WAN) domains.
-   Routing protocols are used to transport data across the network.

Routers are far more expensive than other network equipment such as hubs, switches, and routers. D-Link, Cisco, and Nortel are some of the companies that manufacture routers.



#### ==What is a Switch?==

A switch is essentially a piece of hardware or a device that is responsible for routing data from multiple input ports to a certain output port, which then sends the data to its final destination. As a result, it is mostly utilized to transmit data packets between various network devices such as routers and servers.

-   A switch is a data connection layer (layer 2 d) gadget. It guarantees that the data packets being sent are correct and free from errors.
-   In order to forward the data to the data link layer, the switch uses the MAC address.
-   A switch is also known as a **multiport bridge** since it accepts data from several ports.
-   A switch is a device that is used to forward electrical or optical signals. Any two network nodes that reach the switch have their own electrical signal channel.
-   A switch includes several ports, each of which may be linked to a LAN or a high-performance server or workstation through a bridge function.

---


#### ==What is the difference between TCP and UDP?==

| **Basis** | **Transmission control protocol (TCP)** | **User datagram protocol (UDP)** |
| --- | --- | --- |
| **Type of Service** | [TCP](https://www.geeksforgeeks.org/what-is-transmission-control-protocol-tcp/) is a connection-oriented protocol. Connection-orientation means that the communicating devices should establish a connection before transmitting data and should close the connection after transmitting the data. | [UDP](https://www.geeksforgeeks.org/user-datagram-protocol-udp/) is the Datagram-oriented protocol. This is because there is no overhead for opening a connection, maintaining a connection, and terminating a connection. UDP is efficient for broadcast and multicast types of network transmission. |
| **Reliability** | TCP is reliable as it guarantees the delivery of data to the destination router. | The delivery of data to the destination cannot be guaranteed in UDP. | **
| **Error checking mechanism** | TCP provides extensive error-checking mechanisms. It is because it provides flow control and acknowledgment of data. | UDP has only the basic error checking mechanism using checksums. |
| **Acknowledgment** | An acknowledgment segment is present. | No acknowledgment segment.
| **Sequence** | Sequencing of data is a feature of Transmission Control Protocol (TCP). this means that packets arrive in order at the receiver.| There is no sequencing of data in UDP. If the order is required, it has to be managed by the application layer.
| **Speed** | TCP is comparatively slower than UDP. | UDP is faster, simpler, and more efficient than TCP.
| **Retransmission** | Retransmission of lost packets is possible in TCP, but not in UDP. | There is no retransmission of lost packets in the User Datagram Protocol (UDP).
| **Header Length** | TCP has a (20-60) bytes variable length header. | UDP has an 8 bytes fixed-length header.
| **Weight** | TCP is heavy-weight. | UDP is lightweight.
| **Handshaking Techniques** | Uses handshakes such as SYN, ACK, SYN-ACK | It’s a connectionless protocol i.e. No handshake
| **Broadcasting** | TCP doesn’t support Broadcasting. | UDP supports Broadcasting.
| **Protocols** | TCP is used by [HTTP, HTTPs](https://www.geeksforgeeks.org/difference-between-http-and-https-2/), [FTP](https://www.geeksforgeeks.org/file-transfer-protocol-ftp/), [SMTP](https://www.geeksforgeeks.org/simple-mail-transfer-protocol-smtp/) and [Telnet](https://www.geeksforgeeks.org/introduction-to-telnet/). | UDP is used by [DNS](https://www.geeksforgeeks.org/details-on-dns/), [DHCP](https://www.geeksforgeeks.org/dynamic-host-configuration-protocol-dhcp/), TFTP, [SNMP](https://www.geeksforgeeks.org/simple-network-management-protocol-snmp/), [RIP](https://www.geeksforgeeks.org/routing-information-protocol-rip/), and [VoIP](https://www.geeksforgeeks.org/voice-over-internet-protocol-voip/).
| **Stream Type** | The TCP connection is a byte stream. | UDP connection is message stream.
| **Overhead** | Low but higher than UDP. | Very low.

---


#### ==What is a VPN?==

A virtual private network, or VPN, is a service that creates an encrypted tunnel to transmit data over the internet while ensuring the user’s online privacy and protecting sensitive data. Unlike [website security](https://www.wix.com/blog/2022/01/website-security/) tools used by site owners to protect visitors’ information on certain pages, VPNs keep users secure through their entire online journey by hiding their [IP address](https://www.wix.com/encyclopedia/definition/ip-internet-protocol-address) in order to make any action virtually untraceable.

---


#### ==What is DNS?==

The domain name system (DNS) is a naming database in which internet [domain](https://www.techtarget.com/whatis/definition/domain) names are located and translated into [Internet Protocol (IP) addresses](https://www.techtarget.com/whatis/definition/IP-address-Internet-Protocol-Address). The domain name system maps the name people use to locate a website to the IP address that a computer uses to locate that website.

For example, if someone types "example.com" into a web browser, a server behind the scenes maps that name to the corresponding IP address. An IP address is similar in structure to 203.0.113.72.

Web browsing and most other internet activities rely on DNS to quickly provide the information necessary to connect users to remote hosts. DNS mapping is distributed throughout the internet in a hierarchy of authority. [Access providers](https://www.techtarget.com/whatis/definition/access-provider) and enterprises, as well as governments, universities and other organizations, typically have their own assigned ranges of IP addresses and an assigned domain name. They also typically run DNS servers to manage the mapping of those names to those addresses. Most Uniform Resource Locators (URLs) are built around the domain name of the web server that takes client requests.


---


#### ==What is DHCP?==

Dynamic Host Configuration Protocol (DHCP) is a network management protocol used to automate the process of configuring devices on IP networks, thus allowing them to use network services such as DNS, NTP, and any communication protocol based on UDP or TCP. A DHCP server dynamically assigns an IP address and other network configuration parameters to each device on a network so they can communicate with other IP networks. DHCP is an enhancement of an older protocol called BOOTP. DHCP is an important part of the [DDI solution](https://www.efficientip.com/solutions/smart-ddi/) (DNS-DHCP-IPAM).

---


#### ==What is a VPC==

A **virtual private cloud (VPC)** is an on-demand configurable pool of [shared resources](https://en.wikipedia.org/wiki/Shared_resources "Shared resources") allocated within a **public** [cloud](https://en.wikipedia.org/wiki/Cloud_computing "Cloud computing") environment, providing a certain level of isolation between the different organizations (denoted as _users_ hereafter) using the resources. The isolation between one VPC user and all other users of the same cloud (other VPC users as well as other public cloud users) is achieved normally through allocation of a private IP subnet and a virtual communication construct (such as a [VLAN](https://en.wikipedia.org/wiki/VLAN "VLAN") or a set of [encrypted communication](https://en.wikipedia.org/wiki/Encrypted_communication "Encrypted communication") channels) per user. In a VPC, the previously described mechanism, providing isolation within the cloud, is accompanied with a [virtual private network](https://en.wikipedia.org/wiki/Virtual_private_network "Virtual private network") (VPN) function (again, allocated per VPC user) that secures, by means of authentication and encryption, the remote access of the organization to its VPC resources. With the introduction of the described isolation levels, an organization using this service is in effect working on a '**virtually private'** cloud (that is, as if the cloud infrastructure is not shared with other users), and hence the name VPC.

VPC is most commonly used in the context of cloud [infrastructure as a service](https://en.wikipedia.org/wiki/Infrastructure_as_a_service "Infrastructure as a service"). In this context, the infrastructure provider, providing the underlying public cloud infrastructure, and the provider realizing the VPC service over this infrastructure, may be different vendors.

---


## Security engineering

#### ==In what AWS service can you store sensitive data?==

In Amazon Web Services (AWS), there are multiple services that can be used to store sensitive data securely. Here are a few AWS services commonly used for storing sensitive data:

1. AWS Secrets Manager:
   - AWS Secrets Manager is a service specifically designed for storing and managing sensitive information such as database credentials, API keys, and other secrets.
   - It provides a central location to securely store and retrieve secrets, eliminating the need to hardcode or manage secrets directly in applications.
   - Secrets Manager offers encryption at rest and in transit, integration with AWS Identity and Access Management (IAM) for access control, and automatic rotation of secrets for enhanced security.

2. AWS Key Management Service (KMS):
   - AWS Key Management Service (KMS) is a managed service for creating and controlling the encryption keys used to encrypt data in other AWS services and applications.
   - KMS enables you to encrypt sensitive data before storing it in other AWS services such as Amazon S3 or Amazon EBS.
   - It provides key management features, including key creation, rotation, and auditing, ensuring the security and compliance of your data.

3. Amazon S3 (Simple Storage Service):
   - Amazon S3 is an object storage service that allows you to store and retrieve large amounts of data.
   - S3 provides built-in features to secure your data, including access control policies, server-side encryption, and integration with AWS Identity and Access Management (IAM) for fine-grained access control.
   - You can encrypt your sensitive data in S3 using AWS KMS-managed keys or your own encryption keys.

4. Amazon RDS (Relational Database Service):
   - Amazon RDS is a managed database service that supports various database engines, including MySQL, PostgreSQL, Oracle, and SQL Server.
   - RDS provides encryption at rest for database storage, allowing you to encrypt your sensitive data stored in RDS using AWS KMS-managed keys.
   - It also offers additional security features such as automated backups, database snapshots, and secure network access control.

These are just a few examples of AWS services that can be used to store sensitive data securely. The choice of the service depends on the specific requirements of your application and the nature of the sensitive data you need to store. It's recommended to review the documentation and security best practices provided by AWS for each service to ensure proper configuration and protection of your sensitive data.


#### ==What network topology is good for hiding EC2?==

If you want to hide your EC2 instances from direct access on the internet, you can utilize a private network topology. A few network topology options that can help achieve this goal are:

1. Virtual Private Cloud (VPC) with Private Subnets:
   - AWS Virtual Private Cloud (VPC) allows you to create a virtual network in the AWS cloud.
   - Configure your VPC with private subnets that do not have direct internet access.
   - Place your EC2 instances in these private subnets to isolate them from the public internet.
   - Access to these instances can be controlled through bastion hosts or VPN connections.

2. VPC with Network Address Translation (NAT) Gateway:
   - Create a VPC with both public and private subnets.
   - Place your EC2 instances in the private subnet, which does not have internet gateway attached.
   - Deploy a NAT Gateway or NAT instance in the public subnet, which allows the private instances to access the internet for necessary updates or external communication.

3. VPC Peering:
   - Establish VPC peering connections between different VPCs.
   - Place your EC2 instances in a separate VPC, which is not directly accessible from the internet.
   - Use VPC peering to establish connectivity between this private VPC and other VPCs that have internet access.

4. VPN Connections:
   - Set up a VPN connection between your on-premises network or remote location and the VPC.
   - This allows you to access your EC2 instances securely through an encrypted VPN tunnel.
   - The EC2 instances can be placed in private subnets that are not directly accessible from the internet.

By implementing these network topology options, you can effectively hide your EC2 instances from direct access on the internet and enforce controlled access to them through secure network connections or internal networks. The specific choice of topology depends on your specific requirements and the level of isolation you need for your EC2 instances.




#### ==How those EC2 called which are serving as a single entry point for accessing protected resource on a restricted network?==

The EC2 instances that serve as a single entry point for accessing protected resources on a restricted network are commonly referred to as bastion hosts or jump boxes.

A bastion host, also known as a jump box, is a special-purpose server or instance that is placed in a publicly accessible subnet of a network, often in a demilitarized zone (DMZ) or a separate security group. Its primary purpose is to provide secure access to other resources within a restricted or private network.

Here's how a bastion host typically functions:

1. Secure Access Point: The bastion host acts as a secure access point from the public internet into the private network. It is accessible from the internet, typically via SSH or RDP, and provides a gateway for authorized users to connect to other resources within the restricted network.

2. Access Control and Authentication: The bastion host enforces access control and authentication mechanisms to ensure only authorized users can connect. This may involve key-based authentication, multi-factor authentication (MFA), or other security measures to verify the identity of the connecting users.

3. Traffic Filtering and Security: The bastion host often has strict security measures implemented, such as firewall rules, intrusion detection and prevention systems, and logging. These measures help protect the restricted network from unauthorized access and potential security threats.

4. Proxy or Tunneling: Once connected to the bastion host, users can establish secure connections or tunnels to other resources within the restricted network. This allows them to access and manage the protected resources indirectly, without exposing them directly to the internet.

By utilizing a bastion host, organizations can strengthen the security of their restricted networks by adding an additional layer of access control and isolation. It provides a controlled and monitored entry point for authorized users to access protected resources while protecting them from direct exposure to the public internet.



#### ==What AWS service is responsible for monitoring and log collection?==

The AWS service responsible for monitoring and log collection is Amazon CloudWatch.

Amazon CloudWatch provides a centralized monitoring and observability solution for your AWS resources and applications. It offers a wide range of monitoring capabilities, including metrics, logs, events, and dashboards. Here's how CloudWatch handles monitoring and log collection:

1. Metrics:
   - CloudWatch collects and stores metrics, which are numeric data points related to the performance and behavior of your AWS resources.
   - You can monitor various AWS services and custom applications by collecting and analyzing metrics such as CPU utilization, network traffic, or request latency.
   - CloudWatch provides pre-built dashboards and allows you to create custom dashboards to visualize and monitor these metrics.

2. Logs:
   - CloudWatch Logs enables you to collect, monitor, and store logs from your AWS resources and applications.
   - It allows you to stream log data in real-time and store it durably for long-term retention.
   - You can capture logs from various sources, including EC2 instances, Lambda functions, AWS services, and custom applications.
   - CloudWatch Logs can be used to centralize log collection, troubleshoot issues, perform analysis, and set up alarms based on log events.

3. Events:
   - CloudWatch Events provides event-driven monitoring for AWS resources and services.
   - It allows you to respond to changes and events happening in your environment by triggering actions.
   - You can create rules to match specific events and trigger actions such as launching an EC2 instance, invoking a Lambda function, or sending a notification.

4. Alarms and Actions:
   - CloudWatch Alarms enable you to set thresholds on metrics and trigger actions when those thresholds are breached.
   - You can create alarms to monitor specific metrics and take automated actions such as sending notifications, triggering Auto Scaling, or executing AWS Lambda functions.

In summary, Amazon CloudWatch is the AWS service responsible for monitoring and log collection. It offers a comprehensive set of tools to monitor metrics, collect and analyze logs, and set up alarms and automated actions for your AWS resources and applications.



#### ==What AWS service is responsible for tracking activites on the account?==

The AWS service responsible for tracking activities on an AWS account is AWS CloudTrail.

AWS CloudTrail is a service that enables you to monitor, log, and retain account activity related to actions taken within your AWS infrastructure. It provides a detailed history of API calls made by users, roles, or AWS services in your account. Here are the key features and functionalities of AWS CloudTrail:

1. Activity Logging: CloudTrail logs API calls made to various AWS services, including changes to resources, security-related events, and management operations. It captures important information such as the identity of the caller, the time of the call, the source IP address, and more.

2. Account-Level Logging: CloudTrail tracks activity across the entire AWS account, including all regions. It captures events related to AWS Management Console, AWS CLI, SDKs, and other AWS services.

3. Event History: CloudTrail provides a comprehensive event history that can be searched and analyzed. You can view and download event logs for specific time frames or perform searches based on specific criteria.

4. Integration with Other Services: CloudTrail can integrate with other AWS services, such as AWS CloudWatch, AWS S3, and AWS Lambda. You can configure CloudTrail to deliver log files to S3 for long-term storage or trigger actions based on specific events using CloudWatch Alarms or Lambda functions.

5. Compliance and Auditing: CloudTrail helps meet auditing and compliance requirements. It provides an audit trail that can be used for security analysis, resource change tracking, troubleshooting, and compliance reporting. It can be particularly useful for demonstrating compliance with regulatory standards like PCI DSS, HIPAA, and GDPR.

6. Security Analysis: CloudTrail logs can be used for security analysis and monitoring. By analyzing the recorded API calls, you can detect unusual activity, identify potential security threats, and investigate any suspicious behavior.

In summary, AWS CloudTrail is the service responsible for tracking activities on an AWS account. It provides a detailed history of API calls made within the AWS infrastructure, enabling auditing, compliance, security analysis, and troubleshooting.

#### ==What is the difference between SG and NACL?==

In AWS, SG (Security Group) and NACL (Network Access Control List) are both used for network security, but they operate at different layers and have distinct functionalities. Here are the key differences between Security Groups and Network Access Control Lists:

1. Layer of Operation:
   - Security Groups (SGs) operate at the instance level or the Elastic Network Interface (ENI) level. They are associated with EC2 instances and control inbound and outbound traffic at the transport (Layer 4) and application (Layer 7) layers of the OSI model.
   - Network Access Control Lists (NACLs) operate at the subnet level. They are associated with subnets and control inbound and outbound traffic at the network (Layer 3) layer of the OSI model.

2. Stateful vs. Stateless:
   - Security Groups are stateful. If you allow inbound traffic, the return traffic is automatically allowed, simplifying the configuration. For example, if you allow inbound HTTP traffic, the corresponding outbound HTTP traffic is allowed.
   - Network Access Control Lists are stateless. You must explicitly allow inbound and outbound rules separately, as return traffic is not automatically allowed.

3. Rule Evaluation:
   - Security Group rules are evaluated in a first-match basis. If a rule matches, it is applied, and subsequent rules are not evaluated.
   - Network Access Control List rules are evaluated in a numbered order. Each rule is evaluated, and the rule number determines the order of evaluation. The rule with the lowest number that matches is applied, and further rules may be evaluated.

4. Rule Flexibility:
   - Security Groups allow you to define rules based on specific IP addresses, CIDR blocks, or other security groups within the same VPC. You can create granular rules based on ports, protocols, and source/destination IP ranges.
   - Network Access Control Lists provide a broader range of options for allowing or denying traffic, including IP addresses, CIDR blocks, port ranges, and protocol numbers.

5. Scope:
   - Security Groups are applicable within a VPC and operate at the instance level or ENI level.
   - Network Access Control Lists are applied at the subnet level and affect all traffic in and out of the subnet.

In summary, Security Groups are stateful, operate at the instance level, and provide granular control over inbound and outbound traffic at the transport and application layers. Network Access Control Lists are stateless, operate at the subnet level, and control inbound and outbound traffic at the network layer. Understanding the differences between Security Groups and Network Access Control Lists helps in implementing effective network security in AWS environments.


#### ==What is the difference between KMS and HSM?==

KMS (Key Management Service) and HSM (Hardware Security Module) are both cryptographic solutions used for securing keys and performing cryptographic operations, but they differ in their implementations and use cases. Here are the key differences between KMS and HSM:

1. Implementation:
   - KMS: KMS is a managed service provided by cloud service providers like AWS. It is a software-based solution that runs on shared infrastructure managed by the service provider. KMS abstracts the underlying hardware and provides a secure key management and encryption service.
   - HSM: HSM is a physical hardware device designed specifically for cryptographic operations. It is a dedicated and tamper-resistant hardware device that provides a secure environment for key management and cryptographic functions. HSMs are typically deployed on-premises or in dedicated data centers.

2. Key Management:
   - KMS: KMS provides a managed key management service where keys are stored, managed, and protected by the cloud service provider. It offers features like key rotation, auditing, and integration with other cloud services.
   - HSM: HSMs offer a dedicated and secure hardware environment for key management. Keys are generated, stored, and managed within the HSM, providing a higher level of physical and logical security.

3. Cryptographic Operations:
   - KMS: KMS primarily focuses on key management and provides an interface to perform various cryptographic operations, such as encryption, decryption, signing, and verification. These operations are performed using the keys managed by KMS.
   - HSM: HSMs excel in performing cryptographic operations securely. They provide a hardware-accelerated environment for operations like encryption, decryption, signing, hashing, and random number generation. HSMs are designed to protect sensitive keys and perform these operations with high-performance and strong security guarantees.

4. Deployment and Scalability:
   - KMS: KMS is a scalable and managed service provided by cloud service providers. It offers a highly available and resilient infrastructure for key management and cryptographic operations. The service can scale to handle varying workloads and demands.
   - HSM: HSMs are physical hardware devices that require deployment on-premises or in dedicated data centers. They are typically deployed in a clustered or redundant configuration for high availability. Scaling HSM capacity may involve adding more physical devices.

5. Compliance and Certifications:
   - KMS: KMS is built on industry best practices and undergoes regular security audits and certifications. It provides compliance with various standards, such as SOC, PCI DSS, and HIPAA. The compliance responsibility is shared with the cloud service provider.
   - HSM: HSMs are designed to meet strict compliance requirements and are often used in highly regulated industries. They are certified against industry standards such as FIPS 140-2 and Common Criteria.

In summary, KMS is a managed key management service provided by cloud service providers, while HSMs are physical hardware devices dedicated to cryptographic operations and key management. KMS offers a scalable and abstracted solution for key management, while HSMs provide a dedicated and highly secure hardware environment for cryptographic operations. The choice between KMS and HSM depends on the specific security requirements, compliance needs, and performance considerations of the application or organization.

---


## Application

### What is the difference between Docker and Virtual Machine?

### What is the keyworld for defining the base image of a Dockerfile?

#### What is the difference between CMD and ENTRYPOINT?

#### What is the layout of a minimal Kubernetes deployment?

#### What is the difference between Deployment and StatefulSet kubernetes object?

#### What is a Service kubernetes object responsible for?

#### How can be a kubernetes pod reached from the public internet?

#### What is the difference between LivenessProbe and ReadinessProbe?

#### What is the difference between resource Limit and Request?

---

## Release Engineer

#### What is the Git Flow?

#### What is Continuous Integration, Delivery, Deployment?

#### What are the Jenkins Agents?

#### What keywords can be used in Gitlab to start a sidecar container during the build?

#### How can you create parallel build jobs in Gitlab CI?
