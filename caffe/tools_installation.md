This file is for installation of tools/packages whithout root



1.Matlab
--------
* step1:
	* 进入存放安装文件的目录，阅读并修改'installer_input.txt'
		* destinationFolder=/snfs01/ff/Matlab/R2013a（你的安装路径，注意要写成绝对路径
		* fileInstallationKey=xxxxx-xxxxx-xxxxx-xxxxx （下载的文件里有，自己找找
		* agreeToLicense=yes
		* outputFile=/snfs01/ff/matlabinstall.log （安装日志，可有可无）
		* mode=silent （安装方式）
		* licensePath=/snfs01/ff/MatlabInstall/serial/license.lic （license文件位置，绝对路径）   
		* activationPropertiesFile=/matlab/etc/activate.ini //激活文件
	* 执行 ` ./install -inputFile installer_input.txt`
	或者  
	* ./install -mode silent -destinationFolder /DATACENTER3/qionghua.he/local/matlab/ -agreeToLicense yes -fileInstallationKey 09806-07443-53955-64350-21751-41297 licensePath /DATACENTER3/qionghua.he/packages/Matlab+2016b+Linux64+Crack/license_standalone.lic
    
* step2:用`chmod +x`赋予其可执行权限  <br>
	* chmod +x install<br>
	* chmod +x install_Unix<br>
	* 两秒钟就结束，但是没有安装，有错误但是没有提示，（看了下install和install_unix的脚本文件）。<br>
	* 解决方法：切换到安装包下对应sys/java/jre/glnx86/jre/bin/java路径，执行chmod +x java就好了。<br>
 
* step3: <br>
	* 复制R2016b_glnxa64目录下的 activate.ini 和 license_standalone.lic 到安装目录下matlab/bin下面<br>
	* 修改activate.ini文件 <br>
		* isSilent=true //开启silent模式<br>
		* activateCommand=activateOffline //设置激活方式, 离线激活 无需联网<br>
		* licenseFile=license_standalone.lic //license文件位置<br>
	* 执行 `./activate_matlab.sh -propertiesFile activate.ini`<br>
* step4:  <br>
	* 将Matlab+2016b+Linux64+Crack/R2016b/bin/glnxa64/`ibmwservices.so`复制到 安装路径matlab/bin/glnxa64/下

* step5:  <br>
	* 修改~/.bashrc<br>
		* MY_PATH="/DATACENTER2/qionghua.he/local/" <br>
		* export PATH=$PATH:$MY_PATH/matlab/bin/<br>
	* source ~/.bashrc
* step6:  <br>
	* 测试  matlab<br>
	
2.Python & Matlab
-----------------
* step1：安装
	* 在Matlab命令行输入`matlabroot` 得到matlabroot
	* Mac&Linux systems 
		* `cd "matlabroot/extern/engines/python"`
		* 'python setup.py install'
* step2：使用自带函数 `https://cn.mathworks.com/help/matlab/apiref/matlab.engine.start_matlab.html`
	* 调用matlab自带的sqrt函数
		* import matlab.engine
		* eng = matlab.engine.start_matlab()
		* A=eng.sqrt(4.)
* step3：使用用户函数 `https://cn.mathworks.com/help/matlab/matlab_external/call-user-script-and-function-from-python.html`
	* 在调用当前目录下的文件triarea.m
		* import matlab.engine
		* eng = matlab.engine.start_matlab()
		* eng.triarea(nargout=0) %没有返回参数
		* ret = eng.triarea(1.0,5.0) %带有返回参数
		
* step1：
	* 在python下安装 pip install mlab
	
* step2：调用matlab的内部函数文件
	* 新建Python文件 
		* from mlab.releases import latest_release as matlab
		* matlab.plot([2,3,4,5,8,1],'-o') #画个图
* step3: 调用matlab的自定义m函数文件
	* from mlab.releases import latest_release as matlab
	* matlab.path(matlab.path(),r'C:\Tools\mlabtest')   #'C:\Tools\mlabtest' the path of the read.m
	* data=matlab.read('input.txt') 
	
3.MXNET
----------
* step1：
	* 安装
		* `git clone -recursive https://github.com/dmlc/mxnet`
		* `cd mxnet'
		* `cp make/config.mk ./`
		* vi config.mk ：`USE_CUDA = 1` `USE_CUDA_PATH = /usr/local/cuda` 
		* `USE_BLAS = openblas` (#Line no : 93) 
    		* `ADD_LDFLAGS = -L/home_dir/openblas/lib`
    		* `ADD_CFLAGS =  -I/home_dir/openblas/include`
		* `make -j8`
	* Python 使用
		* `cd python`
		* `python setup.py install`
		* `export PYTHONPATH=~/mxnet/python` to ~/.bashrc
	* 问题1
		* cannot find cuda.h
		* vi config.mk : USE_CUDA_PATH=
	* 问题2
		* cannot find opencv2/cv.hpp
		* `locate opencv.pc`
		* export PKG_CONFIG_PATH=/path/to/lib/pkgconfig
		
4.Ice for Python
--------
* step1：
	* 安装
		* wget https://pypi.python.org/packages/7a/c2/b65a15aa0a8711708f6c39bddf52596e8d477e9e943dc70cad6f9b9c807a/zeroc-ice-3.7.0.tar.gz#md5=930b0357118906ae58bf526a5ab3c715
		* tar -zxvf *.tar.gz
		* cd zeroc-ice-3.7
		* `python setup.py install`
* step2：问题
	* 安装openssl
		* wget https://www.openssl.org/source/openssl-1.0.2m.tar.gz
		* tar -xzvf openssl-1.0.2m.tar.gz
		* cd openssl-1.0.2m
		* ./config --prefix=
		* ./config -t
		* make && make install

