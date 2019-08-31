# introduce 
My scripts for MOCOS LINXU WINDOWS softwares install
# macOS
## disable warning
sudo spctl --master-disable
## install brew
### origin
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
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
## install basic
brew install --HEAD --with-jansson universal-ctags/universal-ctags/universal-ctags    
brew install wget curl vim neovim yarn cmake global tmux rg fzf 
## oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
## install with cask
brew cask install qq wechat neteasemusic iina 
brew cask install syncthing 
brew cask install hyperswitch iterm2 alacritty mounty mos karabiner-elements handshaker hammerspoon
brew cask install kantu snipaste
brew cask install baidunetdisk aria2gui 
brew cask install docker zotero xmind wiznote foxitreader cajviewer
brew cask install keka firefox yandex google-chrome mysqlworkbench clashx
## install handly
vscode filezilla free-download-manager vanilla vimR microsoft-office dictionnary