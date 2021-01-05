##1. 显示 Terminal 自带的 shell

```shell
//查看当前环境shell
echo $SHELL
//查看系统自带哪些shell
cat /etc/shells
//将zsh设置为默认shell
chsh -s $(which zsh) //需要重启
```



##2. 在 zsh 环境中 安装 oh-my-zsh

```shell
# 安装 oh my zsh 之前必须安装 zsh
# 方法一：通过 wget 或者 curl 安装
sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

# 方法二：当然也可以通过git下载
git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh

--
# 安装 oh my zsh 提示 curl: (7) Failed to connect to raw.githubusercontent.com port 443: Connection refused (解决方法)
# 方法三 镜像
sh -c "$(curl -fsSL https://gitee.com/mirrors/oh-my-zsh/raw/master/tools/install.sh)"
```



##2.4. 安装 theme | Powerlevel10k

```shell
# 下載並安裝 powerlevel10k
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>! ~/.zshrc
# 方便使用者的簡易設定
p10k configure
# (進階編輯配置) ~/.zshrc (zsh 的預設配置)
vim ~/.zshrc
# (進階編輯配置) ~/.p10k.zsh (powerlevel10k 的配置)
vim ~/.p10k.zsh
```



##2.5. 安装 oh-my-zsh 里的插件

安装插件需要打开`~/.zshrc`，找到`plugins=`，安装完成后，在其中写插件名
注意，若修改此文件，重启终端后有效 或 使用 `source ~/.zshrc` 更新配置。

#### + autojump

功能：实现目录间快速跳转，通过 history 中的行为 cache 下来。可以 直接 `j + 目录名`

```shell
git clone git://github.com/joelthelion/autojump.git
cd autojump
./install.py
subl ~/.zshrc #用 vim open 都行
# 在文件里找到 plugins，添加
plugins=(autojump)
# 在文件末尾添加
[[ -s ~/.autojump/etc/profile.d/autojump.sh ]] && . ~/.autojump/etc/profile.d/autojump.sh
source ~/.zshrc
```

#### + zsh-autosuggestion

功能：输入命令时可提示 自动补全（灰色部分），然后摁键盘的右键填满

```shell
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
subl ~/.zshrc #用 vim open 都行
# 在文件里找到 plugins，添加
plugins=(
  autojump
  zsh-autosuggestions
)
source ~/.zshrc
```

#### + zsh-syntax-highlighting

功能：提示错误拼写的命令

```shell
git clone git://github.com/zsh-users/zsh-syntax-highlighting $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
subl ~/.zshrc #用 vim open 都行
# 在文件里找到plugins，添加
plugins=(
  autojump
  zsh-autosuggestions
  zsh-syntax-highlighting
)
source ~/.zshrc
```



##3. zsh 快速打开 sublime Text 进行编辑

   1. 打开`open ~/.zshrc`
   2. 在`.zshrc`尾部加入 

   ```bash
   alias subl="/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl"
   ```

   3. 更新改动 `source ~/.zshrc`
   4. 便可使用 sublime 在命令行中创建和编辑文件 `subl test.txt`

----

Reference：

+ ohmyzsh github: *https://github.com/ohmyzsh/ohmyzsh*
+ oh my zsh 官网: *https://ohmyz.sh/*
+ 颜酱 *https://juejin.cn/post/6844903939121348616* 来源：掘金
