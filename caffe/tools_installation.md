This file is for installation of tools/packages whithout root



1.Matlab
--------
* step1:进入存放安装文件的目录，阅读并修改installer_input.txt 
    destinationFolder=/snfs01/ff/Matlab/R2013a（你的安装路径，注意要写成绝对路径）
    fileInstallationKey=xxxxx-xxxxx-xxxxx-xxxxx （下载的文件里有，自己找找）
    agreeToLicense=yes 
    outputFile=/snfs01/ff/matlabinstall.log （安装日志，可有可无）
    mode=silent （安装方式）
    licensePath=/snfs01/ff/MatlabInstall/serial/license.lic （license文件位置，绝对路径）
    
    或者
    ./install -mode silent -destinationFolder /DATACENTER3/qionghua.he/local/matlab/ -agreeToLicense yes -fileInstallationKey 09806-07443-53955-64350-21751-41297 licensePath /DATACENTER3/qionghua.he/packages/Matlab+2016b+Linux64+Crack/license_standalone.lic

* step2:用chmod +x赋予其可执行权限  
    chmod +x install
    chmod +x install
    两秒钟就结束，但是没有安装，有错误但是没有提示，（看了下install和install_unix的脚本文件）。
    解决方法：切换到安装包下对应sys/java/jre/glnx86/jre/bin/java路径，执行chmod +x java就好了。
    

* step3:

