# Set up a profile

A profile is a script that runs when you start a new session. Having a customized environment can make you more productive.

1. Enter `pwsh` in a terminal window to start a PowerShell session:
```powershell
pwsh
```

2. run this command:
```powershell
$Profile | Select-Object *
```
The output will look like this:
```powershell
CurrentUserAllHosts                        CurrentUserCurrentHost
-------------------                        ----------------------
/home/<user>/.config/PowerShell/profile.ps1 /home/<user>/.config/PowerShell/Microsoft.…
```

3. Create a profile for the current user and the current host by running the command New-Item
```powershell
New-Item -ItemType "file" -Value 'Write-Host "Hello <replace with your name>, welcome back" -foregroundcolor Green ' -Path $Profile.CurrentUserCurrentHost -Force
```
The -Force switch overwrites existing content, so be careful if you run this command locally and have an existing profile.

4. Run pwsh to create a new shell. You should now see the following (in green):
```powershell
Hello <your name>, welcome back
```
