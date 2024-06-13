# bloqueador-ip-powershell-scriipt

### this bad boy here gonna block the url on your pc, it create a outbound rule on your fire wall that block the url site. 

run this at adm powershell

i dont think it works for any google plataform 


```shell
# Define the URL
$URL = "example.com"

# Resolve the URL to an IP address
$IP = [System.Net.Dns]::GetHostAddresses($URL) | Select-Object -ExpandProperty IPAddressToString

if ($IP) {
    # Block the IP address using Windows Firewall
    New-NetFirewallRule -DisplayName "Block $URL" -Direction Inbound -RemoteAddress $IP -Action Block
    New-NetFirewallRule -DisplayName "Block $URL" -Direction Outbound -RemoteAddress $IP -Action Block

    Write-Host "Blocked $URL ($IP)"
} else {
    Write-Host "Failed to resolve IP for $URL"
}

```
