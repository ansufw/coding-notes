# PowerShell

## Create new environment variable

1. Temporary

```powershell
$env:NEW_ENV_VAR = "new_value"
```

2. Permanent
```powershell
[Environment]::SetEnvironmentVariable("NEW_ENV_VAR", "new_value", "User")
```

in the third parameter you can use: 
- Machine: Variable for all users
- User: Variable for current user
- Process: Variable for current process

## View environment variables

1. View all

```powershell
Get-ChildItem Env:
```

2. View specific
```powershell
Get-ChildItem Env:NEW_ENV_VAR
# or
$env:MY_VAR
```

## Remove environment variable

```powershell
Remove-Item Env:\MY_ENV_VAR
```

## Set env variable from file
```powershell
[Environment]::SetEnvironmentVariable("TEST1", $(Get-Content -Raw C:\Users\user\.ssh\id_rsa), "User")
```

## Refresh powershell

```powershell
refreshenv
```
note: RefreshEnv.cmd does not work when run from this process. If you're in PowerShell, please 'Import-Module $env:ChocolateyInstall\helpers\chocolateyProfile.psm1' and try again.


