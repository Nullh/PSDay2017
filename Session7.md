# Creating Complex Labs with Lability
## [Andre Kamman](http://andrekamman.com) DP MVP

Lability - `install-module lability`
`get-command -module lability`

Check the defaults then `Start-LabHostConfiguration` and you're installed and configured.
`Test-LabHostConfiguration -Verbose` will tell you if your install is valid.

To add your own non-eval images use: `Register-LabMedia -Id <name> -MediaType ISO -Uri file://blah -Architecture x64 -ImageName "Windows Sserver 2016 WINDOWSSERVERCORE" -Filename blah.iso` this will look for the iso file in your default directories set up in config.

To find the correct Windows image, mount the image then  `Get-WindowsImage -ImagePath C:\sources\install.wim`

