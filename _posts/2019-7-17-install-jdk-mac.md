JENV官网http://www.jenv.be/

java sdk 1.6 for mac 在苹果官网下载

https://support.apple.com/kb/DL1572?locale=zh_CN

或者

http://download.csdn.net/download/cl61917380/9932543

1.终端中查看当前系统JAVA版本

java -version
java version "1.8.0"
Java(TM) SE Runtime Environment (build 1.8.0-b132)

2.安装JAVA SDK 1.6
3.安装JENV

brew install jenv
echo 'export PATH="$HOME/.jenv/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(jenv init -)"' >> ~/.bash_profile
4.重新打开一个新的终端运行如下内容（SDK路径根据自己情况）
jenv add /Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home
jenv add /Library/Java/JavaVirtualMachines/jdk1.8.0.jdk/Contents/Home

5.查看结果
$ jenv versions
* system (set by /Users/su/.jenv/version)
  1.6
  1.6.0.65
  1.8
  1.8.0
  oracle64-1.6.0.65
  oracle64-1.8.0

jenv local oracle64-1.6.0.65
java -version
java version "1.6.0_65"
Java(TM) SE Runtime Environment (build 1.6.0_65-b14-468-11M4833)
Java HotSpot(TM) 64-Bit Server VM (build 20.65-b04-468, mixed mode)

--------------------- 
作者：coooliang 
来源：CSDN 
原文：https://blog.csdn.net/coooliang/article/details/77161649 
版权声明：本文为博主原创文章，转载请附上博文链接！
