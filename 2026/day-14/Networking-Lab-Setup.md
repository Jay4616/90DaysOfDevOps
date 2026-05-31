#Day 14: Networking & Troubleshooting Checklist
Understanding basic networking diagnostics is essential for identifying communication blocks, resolving latency issues, and keeping services connected on cloud infrastructure.

#🛠️ Practical Diagnostic Commands

# 1. Check local IP addresses and active interfaces
hostname -I
ip addr show

# 2. Test network layer connectivity and trace the routing path
ping -c 4 google.com
traceroute google.com

# 3. Inspect DNS resolution details and query nameservers
nslookup google.com
dig google.com

# 4. Audit active listening ports (TCP/UDP) with Process ID (PID) information
sudo ss -tulpn
sudo netstat -tulpn

# 5. Test application layer response and verify raw port socket connectivity
curl -I https://www.google.com
nc -zv google.com 443
