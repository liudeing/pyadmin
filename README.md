## 配置python多环境
pyenv 可在不同 python 版本之间轻松切换，实现 python 环境隔离，且支持自动激活和退出虚拟环境
STEP1. 安装和设置 pyenv
```shell
$ brew install pyenv 
$ brew install pyenv-virtualenv
```
STEP2. 根据自身环境，将下方内容加到对应文件中： .bashrc 或者 .zshrc
```shell
# pyenv
export PYENV_ROOT="/opt/homebrew/opt/pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
export PATH="$PYENV_ROOT/shims:$PATH"

if which pyenv > /dev/null;
  then eval "$(pyenv init -)";
fi

# pyenv-virtualenv
if which pyenv virtualenv > /dev/null;
  then eval "$(pyenv virtualenv-init -)";
fi
```
命令刷新`source ~/.zshrc`

STEP3. 验证是否安装成功 
```
pyenv
```
STEP4. python指定任意的runtime
```
~/.pyenv/versions/3.12.1/bin/python -m venv .venv
```
STEP5. 使用

使用如下语句创建虚拟环境

`pyenv virtualenv 版本号 环境名`

注意：版本号需要以之前pyenv里安装的Python版本号相同。

使用如下命令激活虚拟环境：

`pyenv activate 环境名`

使用 `pyenv deactivate` 退出环境。
使用 `rm -rf ~/.pyenv/versions/环境名` 删除环境。

| 基本使用命令           | 描述                                          |
|:-----------------|:--------------------------------------------|
| pyenv --version  | 查看 pyenv 的版本                                |
| pyenv versions   | 罗列当前已安装的所有 python 环境，如果是当前正在使用的环境，则前面会有个 *  |
| pyenv help       | 查看帮助                                        |
| pyenv init       | 如果输入 pyenv 之后使用 tab 不补全，可以使用该命令进行初始即可使用补全命令 |

| 安装环境命令            | 描述                         |
|:------------------|:---------------------------|
| pyenv install -l  | 显示可以安装的版本列表                |
| pyenv install     | 版本号安装指定版本的 python          |
| pyenv rehash      | 更新本地数据库，安装指定版本的 python 后使用 |

| 环境应用命令       | 描述                                                                       |
|:-------------|:-------------------------------------------------------------------------|
| pyenv global | 版本号更改本机版本，重启不会造成再次更改                                                     |
| pyenv local  | 版本号会在当前目录创建 .python-version 文件，并记录设置的 python 环境，每次进入该目录会自动设置成该 python 环境 |
| pyenv shell  | 版本号更改当前 shell 下使用的 python 版本，临时生效，优先级高于 global                           |

STEP6. 卸载
卸载pyenv时，只需要删除 ~/.pyenv 目录、删除 ~/.bashrc 文件中的上文加入的部分即可。

## 设置django工程
1. 安装django源码
* 安装pip
* 看一下env，提供的隔离python开发环境
* 在创建和激活的虚拟环境后 `python -m pip install Django==5.0.3`
2. 查看该目录下所有的安装包和版本，`pip list` 
3. 创建一个Django项目
* `python -m django --version`
* `django-admin startproject pyadmin`
* `python manage.py runserver 8000`



