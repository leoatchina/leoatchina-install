# Introduce
My scripts for MOCOS LINUX WINDOWS softwares installation

## macOS

### disable warning
sudo spctl --master-disable

### install brew
#### origin
sh -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
#### use tsinghua mirror
```
git -C "$(brew --repo)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git
git -C "$(brew --repo homebrew/core)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git
git -C "$(brew --repo homebrew/cask)" remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask.git
brew update
```

### oh-my-zsh
```
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
### install basic
```
brew install --HEAD --with-jansson universal-ctags/universal-ctags/universal-ctags
brew install wget curl git vim neovim yarn cmake global tmux rg fzf
```
### pip use tsinghua mirrorr
```
pip3 config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip3 install pip -U
pip3 install pynvim python-language-server pygments neovim-reomote
```
### install with cask
```
brew cask install qq wechat neteasemusic iina
brew cask install hyperswitch iterm2 therm mounty mos karabiner-elements handshaker hammerspoon
brew cask install snipaste zotero xmind wiznote foxitreader cajviewer vscode
brew cask install keka yandex google-chrome firefox microsoft-edge docker
brew cask install v2rayu clash syncthing
```
### install handly
```
filezilla free-download-manager microsoft-office dictionnary shimo dr.unarchiver baiduinput baidunetdisk
```


## windows

### 美化powershell
*Running as administrator来打开PowerShell
```
Set-ExecutionPolicy RemoteSigned
Set-PSRepository -Name PSGallery -InstallationPolicy Trusted

iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

choco feature enable -n allowGlobalConfirmation
cinst git fzf lua sudo -y

cinst ccleaner bandizip ditto -y
cinst goldendict honeyview foxitreader sumatrapdf pdfxchangeviewer -y
cinst tim wechat filezilla brave firefox motrix nextcloud-client -y
cinst potplayer netease-cloudmusic -y

cinst everthing git vim neovim joplin notepad3 vscode  typora nodejs yarn zotero powertoys -y
cinst mobaxterm microsoft-windows-terminal alacritty -y
cinst visualstudio2019community -y
cinst wsl2 -y
cinst clash-for-windows -y

Install-Module -Name PSReadLine -Force -SkipPublisherCheck
Install-Module posh-git
Install-Module oh-my-posh
Install-Module --AllowCobber Get-ChildItemColor
Install-Module WindowsConsoleFonts
Install-Module windows-screenfetch  
Install-Module PSColor
Install-Module PSFzf
Install-Module DirColors

