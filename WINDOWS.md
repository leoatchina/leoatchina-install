# windows

- Install winget/windows_terminal from window store
- add edge mobarxterm to taskbar

## Install with winget 
```
winget install -e gsudo
winget install -e powertoys
winget install -e chrome
winget install -e anaconda3
winget install -e tim 
winget install -e wechat
winget install -e nodejs
winget install -e --id=Sogou.SogouWBInput
npm install -g yarn
```
## optinal
```
winget install -e huorong
winget install -e peazip
```

## install scoop
```
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
# irm get.scoop.sh | iex
$webClient = New-Object System.Net.WebClient
$webClient.Proxy = New-Object System.Net.WebProxy('10.10.52.61', 7890)
$webClient.DownloadString('https://get.scoop.sh') -replace "new-object net.webclient","$webClient" | Invoke-Expression
scoop bucket add java
scoop bucket add extra
scoop bucket add nirsoft
scoop bucket add nerd-fonts
scoop bucket add apps https://github.com/kkzzhizhou/scoop-apps
scoop bucket add lemon https://github.com/hoilc/scoop-lemon
scoop bucket add scoopet https://github.com/ivaquero/scoopet.git
scoop install scoop-completion
Import-Module "$($(Get-Item $(Get-Command scoop.ps1).Path).Directory.Parent.FullName)\modules\scoop-completion"

```
## modify hosts
```
code C:\Windows\System32\drivers\etc
199.232.68.133 raw.githubusercontent.com
```
## scoop install
```
scoop install firefox filezilla
scoop install everything fzf lua wget curl dismplusplus ripgrep clink git 
scoop install vim neovim joplin zotero notepad3 zeal obsidian vscode goldendict
scoop install r rstudio potplayer mysql-workbench sqlitestudio idea obsidian
scoop install wireshark fiddler nextcloud
scoop install MicrosoftVisualStudioCommunity2022-install   
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
Install-Module DirColors
Install-Module -Name PSFzf -RequiredVersion 2.0.0 -Scope CurrentUser -Force




cd C:/Config
git clone --depth 1 https://github.com/powerline/fonts.git
cd .\fonts\
.\install.ps1
cd ..
```


## $PROFILE
notepad $PROFILE
```
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
Import-Module "$($(Get-Item $(Get-Command scoop.ps1).Path).Directory.Parent.FullName)\modules\scoop-completion"

# Utilities
function rmrf($item) { Remove-Item $item -Recurse -Force }
function mkfile($file) { "" | Out-File $file -Encoding ASCII }
function which ($command) {
  Get-Command -Name $command -ErrorAction SilentlyContinue |
    Select-Object -ExpandProperty Path -ErrorAction SilentlyContinue
}
function touch($name){
  if ($name) {
    $file_path = Split-Path -Path $name
    $file_name = Split-Path -Path $name -Leaf
    if ($file_path -eq "") {
      $file_path = "."
    }
    if (-Not (Test-Path($file_path))) {
      New-Item -ItemType "directory" -Path $file_path
    }
    New-Item -Path $file_path -Name $file_name -ItemType "file"
  }
  else {
     Write-Host "Command to create new file."
  }
}

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
ms-office wps utools snipaste wezterm tabby
```
