Objective
Configure and test firewall rules on a Windows machine using Windows Defender Firewall and PowerShell.

Tool Used
- Windows Defender Firewall with Advanced Security
- PowerShell

Steps Performed
1. Listed current firewall rules using PowerShell.
2. Created an inbound block rule for "port 23 (Telnet)".
3. Verified the port was blocked using "Test-NetConnection".
4. Created an inbound allow rule for "port 22 (SSH)".
5. Removed the block rule to restore original settings.

## Commands Used

powershell
- Get-NetFirewallRule | Where-Object { $_.Enabled -eq 'True' }
- New-NetFirewallRule -DisplayName "Block_Telnet_In" -Direction Inbound -Protocol TCP -LocalPort 23 -Action Block
- Test-NetConnection -ComputerName 127.0.0.1 -Port 23
- New-NetFirewallRule -DisplayName "Allow_SSH_In" -Direction Inbound -Protocol TCP -LocalPort 22 -Action Allow
- Remove-NetFirewallRule -DisplayName "Block_Telnet_In"