@"
#requires -Version 2 -Modules posh-git
function Write-Theme {
    param(
        [bool]
        `$lastCommandFailed,
        [string]
        `$with
    )

    `$lastColor = `$sl.Colors.PromptBackgroundColor
    `$prompt = Write-Prompt -Object `$sl.PromptSymbols.StartSymbol -ForegroundColor `$sl.Colors.PromptForegroundColor -BackgroundColor `$sl.Colors.SessionInfoBackgroundColor

    #check the last command state and indicate if failed
    If (`$lastCommandFailed) {
        `$prompt += Write-Prompt -Object "`$(`$sl.PromptSymbols.FailedCommandSymbol) " -ForegroundColor `$sl.Colors.CommandFailedIconForegroundColor -BackgroundColor `$sl.Colors.SessionInfoBackgroundColor
    }

    #check for elevated prompt
    If (Test-Administrator) {
        `$prompt += Write-Prompt -Object "`$(`$sl.PromptSymbols.ElevatedSymbol) " -ForegroundColor `$sl.Colors.AdminIconForegroundColor -BackgroundColor `$sl.Colors.SessionInfoBackgroundColor
    }

    `$user = [System.Environment]::UserName
    `$computer = [System.Environment]::MachineName
    `$path = Get-FullPath -dir `$pwd
    if (Test-NotDefaultUser(`$user)) {
        `$prompt += Write-Prompt -Object "`$user@`$computer " -ForegroundColor `$sl.Colors.SessionInfoForegroundColor -BackgroundColor `$sl.Colors.SessionInfoBackgroundColor
    }

    if (Test-VirtualEnv) {
        `$prompt += Write-Prompt -Object "`$(`$sl.PromptSymbols.SegmentForwardSymbol) " -ForegroundColor `$sl.Colors.SessionInfoBackgroundColor -BackgroundColor `$sl.Colors.VirtualEnvBackgroundColor
        `$prompt += Write-Prompt -Object "`$(`$sl.PromptSymbols.VirtualEnvSymbol) `$(Get-VirtualEnvName) " -ForegroundColor `$sl.Colors.VirtualEnvForegroundColor -BackgroundColor `$sl.Colors.VirtualEnvBackgroundColor
        `$prompt += Write-Prompt -Object "`$(`$sl.PromptSymbols.SegmentForwardSymbol) " -ForegroundColor `$sl.Colors.VirtualEnvBackgroundColor -BackgroundColor `$sl.Colors.PromptBackgroundColor
    }
    else {
        `$prompt += Write-Prompt -Object "`$(`$sl.PromptSymbols.SegmentForwardSymbol) " -ForegroundColor `$sl.Colors.SessionInfoBackgroundColor -BackgroundColor `$sl.Colors.PromptBackgroundColor
    }

    # Writes the drive portion
    `$prompt += Write-Prompt -Object "`$path " -ForegroundColor `$sl.Colors.PromptForegroundColor -BackgroundColor `$sl.Colors.PromptBackgroundColor

    `$status = Get-VCSStatus
    if (`$status) {
        `$themeInfo = Get-VcsInfo -status (`$status)
        `$lastColor = `$themeInfo.BackgroundColor
        `$prompt += Write-Prompt -Object `$(`$sl.PromptSymbols.SegmentForwardSymbol) -ForegroundColor `$sl.Colors.PromptBackgroundColor -BackgroundColor `$lastColor
        `$prompt += Write-Prompt -Object " `$(`$themeInfo.VcInfo) " -BackgroundColor `$lastColor -ForegroundColor `$sl.Colors.GitForegroundColor
    }

    # Writes the postfix to the prompt
    `$prompt += Write-Prompt -Object `$sl.PromptSymbols.SegmentForwardSymbol -ForegroundColor `$lastColor

    `$timeStamp = Get-Date -UFormat %r
    `$timestamp = "[`$timeStamp]"

    `$prompt += Set-CursorForRightBlockWrite -textLength (`$timestamp.Length + 1)
    `$prompt += Write-Prompt `$timeStamp -ForegroundColor `$sl.Colors.PromptForegroundColor

    `$prompt += Set-Newline

    if (`$with) {
        `$prompt += Write-Prompt -Object "`$(`$with.ToUpper()) " -BackgroundColor `$sl.Colors.WithBackgroundColor -ForegroundColor `$sl.Colors.WithForegroundColor
    }
    `$prompt += Write-Prompt -Object (`$sl.PromptSymbols.PromptIndicator) -ForegroundColor `$sl.Colors.PromptBackgroundColor
    `$prompt += ' '
    `$prompt
}

`$sl = `$global:ThemeSettings #local settings
`$sl.PromptSymbols.StartSymbol = ''
`$sl.PromptSymbols.PromptIndicator = [char]::ConvertFromUtf32(0x276F)
`$sl.PromptSymbols.SegmentForwardSymbol = [char]::ConvertFromUtf32(0xE0B0)
`$sl.Colors.PromptForegroundColor = [ConsoleColor]::White
`$sl.Colors.PromptSymbolColor = [ConsoleColor]::White
`$sl.Colors.PromptHighlightColor = [ConsoleColor]::DarkBlue
`$sl.Colors.GitForegroundColor = [ConsoleColor]::Black
`$sl.Colors.WithForegroundColor = [ConsoleColor]::DarkRed
`$sl.Colors.WithBackgroundColor = [ConsoleColor]::Magenta
`$sl.Colors.VirtualEnvBackgroundColor = [System.ConsoleColor]::Red
`$sl.Colors.VirtualEnvForegroundColor = [System.ConsoleColor]::White
"@ > $env:userprofile"\Documents\WindowsPowerShell\Modules\oh-my-posh\2.0.487\Themes\Paradox.psm1"

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
huorong office v2ray-trojan dism
```

## jupyterlab
###
```
jupyter labextension install @jupyter-widgets/jupyterlab-manager
jupyter labextension install ipysheet
jupyter labextension install @jupyterlab/toc
jupyter labextension install jupyterlab-drawio
jupyter labextension install jupyterlab-kernelspy
jupyter labextension install jupyterlab-spreadsheet
jupyter labextension install @krassowski/jupyterlab_go_to_definition
jupyter labextension install @telamonian/theme-darcula
jupyter labextension install @mohirio/jupyterlab-horizon-theme
jupyter labextension install jupyterlab_vim
jupyter labextension install @lckr/jupyterlab_variableinspector
jupyter lab build
```
