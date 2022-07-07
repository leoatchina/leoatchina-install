# windows

- Install winget/windows_terminal from window store
- add edge mobarxterm to taskbar

## Install with winget 
```
winget install -e git
winget install -e gsudo
winget install -e wezterm
winget install -e peazip
winget install -e powertoys
winget install -e everything
winget install -e firefox
winget install -e filezilla
winget install -e honeyview
winget install -e tim 
winget install -e wechat
winget install -e huorong
winget install -e snipaste
winget install -e anaconda3
winget install -e foxitreader
winget install -e honeyview
winget install -e clash-for-window
winget install -e nodejs
npm install -g yarn
```


## install scoop
```
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
# irm get.scoop.sh | iex

$webClient = New-Object System.Net.WebClient
$webClient.Proxy = New-Object System.Net.WebProxy('10.10.52.61', 7890)
$webClient.DownloadString('https://get.scoop.sh') -replace "new-object net.webclient","$webClient" | Invoke-Expression
scoop bucket add extra
scoop bucket add nerd-fonts
```
## modify hosts
```
code C:\Windows\System32\drivers\etc
199.232.68.133 raw.githubusercontent.com
```

## scoop install
```
scoop install fzf lua wget curl dismplusplus
scoop install vim neovim joplin zotero notepad3 zeal obsidian vscode goldendict
scoop install r rstudio potplayer mysql-workbench sqlitestudio idea pycharm
scoop install wireshark fiddler nextcloud 
```

## 美化powershell
```
Install-Module -Name PSReadLine -Force -SkipPublisherCheck
Install-Module posh-git
Install-Module oh-my-posh
Install-Module Get-ChildItemColor -AllowClobber
Install-Module WindowsConsoleFonts
Install-Module windows-screenfetch
Install-Module PSColor
Install-Module PSFzf
Install-Module DirColors

New-Item -Type File -Path $PROFILE -Force
@"
  Set-ExecutionPolicy -Scope CurrentUser Bypass
  Set-Alias ll Get-ChildItemColor -option AllScope
  Set-Alias ls Get-ChildItemColorFormatWide -option AllScope
  Import-Module posh-git
  Import-Module oh-my-posh
  Import-Module Get-ChildItemColor
  Import-Module WindowsConsoleFonts
  Import-Module windows-screenfetch
  Import-Module DirColors
  Import-Module PSReadline
  Import-Module PSColor
  Import-Module PSFzf -ArgumentList 'Ctrl+t','Ctrl+r'
  function which($name) { Get-Command $name | Select-Object Definition }
  function rmrf($item) { Remove-Item $item -Recurse -Force }
  function mkfile($file) { "" | Out-File $file -Encoding ASCII }
"@ > $PROFILE

cd C:/Config
git clone --depth 1 https://github.com/powerline/fonts.git
cd .\fonts\
.\install.ps1
cd ..
```

## wsl2
```
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
download and install https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi
wsl --set-default-version 2

```

### install handly
```
office wps yuque utools snipaste
```