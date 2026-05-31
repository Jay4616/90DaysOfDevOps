Day 14: Networking & Troubleshooting Checklist

Understanding basic networking diagnostics is essential for identifying communication blocks, resolving latency issues, and keeping services connected on cloud infrastructure.

This guide covers the essential commands to inspect local network configurations, test connection layers, and trace remote endpoint routing.

🛠️ Practical Diagnostic Commands

1. Check Local IP Addresses and Active Interfaces

Use these commands to verify your local IP configuration and inspect active network adapters.

# Display only the local IP addresses
hostname -I

# Show detailed statistics for all network interfaces
ip addr show


2. Test Network Layer Connectivity and Route Paths

Use these commands to check if an external host is reachable and trace the exact hops your data packets take to get there.

# Send 4 ICMP echo requests to verify connectivity
ping -c 4 google.com

# Trace the path packets take to reach the destination
traceroute google.com


3. Inspect DNS Resolution Details

Use these tools to verify if domain names are translating correctly to IP addresses through your DNS servers.

# Query the domain nameserver for basic IP translation
nslookup google.com

# Retrieve detailed DNS query records (A, MX, TXT, etc.)
dig google.com


4. Audit Active Listening Ports (TCP/UDP)

Check what services/programs are currently listening on your network ports, including their Process IDs (PID).

# Modern socket statistics tool (Recommended)
sudo ss -tulpn

# Legacy netstat tool (Fallback option)
sudo netstat -tulpn


5. Test Application Layer and Raw Port Connectivity

Test if a web page is responsive or verify if a specific port is accessible through firewalls.

# Fetch only the HTTP response headers from a server
curl -I [https://www.google.com](https://www.google.com)

# Scan a specific remote port to verify if it is open (port 443 is HTTPS)
nc -zv google.com 443
