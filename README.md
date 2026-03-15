#!/bin/bash
# system_audit.sh - Basic Security Audit Script

echo "===== SYSTEM SECURITY AUDIT ====="
echo ""
echo "[*] Current User: $(whoami)"
echo "[*] Hostname: $(hostname)"
echo "[*] OS Info: $(uname -a)"
echo ""
echo "[*] Open Ports:"
netstat -tlnp 2>/dev/null || ss -tlnp
echo ""
echo "[*] Users with login shell:"
grep -v '/nologin\|/false' /etc/passwd
echo ""
echo "[*] SUID Files:"
find / -perm -4000 2>/dev/null
echo ""
echo "===== AUDIT COMPLETE ====="
