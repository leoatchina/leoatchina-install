# Introduce
My scripts for MOCOS LINXU WINDOWS softwares install
# macOS
## disable warning
sudo spctl --master-disable
## install brew
### origin
sh -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
### use china mirror

curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install > /tmp/brew_install

sed 's#https://github\.com/Homebrew/brew#git://mirrors\.ustc\.edu\.cn/brew\.git#g' /tmp/brew_install > /tmp/brew_install_new

/usr/bin/ruby /tmp/brew_install_new

cd "$(brew --repo)"

git remote set-url origin https://mirrors.ustc.edu.cn/brew.git

cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"

git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git

cd "$(brew --repo)/Library/Taps/homebrew/homebrew-cask"

git remote set-url origin git://mirrors.ustc.edu.cn/homebrew-cask.git

echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.bash_profile

source ~/.bash_profile

brew update

## oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

## install basic
brew install --HEAD --with-jansson universal-ctags/universal-ctags/universal-ctags

brew install wget curl vim neovim yarn cmake global tmux rg fzf
##　use tsinghua mirrorr
pip3 config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

pip3 install pip -U

pip3 install neovim python-language-server pygments
## install with cask
brew cask install qq wechat neteasemusic iina

brew cask install syncthing

brew cask install hyperswitch iterm2 alacritty mounty mos karabiner-elements handshaker hammerspoon

brew cask install snipaste zotero xmind wiznote foxitreader cajviewer vimr

brew cask install keka yandex google-chrome clashx v2rayu docker
## install handly
vscode filezilla free-download-manager vanilla microsoft-office dictionnary shimo dr.unarchiver baiduinput baidunetdisk
# windows
## Running as administrator来打开PowerShell, install chocolatey
Set-ExecutionPolicy RemoteSigned
iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex
## install with chocolatey
cinst anaconda3 mobaxterm microsoft-windows-terminal wsl wsl-ubuntu-1804 -y

cinst ccleaner bandizip ditto -y

cinst goldendict snipaste xnview cajviewer foxitreader sumatrapdf foxmail -y

cinst tim wechat googlechrome yandex -y

cinst everthing wox git neovim yarn zotero synctrayzor -y

cinst potplayer netease-cloudmusic -y

## install handly
huorong office vscode filezilla edge clashx v2rayn qqinput freedownloadmanager dism
