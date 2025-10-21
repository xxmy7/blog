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



#### 同步文件夹

> `rsync`介绍：
> `sync`同步：刷新文件系统缓存，强制将修改过的数据块写入磁盘，并且更新超级快。一般重启系统前执行`sync`命令
> `async`：将数据先缓存在缓冲区，再周期性（一般是30s）的去同步到磁盘 。性能好，但是不能保证数据的安全性
> `rsync`：远程同步，remote synchronous

1. 本地同步：

    ```bash		
    rsync -a 源目录或文件 目标目录或文件
    例如：
    rsync -a /dir1/ /dir2/     #dir1下所有文件同步到dir2下
    ```

2. 远程同步：

    ```bash
    # 将192.168.1.77服务器/etc/hosts文件拷贝到本地/dir1文件夹下
    rsync -av root@192.168.1.77:/etc/hosts /dir1/     
    ```
    
    默认是需要输入密码才能同步，因为rsync基于ssh服务
    注：免密登录，这只密钥对
    
    ```bash
    # 将dirA的所有文件同步到dirB内，并删除dirB内多余的文件   
    rsync -av --delete  dirA/ dirB/
    ```
    
    注意最后是有`/`的

##### 基本用法

1. `-r` 参数

本机使用 rsync 命令时，可以作为`cp`和`mv`命令的替代方法，将源目录同步到目标目录。

```bash
 rsync -r source destination
```

上面命令中，`-r`表示递归，即包含子目录。注意，`-r`是必须的，否则 rsync 运行不会成功。`source`目录表示源目录，`destination`表示目标目录。

如果有多个文件或目录需要同步，可以写成下面这样。

```bash
rsync -r source1 source2 destination
```

上面命令中，`source1`、`source2`都会被同步到`destination`目录。

2. `-a` 参数

`-a`参数可以替代`-r`，除了可以递归同步以外，还可以同步元信息（比如修改时间、权限等）。由于 rsync 默认使用文件大小和修改时间决定文件是否需要更新，所以`-a`比`-r`更有用。下面的用法才是常见的写法。

```bash
 rsync -a source destination
```

目标目录`destination`如果不存在，rsync 会自动创建。执行上面的命令后，源目录`source`被完整地复制到了目标目录`destination`下面，即形成了`destination/source`的目录结构。

如果只想同步源目录`source`里面的内容到目标目录`destination`，则需要在源目录后面加上斜杠。

```bash
rsync -a source/ destination
```

上面命令执行后，`source`目录里面的内容，就都被复制到了`destination`目录里面，并不会在`destination`下面创建一个`source`子目录。

3. `-n` 参数

如果不确定 rsync 执行后会产生什么结果，可以先用`-n`或`--dry-run`参数模拟执行的结果。

```bash
rsync -anv source/ destination
```

上面命令中，`-n`参数模拟命令执行的结果，并不真的执行命令。`-v`参数则是将结果输出到终端，这样就可以看到哪些内容会被同步。

4. `--delete` 参数

默认情况下，`rsync` 只确保源目录的所有内容（明确排除的文件除外）都复制到目标目录。它不会使两个目录保持相同，并且不会删除文件。如果要使得目标目录成为源目录的镜像副本，则必须使用`--delete`参数，这将删除只存在于目标目录、不存在于源目录的文件。

```bash
rsync -av --delete source/ destination
```

上面命令中，`--delete`参数会使得`destination`成为`source`的一个镜像。
