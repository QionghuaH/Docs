LINUX PROBLEM
--------
* 问题1.bash:./configure /bin/sh^M: bad interpreter: No such file or directory
	* 原因：configure文件是dos格式的，怎么转换成unix格式的呢？
	* 解决：这就要用到vi的强大功能了：
		* vi configure
  * :set ff=unix
  * :wq
* 问题2.Perhaps you should add the directory containing `opencv.pc'
	* 解决 export PKG_CONFIG_PATH=/cv/lib:$PKG_CONFIG_PATH
