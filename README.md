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

<b>ForEach-Object: </b> <b>Example:</b> $hosts | ForEach-Object `{write-host $_ -backgroundColour white -foregroundcolour black}`<b>Example:</b> $hosts | ForEach-Object `{Write-Host "Hostname: $($_)" -BackgroundColor white -foreground black}`<br>

<b>Out-file:</b> <b>Example:</b> "My name is nick" | out-file test.txt -Append <b>Example:</b> $hosts | ForEach-Object `{"Hostname: $($_)" | Out-file newfile.txt -Append}`


<p>
<img src= "https://github.com/NickHoward1/PowerShell-Commands-/blob/a01fb060128f33ef4aa0e5496e2de8179ec54938/Screenshot%202026-05-11%20at%2012.56.39.png" width="300" height="300" /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<img src= "https://github.com/NickHoward1/PowerShell-Commands-/blob/5983ede86a5faf73188af4461bb1a9fb9512e7cc/Screenshot%202026-05-11%20at%2013.06.54.png" width="300" height="300"/> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src= "https://github.com/NickHoward1/PowerShell-Commands-/blob/dc8febddd1f0a955ce7872b1cf8520e6a84ec7e3/Screenshot%202026-05-11%20at%2013.33.43.png" width="300" height="300" /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src= "https://github.com/NickHoward1/PowerShell-Commands-/blob/1dba6922505897c101fa455a77b98cf5f34e7848/Screenshot%202026-05-11%20at%2014.41.22.png" width="300" height="300"/> 
</p>

<b>Net Connection</b> <b>Example:</b> Test-NetConnection -ComputerName www.google.com <b>Example:</b> $hoststatus = Test-NetConnection -ComputerName www.google.com
$hoststatus | select * <b>Example:</b>Test-NetConnection -ComputerName www.google.com -port 443

<b>Example:</b> $hosts | ForEach-Object `{ 
    Write-Host "Testing host: $($_)"
    Test-NetConnection -computerName $_ -Port 443
    Test-Netconnection -computerName $_ -Port 80
    Write-Host ""  
}`

<b>Convertto-json:</b>  <b>Example:</b $hosts | convertto-json <b>Example:</b $hosts[0] <b>Example:$hosts[0] | select*

<b>Get-date:</b>  <b>Example:</b


<img src= "https://github.com/NickHoward1/PowerShell-Commands-/blob/874a91777073c06aae48d79ec84a88a829601f69/Screenshot%202026-05-11%20at%2014.58.19.png" width="300" height="300" /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<img src= ""/> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <img src= "" />

<h2>Outcomes</h2>
