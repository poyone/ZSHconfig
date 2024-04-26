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



# SSH

