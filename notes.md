# cd
cd ~  回家  
cd ~/digital-cousins 切换目录  
cd .. 的意思就是：切换到当前目录的上一级目录。  

# wget 命令：互联网下载器
wget 是一个用于从网上下载文件的命令行工具。

你可以把它想象成没有界面的浏览器或者像迅雷、IDM 这样的下载工具，但它是在终端里通过命令来工作的。

功能：它支持 HTTP, HTTPS, FTP 等协议，可以从指定的 URL 地址下载文件。

特点：非常稳定，支持断点续传（如果下载中断，可以重新连接继续下载）。

在你命令中的用途：

bash
wget https://repo.anaconda.com/miniconda/Miniconda3-py310_24.5.0-0-Linux-x86_64.sh
这行命令的意思是：“请从 https://repo.anaconda.com/... 这个网址，把名为 Miniconda3-py310_24.5.0-0-Linux-x86_64.sh 的文件下载到我当前所在的文件夹里。”

运行后，你会看到下载进度，完成后你的 digital-cousins 目录里就会多出一个 .sh 文件。

下载失败的话考虑本地下载后再上传服务器
打开powershell后scp "C:\Users\张泽\Downloads\paramnet_360cities_edina_rpfpp.pth" zzybdgq@172.24.112.192:/home/zzybdgq/.cache/torch/hub/checkpoints/paramnet_360cities_edina_rpfpp.pth

# bash 命令：脚本解释器 / 运行器
bash 是一种 Shell（命令解释器），也是它的命令名称。用它来执行一个文件，意思是“请把这个文件里的内容当作一系列命令来逐行执行”。

什么是 Shell？ 就是你正在使用的这个黑色终端窗口，它负责理解你输入的命令（如 ls, cd），并调用系统真正的程序来执行。bash 是最流行的一种 Shell。

什么是 Shell 脚本 (.sh 文件)？ 它是一个文本文件，里面写了一连串的命令（就像 Windows 的 .bat 批处理文件）。光双击这个文件是没有用的，需要有一个“解释器”来读它、执行它。

在你命令中的用途：

bash
bash Miniconda3-py310_24.5.0-0-Linux-x86_64.sh
这行命令的意思是：“请调用 bash 这个解释器，来读取并执行 Miniconda3-py310_24.5.0-0-Linux-x86_64.sh 这个文件里的所有安装指令。”

这个 .sh 文件本身不是可执行程序，它是一个“安装脚本”。bash 命令才是真正干活的人，它打开这个“安装说明书”（脚本文件），然后按照里面的步骤一步步地安装 Miniconda。

一个生动的比喻
整个过程就像你要组装一个家具（安装 Miniconda）：

wget：相当于你上网找到家具商的官网，把家具的安装说明书和所有零件（.sh 文件）下载到你的电脑里。

bash：相当于你自己拿起那份下载好的安装说明书，亲自阅读上面的每一步指示，然后动手组装家具。

所以，这两个命令是连续的关键步骤：先下载（wget），后执行（bash）。

# mkdir -p deps && cd deps
mkdir -p deps mkdir -p deps 的意思是：请确保有一个名为 deps 的目录存在。如果它不存在，就创建它；如果它已经存在，也不用提示错误。

# install
pip install -e 是一个非常重要且实用的 pip 安装命令。我们来详细分解它。
pip install: 标准的 Python 包安装命令。
-e: 是 --editable 选项的简写形式，意思是“可编辑的”。
conda install -c <频道名称> <包名称>

# which
查找文件路径

# 配置代理
export HTTP_PROXY=http://172.19.21.115:7078    
export HTTPS_PROXY=http://172.19.21.115:7078  
vpn要开全局代理  
echo "HTTP_PROXY: $HTTP_PROXY"  
echo "HTTPS_PROXY: $HTTPS_PROXY"  

# python建立虚拟环境
打开PowerShell，并切换到你想要的非C盘目录，比如D盘：

bash
D:  # 切换到D盘
cd D:\MyProjects  # 进入你的项目文件夹（如果没有就新建一个）
mkdir panda3d-survey  # 为你的调研项目创建一个新文件夹
cd panda3d-survey     # 进入这个文件夹
创建虚拟环境：
这里的 venv 文件夹就是你的新环境，它会在当前目录（D:\MyProjects\panda3d-survey）下创建。

bash
python -m venv venv
python -m venv my_venv
激活虚拟环境：

bash
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process
.\venv\Scripts\Activate.ps1
激活后，你的PowerShell命令行前面会出现一个 (venv) 标志，这表示你正工作在这个独立环境中。

在虚拟环境中安装Panda3D：

bash
(venv) PS D:\MyProjects\panda3d-survey> pip install panda3d
看！现在Panda3D就被安装到了 D:\MyProjects\panda3d-survey\venv 这个文件夹里，而不是你的C盘！

未来如何管理：

进入项目工作：每次要在这个项目下工作时，先进入 D:\MyProjects\panda3d-survey 目录，然后执行第3步（激活环境）。

安装其他库：在 (venv) 环境下用 pip install，所有库都会装到D盘。

删除项目：如果你以后不想做这个项目了，直接整个删除 D:\MyProjects\panda3d-survey 文件夹，所有相关文件（代码、环境、安装的库）就都清理干净了，完全不会弄乱C盘。

nptepad main.py 创建文件


Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process  防止报错


# -*- coding: utf-8 -*-


打开 VS Code，确保已安装 "Remote - WSL" 扩展（如果没有，在扩展商店搜索安装）
按下 Ctrl+Shift+P 打开命令面板，输入并选择：
WSL: Connect to WSL using Distro
选择你的 Ubuntu 子系统，VS Code 会自动新建一个连接到 WSL 的窗口
在新窗口中，点击左侧 "资源管理器" 图标，再点击 "打开文件夹"，就能浏览并选择 Ubuntu 里的目录了
