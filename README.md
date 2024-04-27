> 个人iTerm2、Oh My Zsh 和 SSH 配置记录



# iTerm2

## 安装 

`brew install iTerm2  `

## 配置

1. 设置为默认终端
2. Appearance -> Theme -> Minimal (让窗口栏跟terminal一体化)
3. Profile -> Keys -> Key Mappings -> Presets...(left corner) -> Natural Text Editing 
    现在就可以想文字编辑一样编辑CLI，如: command+backspace=删除整行
4. Profile -> General -> Working Directory -> Reuse previous session's directory
    新开窗口的工作目录就是旧窗口的目录
5. 颜色 我希望配置类似我vscode的1984主题风格，所以选中了[详情见 iTerm2 colors theme: Cyberdyne](https://iterm2colorschemes.com/)，我也导出了一份配置 见Default.json文件

## 快捷键

+ Keys -> Key Bindings -> click `+` in left corner
+ Keybord Shortcut -> Click to Set -> press your hotkey
+ Action -> text -> sent text -> command you want + `\n` (for sent it to terminal)
  + such as `ssh account@xxx.xxx.xxx.xxx \n` to connect your service.

# Oh My ZSH



## 安装

[Oh My ZSH 官网](https://ohmyz.sh/)

`sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

## 设置

Mac默认是bash终端

+ `which zsh`显示你的zsh路径
+ `chsh $(which zsh)` 变量替换，并change shell 为 zsh
+ `echo $SHELL` 查看你当前用的是哪个shell


## 配置

> 以下以powerlevel10k, zsh-autosuggestions, zsh-syntax-highlighting为例, [参考](https://www.geekhour.net/2023/10/21/linux-terminal/#3-5-%E5%AE%89%E8%A3%85Zsh%E4%B8%BB%E9%A2%98%E5%92%8C%E6%8F%92%E4%BB%B6)

```bash
# powerlevel10k主题
git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
# zsh-autosuggestions自动提示插件
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
# zsh-syntax-highlighting语法高亮插件
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# 配置powerlevel10k
p10k configure
```

其中p10k的安装碰到了bug，第一次安装的时候并没有提示我安装nerd 字体

配置完成一遍之后，再`p10k configure` 反而提示我安装了。

如果你使用vscode, 你也需要[如何将nerd字体应用在vscode终端](https://github.com/romkatv/powerlevel10k/issues/671)

# SSH

> 这里以腾讯云举例

1. `vim /etc/ssh/sshd_config` 

2. 设置`PasswordAuthentication yes`，`PermitRootLogin yes`

## Terminal
这里我们采用iTerm2的action设置我们连接云端
1. 查看云端需要哪个用户，`ls /home/` 查看有哪些用户，而命令行的提示account@xxx，account就是你当前用户
1. 在iTerm2的shortcut里面添加一条记录Title=`xxxx`, Action=`ssh YourAccount@CouldPublicIPAddress`
1. 在iTerm2的Profile -> Session -> Status bar enable (最后一条) -> 加入Action模块，记得要勾选Status bar enable

最后我们就可以在iTerm2界面点击action菜单的`xxxx`应用你的指令，然后输入你的密码就可以了(在腾讯云的远程登入->密码/密钥登入)


## VScode

这里我们主要是安装一款`Remote - SSH`插件，安装之后点击Remote-SSH，点击加号添加你云端主机，`ssh YourAccount@CouldPublicIPAddress` 类似这样的命令，(按照他的placeholder的提示即可)

> 可能添加完后不显示，点击刷新即可

然后右键SSH，可以编辑SSH的config(`/Users/YourAccount/.ssh/config`)，其中`Host`可以更改为你想要的名字。