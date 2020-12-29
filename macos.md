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
brew install wget curl git vim neovim yarn nodejs cmake global tmux rg fzf
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
brew cask install hyperswitch iterm2 mounty mos karabiner-elements handshaker hammerspoon
brew cask install snipaste zotero xmind wiznote foxitreader cajviewer vscode
brew cask install keka google-chrome firefox microsoft-edge docker
brew cask install v2rayu clash
```
### install handly
```
filezilla free-download-manager microsoft-office dictionnary shimo dr.unarchiver baiduinput baidunetdisk
```

