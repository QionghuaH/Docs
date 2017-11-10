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
* step2:用chmod +x赋予其可执行权限  
    chmod +x install
    

* step3:

