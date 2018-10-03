# Agent

1. Cert updates to newest on blueking server. And restart service.
2. Need add account "admin" to business-operation membership.
3. For install linux agent 

   Must  allow root login

   ```text
   vim /etc/ssh/sshd_config
   "PermitRootLogin yes"
   service sshd restart
   ```

4. Inbound , set both on PA and windows firewall and  iptables
5. ```text
   proxy to agent: port TCP:60020-60030 UDP：60020-60030 
   proxy to agent windows: port TCP:22,139,445,49154(wmiexec)
   ```
6. How to open 139,445 on windows

   ```bash
   #open TCP/IP Netbios and its service
   wmic nicconfig where TcpipNetbiosOptions=0 call SetTcpipNetbios 1
   wmic nicconfig where TcpipNetbiosOptions=2 call SetTcpipNetbios 1
   sc stop lmhosts
   sc start lmhosts
   #check: 
   netstat -ano | findstr "139" 
   netstat -ano | findstr "445"
   ```

7. admin$ need on P-Agent, set below and reboot to take effect.

   ```bash
   REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters /v AutoShareWks /t REG_DWORD /d 1 /f
   REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters /v AutoShareServer /t REG_DWORD /d 1 /f
   #after reboot, check show admin$
   net share
   ```

8. Test remote execute on proxy:

   ```bash
   #All P-agents's hostname-IP required in proxy's /etc/hosts
   cd /opt/py27/bin
   ./wmiexec.py -debug Administrator:password@P-Agent-Hostname 'dir C:\'
   ```

## After install 

1.Disable  root login on linux

2.Disable unnecessary rights on windows.

```
keep proxy to agent: port TCP:60020-60030 UDP：60020-60030 
#open TCP/IP Netbios and its service
wmic nicconfig where TcpipNetbiosOptions=0 call SetTcpipNetbios 2
wmic nicconfig where TcpipNetbiosOptions=1 call SetTcpipNetbios 2
sc stop lmhosts
sc start lmhosts
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters /v AutoShareWks /t REG_DWORD /d 0 /f
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters /v AutoShareServer /t REG_DWORD /d 0 /f

```



