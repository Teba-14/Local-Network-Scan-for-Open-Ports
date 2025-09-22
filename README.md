nmap, which stands for **Network Mapper**, is a powerful and versatile open-source tool used for network discovery and security auditing. It can be used to discover hosts and services on a computer network, thus creating a "map" of the network. Nmap is a popular tool among system administrators and security professionals alike.
### Basic Commands and Their Uses
* **Host Discovery**: Nmap can determine which hosts are available on a network.
    * `nmap [target]`
        * **Use**: Scans a single host to see if it's online.
        * **Example**: `nmap 192.168.1.1`
    * `nmap [subnet]`
        * **Use**: Scans an entire subnet to find active hosts.
        * **Example**: `nmap 192.168.1.0/24`
* **Port Scanning**: Nmap identifies open ports on a target host.
    * `nmap -sS [target]`
        * **Use**: Performs a **SYN scan** (stealth scan), which is fast and less likely to be logged by the target. This is the default scan type if a user has sufficient privileges.
    * `nmap -p [port_number] [target]`
        * **Use**: Scans a specific port or a range of ports.
        * **Example**: `nmap -p 80,443,22 192.168.1.1`
* **Service and Version Detection**: Nmap can identify the specific services and versions running on open ports.
    * `nmap -sV [target]`
        * **Use**: Scans and identifies the application and version number of the services running on the open ports. This is a crucial step for vulnerability assessment. 
* **Operating System Detection**: Nmap attempts to guess the operating system of the target machine.
    * `nmap -O [target]`
        * **Use**: Determines the operating system of the target host based on various network characteristics.
* **Aggressive Scan**: This scan type combines multiple features for a comprehensive scan.
    * `nmap -A [target]`
        * **Use**: Enables OS detection (`-O`), version detection (`-sV`), script scanning (`-sC`), and traceroute. This is a very thorough scan.
* **Script Scanning**: The **Nmap Scripting Engine (NSE)** allows users to write scripts to automate a wide variety of networking tasks.
    * `nmap -sC [target]`
        * **Use**: Runs a set of common, default scripts against the target.
    * `nmap --script=[script_name] [target]`
        * **Use**: Runs a specific Nmap script.
        * **Example**: `nmap --script=http-title 192.168.1.1`
* **Traceroute**: Nmap can trace the network path to a target.
    * `nmap --traceroute [target]`
        * **Use**: Maps the network path (hops) between the scanner and the target host.
### Common Nmap Flags
* `-v`: Increases the **verbosity** level, providing more detail about the scan's progress.
* `-T[0-5]`: Sets the **timing template** for the scan. `T4` is the default and considered the most practical, while `T5` is the fastest but can be less reliable and more easily detected. `T0` is the slowest, designed to evade intrusion detection systems.
* `-oA [file_name]`: Saves the scan output in three different formats (normal, XML, and grepable) to files with the specified name.
* `-n`: **No DNS resolution**. This speeds up the scan by preventing Nmap from performing reverse DNS lookups.
* `-sL`: **List scan**. Simply lists the hosts on the network without sending any packets to them, which can be useful for planning scans.
