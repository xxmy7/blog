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

创建指定python版本的环境

```
conda create --name your_env_name python=2.7
conda create --name your_env_name python=3
conda create --name your_env_name python=3.5
```

####列举当前所有环境

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





