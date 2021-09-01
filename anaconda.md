# Anaconda安装指南

## 注意事项

* **尽量不要混用`conda install`与`pip install`**

  使用`conda install`时会检索相关依赖，而`pip install`则不会。混用会造成`conda`环境不稳定等问题。

  当想要安装一些包时，请首先`conda install [包名称]`，如果提示没有此包，再`pip install [包名称]`。一般而言pip的包会比conda的包更全一些。

* **不要给conda添加国内镜像源**

  conda安装时会受一些原因速度比较慢（翻墙会改善此问题）。一些教程会建议为conda换用国内的镜像源以提高安装速度。

  但是国内镜像源往往存在版本落后等问题，同样会造成`conda`环境不稳定等问题。

  当conda因网络问题安装失败时建议多尝试几次。

## 什么是Anaconda？

Anaconda是一个安装、管理python相关包的软件。Anaconda自带python解释器，以及一个界面类似于matlab得IDE——Spyder。

## Anaconda具有安装管理python包的功能。

* 例如安装tensorflow，在cmd中运行

  ```bash
  conda install tensorflow-gpu
  ```

  Anaconda会自动查找tensorflow所需的相关依赖环境，安装cudatoolkit以及cudnn等组件。

* 在某些情况下可能需要在多个python环境中切换，例如一些例程只能在py2得环境下运行，此时可用Anaconda新建一个py2的虚拟环境。在cmd中运行
  * 创建名为py27的虚拟环境，并将python2.7版本安装至此环境中 

    ```bash
    conda create -n py27 python=2.7
    ```

  * 激活py27环境。（Anaconda默认环境为`base`，此环境不可被删除）

    ```bash
    conda activate py27
    ```

  * 在py27环境中安装包

    ```bash
    conda install [包名称]
    ```

## Python、Pycharm、Anaconda 三者之间的关系

[知乎链接](https://zhuanlan.zhihu.com/p/142657444)

## 安装Anaconda\(Windows 64位\)

Anaconda安装包见`/安装包/Anaconda3-2020.11-Windows-x86_64.exe`

