# Installing PSTodoist

## Install latest build

```Powershell
    [Net.ServicePointManager]::SecurityProtocol = "tls12, tls11, tls"

    $ModulePath = "C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\"

    $Version = "master"



    if((Test-Path ".\PStodoist-$Version")) {

        Remove-Item ".\PStodoist-$Version" -Force -Recurse

    }

    Invoke-RestMethod -Uri "https://github.com/harry-joyce/PSTodoist/archive/refs/tags/1.0.zip" -OutFile ".\PStodoist-$Version.zip"

    if((Test-Path ".\PStodoist-$Version")) {

        Remove-Item ".\PStodoist-$Version" -recurse -force

    }


    Expand-Archive ".\PStodoist-$Version.zip" -DestinationPath ".\"
    If(!(Test-Path "$ModulePath\PSTodoist")) {

        New-Item -ItemType Directory -Path $ModulePath -Name 'PSTodoist'

    }

    If(!(Test-Path "$ModulePath\PSTodoist")) {

        Remove-Item "$ModulePath\PSTodoist\*" -Recurse -Force 

    }

    cp ".\PSTodoist-$Version\Release\PSTodoist\*" -Destination "$ModulePath\PSTodoist\" -Recurse -Force
```
