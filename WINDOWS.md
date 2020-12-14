## windows

setting Policy

```
Set-ExecutionPolicy RemoteSigned
Set-PSRepository -Name PSGallery -InstallationPolicy Trusted
```

Install choco

```
iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
choco feature enable -n allowGlobalConfirmation
```

Install command tools

```
cinst mobaxterm microsoft-windows-terminal git -y
```

go on install

```
cinst sudo gsudo -y
cinst dismplusplus bandizip ditto -y
cinst potplayer netease-cloudmusic -y
cinst honeyview foxitreader sumatrapdf -y
cinst tim wechat filezilla vivaldi googlechrome firefox motrix nextcloud-client wireshark telegram fiddler -y
cinst everthing vim neovim joplin typora zotero powertoys notepad3 zeal freefilesync -y
```

Install program tools

```
cinst fzf lua nodejs yarn -y
cinst mysql.workbench sqlite sqlite.shell sqlitestudio -y
cinst wsl2 docker -y
cinst anaconda3 -y
cinst clash-for-windows v2rayn -y
```

```
cinst docker-desktop -y
cinst r r.studio -y
```

```
cinst visualstudio2019community -y
```

wsl2

```
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
download and install https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi
wsl --set-default-version 2

cinst wsl2 -y
cinst docker-desktop -y
cinst wsl-ubuntu-1804 -y
```

### 美化powershell

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


if (!(Test-Path -Path $PROFILE )) { New-Item -Type File -Path $PROFILE -Force }
@"
  Set-Theme Paradox
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

cd ~/config
git clone --depth 1 https://github.com/powerline/fonts.git
cd .\fonts\
.\install.ps1
cd ..
```

### install handly

```
huorong office wps obsidian yuque utools golendict
```
