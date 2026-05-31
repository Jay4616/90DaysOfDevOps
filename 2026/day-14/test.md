🛠 Networking & Troubleshooting Checklist (Bash)
🔍 Check local IP addresses
bash
# Shows all assigned IP addresses for the host
hostname -I

# Displays detailed interface info (IP, MAC, state)
ip addr show
🌐 Test network layer connectivity & route path
bash
# Send 4 ICMP echo requests to verify connectivity
ping -c 4 google.com

# Trace the route packets take to the destination
traceroute google.com
📡 Inspect DNS resolution details
bash
# Query DNS records using system resolver
nslookup google.com

# Perform detailed DNS lookup with record types
dig google.com
🔒 Check active listening ports (TCP/UDP) and PID/Program name
bash
# Show sockets with protocol, port, PID, and program
sudo ss -tulpn

# Legacy tool for listing active ports and processes
sudo netstat -tulpn
🧩 Test application layer and raw port connectivity
bash
# Fetch only HTTP headers to test web server response
curl -I https://www.google.com

# Check if a specific TCP port is reachable (verbose output)
nc -zv google.com 443
✨ Enhancements
🎨 Color-coded output
bash
# Example: wrap results with ANSI escape codes
echo -e "\e[32m✅ Success\e[0m"
echo -e "\e[31m❌ Failure\e[0m"
echo -e "\e[33m⚠️ Info\e[0m"
📝 Logging results
bash
# Append command output to a log file
ping -c 4 google.com | tee -a network_check.log
🤖 Interactive prompts
bash
# Ask user for domain or port dynamically
read -p "Enter domain to test: " domain
ping -c 4 "$domain"
⚙️ Run all checks in sequence
bash
# Combine everything into one script
./network-check.sh
