### 一、apk介绍

> APK是Android Package的缩写，即Android application package文件或Android安装包。每个要安装到Android平台的应用都要被编译打包为一个单独的文件，扩展名为 .apk

在对apk进行初步的**拆包**（解压）之后，可获得：

 **AndroidManifest.xml**  程序全局配置文件
  **classes.dex**                  Dalvik字节码
  **resources.arsc**            编译后的二进制资源文件
  **META-INF**                     该目录下存放的是签名信息
  **res**                                 该目录存放资源文件
  **assets**                            该目录可以存放一些配置文件

##### 下面对这些文件和目录做些基本的注释和介绍：

**• AndroidManifest.xml**
  该文件是每个apk应用程序都必须包含的文件，它描述了应用程序的名字、版本、权限、引用的库文件等等信息。
**• classes.dex文件** 
  classes.dex是java源码编译后生成的java字节码文件。dex是Dalvik VM executes的全称，即Android Dalvik执行程序。利用解析工具可以将其转换成java来加以阅读和理解。
**• resources.arsc** 
  编译后的二进制资源文件。在做主题美化时要常与这个文件打交道。
**• META-INF目录** 
  META-INF目录下存放的是签名信息，有三个签名文件，用来保证apk包的完整性和系统的安全。在eclipse编译生成一个apk包时，会对所有要打包的文件做一个校验计算，并把计算结果放在META-INF目录下。这就保证了apk包里的文件不能被随意替换。比如拿到一个apk包后，如果想要替换里面的一幅图片，一段代码， 或一段版权信息，想直接解压缩、替换再重新打包，基本是不可能的。如此一来就给病毒感染和恶意修改增加了难度，有助于保护系统的安全。
**• res目录** 
  res目录存放资源文件。包括图片，字符串等等。res下有若干个子目录，主要为drawable，layout，xml。
解包后，几乎所有可能的修改和编辑工作基本都在这里。汉化ROM的主要工作就在这里。汉化ROM实际上就是汉化所有的apk应用程序的字符文件。
**• assets目录**
  assets目录可以存放一些配置文件，这些文件的内容在程序运行过程中可以通过相关的API获得。

### 二、Android逆向工具：Androguard

> Androguard 是使用 Python 编写的逆向工具，它可以在多个平台上运行 Linux/Windows/OSX。使用它可以反编译 android 应用，也可以用来做 android app 的静态分析（static analysis）

```bash
#以下基于linux系统（kali linux）
#获取androguard源码
git clone https://github.com/androguard/androguard.git  

#安装androguard到python库
cd androguard                                           
python setup.py install

#使用pip安装androguard(首选这个安装方式，任选一个)
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple androguard
python3 -m pip install androguard --upgrade  
apt-get install androguard    #kali linux自带androguard工具 （kyyds）
```
