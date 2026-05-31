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

SS:
<img width="1600" height="810" alt="image" src="https://github.com/user-attachments/assets/40d866f8-240a-48b7-836d-bef734e4f70e" />
<img width="1600" height="818" alt="image" src="https://github.com/user-attachments/assets/24ba85df-ca57-45a6-b3f7-2258dc912c50" />
<img width="1600" height="737" alt="image" src="https://github.com/user-attachments/assets/32a4fc38-e396-42b1-8984-63469659fc1b" />



