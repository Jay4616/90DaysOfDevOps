# 🛠 Networking & Troubleshooting Checklist (Bash)

## 🔍 Check local IP addresses
# Shows all assigned IP addresses for the host
hostname -I

# Displays detailed interface info (IP, MAC, state)
ip addr show

## 🌐 Test network layer connectivity & route path
# Send 4 ICMP echo requests to verify connectivity
ping -c 4 google.com

# Trace the route packets take to the destination
traceroute google.com

## 📡 Inspect DNS resolution details
# Query DNS records using system resolver
nslookup google.com

# Perform detailed DNS lookup with record types
dig google.com

## 🔒 Check active listening ports (TCP/UDP) and PID/Program name
# Show sockets with protocol, port, PID, and program
sudo ss -tulpn

# Legacy tool for listing active ports and processes
sudo netstat -tulpn

## 🧩 Test application layer and raw port connectivity
# Fetch only HTTP headers to test web server response
curl -I https://www.google.com

# Check if a specific TCP port is reachable (verbose output)
nc -zv google.com 443
