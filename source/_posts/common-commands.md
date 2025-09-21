---
title: 常用命令
date: 2024-01-10 16:55:48
tags: 
    - 科研
categories: 
    - 编程
summary: 常用的命令和一些配置文件
---

## conda命令

### 获取版本号

```shell
conda --version
conda -V
```

### 环境管理

#### 查看环境管理的全部命令帮助

```shell
conda env -h
```

#### 创建环境

```shell
conda create --name your_env_name
```

##### 创建指定python版本的环境

```
conda create --name your_env_name python=2.7
conda create --name your_env_name python=3
conda create --name your_env_name python=3.5
```

##### 根据已有环境名复制生成新的环境

假设已有环境名为A，需要生成的环境名为B：

```
conda create -n B --clone A
```

##### 根据已有环境路径复制生成新的环境

假设已有环境路径为D:\A，需要生成的新的环境名为B：

```python
conda create -n B --clone D:\A
```

生成的新的环境的位置在anaconda的安装路径下，一般情况在`D:\Anaconda3\envs\`文件夹下。

#### 列举当前所有环境

```shell
conda info --envs
conda env list
```

#### 进入某个环境

```shell
activate your_env_name
```

#### 退出环境

```shell
deactivate 
```

#### 删除虚拟环境

```shell
conda remove -n 虚拟环境名字 --all
```

#### 持久添加通道

```shell
conda config --add channels 通道地址
```

#### 删除通道

```shell
conda config --remove channels 通道地址
```

#### 查看配置文件中有哪些通道

```shell
conda config --get
```

```shell
conda config --show
```



### 镜像链接

（1）常见包

| 镜像名             | 镜像地址                                                |
| ------------------ | ------------------------------------------------------- |
| 清华镜像           | https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main |
| 北京外国语大学镜像 | https://mirrors.bfsu.edu.cn/anaconda/pkgs/main          |
| 阿里巴巴镜像       | https://mirrors.aliyun.com/anaconda/pkgs/main           |

（2）window64下的pytorch的一些镜像

| 镜像名             | 镜像地址                                                     |
| ------------------ | ------------------------------------------------------------ |
| 清华镜像           | https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/win-64/ |
| 北京外国语大学镜像 | https://mirrors.bfsu.edu.cn/anaconda/cloud/pytorch/win-64/   |
| 阿里巴巴镜像       | https://mirrors.aliyun.com/anaconda/cloud/pytorch/win-64/    |
| 南京大学镜像       | https://mirrors.nju.edu.cn/pub/anaconda/cloud/pytorch/win-64/ |



## tmux命令

### 基本概念

1. 会话（Session）

    tmux 会话是一个独立的运行环境，可以包含多个窗口。即使断开连接，会话也会继续在后台运行。

2. 窗口（Window）

    每个会话可以包含多个窗口，类似于浏览器中的标签页。

3. 面板（Pane）

    每个窗口可以分割成多个面板，允许同时查看和操作多个终端。

> `tmux 的所有操作都需要先按下前缀键（默认是 Ctrl+b），然后输入命令键。`

### 会话管理

#### 列出所有会话

```bash
tmux ls
```

#### 创建名为name的新会话

```bash
tmux new -s <name>
```

#### 分离当前会话（会话继续后台运行）

```bash
Ctrl+b d
```

#### 重新连接到指定会话

```bash
tmux attach -t <name>
```

 #### 重命名当前会话

```bash
Ctrl+b $
```

#### 切换会话

```bash
Ctrl+b s
```

## linux命令

#### 统计文件的个数

1. 统计当前文件夹下文件的个数，包括子文件夹里的

```bash
ls -lR|grep "^-"|wc -l
```

2. 统计文件夹下目录的个数，包括子文件夹里的

```bash
ls -lR|grep "^d"|wc -l
```

3.  统计当前文件夹下文件的个数

```bash
ls -l |grep "^-"|wc -l
```

4. 统计当前文件夹下目录（文件夹）的个数

```bash
ls -l |grep "^d"|wc -l
```

5.  查看当前目录下每个子目录的文件数量

```bash
find . -maxdepth 1 -type d | while read dir; do count=$(find "$dir" -type f | wc -l); echo "$dir : $count"; done
```

6. 查看当前文件夹下图片数量

``` bash
find . -type f | grep -iE '\.(jpg|jpeg|png|gif|bmp)$' | wc -l
```

