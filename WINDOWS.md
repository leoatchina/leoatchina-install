
## windows
Install choco
```
Set-ExecutionPolicy RemoteSigned
Set-PSRepository -Name PSGallery -InstallationPolicy Trusted

iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

Install softwares
```
choco feature enable -n allowGlobalConfirmation

cinst git fzf lua sudo gsudo nodejs yarn -y
cinst dismplusplus ccleaner bandizip ditto -y
cinst goldendict honeyview foxitreader sumatrapdf -y
cinst tim wechat filezilla brave firefox motrix nextcloud-client wireshark telegram fiddler -y
cinst potplayer netease-cloudmusic mpv -y
cinst everthing git vim neovim joplin typora zotero powertoys notepad3 zeal freefilesync -y
cinst mobaxterm microsoft-windows-terminal -y
cinst visualstudio2019community anaconda3 -y
cinst mysql.workbench sqlite sqlite.shell sqlitestudio -y
cinst r r.studio -y
cinst wsl2 docker -y
cinst clash-for-windows v2rayn -y
```

### 美化powershell
```
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
huorong office wps obsidian yuque utools
```
