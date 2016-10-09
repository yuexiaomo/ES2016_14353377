# ES2016_14353377

# linux环境下DOL的配置

## DOL配置

#### Description

> **Distributed operation layer (DOL)** is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.

## How To Install

#### 安装必要环境
    ```$ sudo apt-get update```
    ```$ sudo apt-get install ant```
    ```$ sudo apt-get install openjdk-7-jdk```
    ```$ sudo apt-get install unzip```
    
#### 下载文件

    ```$ sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz```
    ```$ sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip```

#### 解压文件

1.  新建dol的文件夹
    ```$  mkdir dol```
2.  将dolethz.zip解压到 dol文件夹中
    ```$ unzip dol_ethz.zip -d dol```
3.  解压systemc
    ```$ tar -zxvf systemc-2.3.1.tgz```
    
#### 编译systemc

1.  解压后进入systemc-2.3.1的目录下
    ```$ cd systemc-2.3.1```
2.  新建一个临时文件夹objdir
    ```$ mkdir objdir```
3.  进入该文件夹objdir
    ```$ cd objdir```
4.  运行configure（能根据系统的环境设置一下参数，用于编译）
    ```$ ../configure CXX=g++ --disable-async-updates```
    下图为运行configure之后的截图    
  ![build后]  (http://a2.qpic.cn/psb?/V10NR5mM4fLmXX/ezRIMKbNh8IYeO3NJpACFMzEof4fO8xhfyQzVcez0vc!/m/dAkBAAAAAAAAnull&bo=dQLzAAAAAAADB6Y!&rf=photolist&t=5)
5.  编译
    ```$ sudo make install ```
    编译完后文件目录如下(`$cd ..`      `$ls`)    
    ![目录](http://a2.qpic.cn/psb?/V10NR5mM4fLmXX/5PLourpZKGwPheMjGkOd.MeNBRxahRB*t.3nEnpwdo0!/m/dAkBAAAAAAAAnull&bo=ZgJ.AAAAAAADBzg!&rf=photolist&t=5)
6.  记录当前的工作路径（会输出当前所在路径，**提前记下**）
    /home/xiaomo/systemc-2.3.1

#### 编译dol

1.  进入刚刚的dol文件夹，修改build.xml文件    找到下面这段话，就是说上面编译的systemc位置在哪里
    > property name=”systemc.inc” value=”YYY/include”      property name=”systemc.lib” value=”YYY/lib-linux/libsystemc.a”/
    把YYY改成上页结果（**对于64位系统,lib-linux要改成lib-linux64**）
2.  编译
     ```$ ant -f build_zip.xml all ```
    若成功会显示build sucessful.  运行第一个例子
    进入build/bin/main路径下
    `$ cd build/bin/main`
    然后运行第一个例子
    `$ ant -f runexample.xml-Dnumber=1 `

成功结果如图所示

![最终结果](http://a3.qpic.cn/psb?/V10NR5mM4fLmXX/DY2NAe8SpifbPNZ0Ei1BLnVlKtBhsnkJzBk3ptIL*yM!/m/dAoBAAAAAAAAnull&bo=UgG0AQAAAAADB8Q!&rf=photolist&t=5)

##感想

1.第一次实验是关于DOL配置的内容，主要按照课件文档来就好，需要注意的是对一些基础linux命令的理解和掌握，比如cd ,ls ,sudo apt-get 等。

2.第二次实验是利用Github建库，关于Github的教程可以在助教给出的链接中查到，上网也可以搜到很多。在这次zhong实验中接触到了全新的markdown语言，而在使用过程中也可以很明显的体会到这种语言在简洁性方面的优势，随时预览的功能也很方便。同时也学会了一些markdown相关语法，难度不大。

3.在写readme时，比较纠结的是图片的上传问题，开始时受网上一些博客启发，想要在库下创建一个装图片的文件夹，可是创建好了之后发现把照片传上来很困难，又想到最终图片以网站链接形式引入，只要传上网就好，于是分享到了QQ空间，有点low，但是效率还是蛮高的。
