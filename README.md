<h1>PowerShell Commands</h1>

<h2>Objective</h2>
To understand how PowerShell operates and applying basic commands in a windows 11 environment<br>

<h2>Environment</h2>
<ul>
 <li>Windows </li>
 </ul>

<h2>Tasks Completed</h2>
<ul>
 <li>Applying PowerShell commands</li>
</ul>

<h2>Screenshots</h2>

<b>Get-Content</b> <b>Example:</b> Get-Content hosts.txt<br>

<b>Command used for:</b> Log analysis: firewall logs, Windows event exports, authentication logs, IOC lists<br>
                         Malware triage: encoded payloads, dropped scripts, persistence files<br>
                         Threat hunting: PowerShell history, scheduled task files, config files<br>

                         
<b>ForEach-Object: </b> <b>Example:</b> $hosts | ForEach-Object `{write-host $_ -backgroundColour white -foregroundcolour black}`<b>Example:</b> $hosts | ForEach-Object `{Write-Host "Hostname: $($_)" -BackgroundColor white -foreground black}`<br>

<b>Command used for:</b> Bulk scanning: IP addresses, usernames, hashes, hosts<br>
                         Threat hunting: Check multiple systems automatically<br>
                         IOC processing: Compare indicators against systems/logs<br>

<b>Out-file:</b> <b>Example:</b> "My name is nick" | out-file test.txt -Append <b>Example:</b> $hosts | ForEach-Object `{"Hostname: $($_)" | Out-file newfile.txt -Append}`

<b>Command used for:</b>Evidence collection: process lists, logs, scan results<br>
                        Reporting: Generate artifacts from scripts<br>
                        Automation: Store outputs for later analysis<br>

<p>
<img src= "https://github.com/NickHoward1/PowerShell-Commands-/blob/a01fb060128f33ef4aa0e5496e2de8179ec54938/Screenshot%202026-05-11%20at%2012.56.39.png" width="300" height="300"/> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src= "https://github.com/NickHoward1/PowerShell-Commands-/blob/5983ede86a5faf73188af4461bb1a9fb9512e7cc/Screenshot%202026-05-11%20at%2013.06.54.png" width="300" height="300"/> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src= "https://github.com/NickHoward1/PowerShell-Commands-/blob/dc8febddd1f0a955ce7872b1cf8520e6a84ec7e3/Screenshot%202026-05-11%20at%2013.33.43.png" width="300" height="300"/> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp
</p>

<b>Net Connection</b> <b>Example:</b> Test-NetConnection -ComputerName www.google.com <b>Example:</b> $hoststatus = Test-NetConnection -ComputerName www.google.com
$hoststatus | select * <b>Example:</b>Test-NetConnection -ComputerName www.google.com -port 443

<b>Command used for:</b> Port testing: open services, firewalls, connectivity
                         Internal recon: Discover reachable systems
                         Blue team diagnostics: VPN access, server exposure, segmentation rules

<b>Example:</b> $hosts | ForEach-Object `{ 
    Write-Host "Testing host: $($_)"
    Test-NetConnection -computerName $_ -Port 443
    Test-Netconnection -computerName $_ -Port 80
    Write-Host ""  
}`

<b>Command used for:</b> Port testing: open services, firewalls, connectivity
                         Internal recon: Discover reachable systems
                         Blue team diagnostics: VPN access, server exposure, segmentation rules
                         
<b>Convertto-json:</b>  <b>Example:</b> $hosts | convertto-json <b>Example:</b> $hosts[0] <b>Example:</b> $hosts[0] | select*

<b>Command used for:</b> SIEM integration: Splunk, Elastic, Sentinel
                         API communication: Security tools often use JSON APIs.
                         Structured evidence collection: process lists, network connections, IOC results

<b>Get-date:</b>  <b>Example:</b> 
$hosts | ForEach-Object `{ 
write-host "Testing Host: $($_)"
"$(get-date): Testing hOST $($_)." | Out-File host_test.log -Append
Test-NetConnection -ComputerName $_ -port 443
Test-NetConnection -ComputerName $_ -port 80
write-host ""
}`

<b>Command used for:</b> Logging: investigations, scans, incident response
                         Timeline analysis: attacks, logins, malware execution
                         Reporting: Track when evidence was collected.

<b>Start-Sleep:</b>  <b>Example:</b> 
$hosts | ForEach-Object `{
write-host "sleeping for 2 seconds..." -BackgroundColor Black -ForegroundColor Blue
start-sleep -seconds 2
write-host "Testing Host: $($_)"
"$(get-date): Testing host $($_)." | Out-File host_test.log -Append
Test-NetConnection -ComputerName $_ -port 443
write-host ""
}`

<b>Command used for:</b> Avoid detection: bypass rate limits, evade EDR heuristics, look less automated
                         Timing attacks: requests, scans, brute-force attempts
                         Malware behavior: beaconing, payload execution


<img src= "https://github.com/NickHoward1/PowerShell-Commands-/blob/874a91777073c06aae48d79ec84a88a829601f69/Screenshot%202026-05-11%20at%2014.58.19.png" width="300" height="300"/> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src= "https://github.com/NickHoward1/PowerShell-Commands-/blob/adca1c2a0574c15aa32e79453bf9945b6fbea7f2/Screenshot%202026-05-12%20at%2019.48.38.png" width="300" height="300"/> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src= "https://github.com/NickHoward1/PowerShell-Commands-/blob/60374dd733045f3c968eb6c91c1d5d0fdfa672ff/Screenshot%202026-05-12%20at%2020.09.00.png" width="300" height="300"/>

<b>Write-host:</b>  <b>Example:</b> write-host -BackgroundColor white -ForegroundColor Black "my name is Nick"

<b>Command used for:</b> Script feedback: pentest automation, recon scripts, scanning tools
                       
<b>Get Command:</b>  <b>Example:</b> get-command write*

<b>Command used for:</b> Enumeration: installed modules, offensive tools, admin utilities
                         Living off the land (LOLBins): Attackers look for built-in tools.
                         Learning environments: Find commands during labs/CTFs.

<b>Get Help:</b>  <b>Example:</b> get-help get-content -online

<b>Command used for:</b> Fast learning: exams, labs, incidents
                         Operator efficiency: Useful when working in unfamiliar environments.
                         Scripting: Learn parameters/options rapidly.


<h2>Real world scripting</h2>

Get-Content suspicious_ips.txt |
ForEach-Object `{
    Write-Host "Checking $_"
    Test-NetConnection $_ -Port 443
    Start-Sleep 1
}` | Out-File results.txt

<b>What this script does:</b> Reads IPs, Loops through them, Prints progress, Tests connectivity, Waits between checks, Saves results
                         
                     


