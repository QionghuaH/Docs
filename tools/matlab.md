
Tools For Matlab
* 1. read json file (百度云盘 `计算机/3rd package`)
```matlab
  addpath('E:\PIR\PIR_V3.0\jsonlab-1.5'); %添加下载包的存放路径    
  fname='Data.json'; %待读取的文件名称  
  jsonData=loadjson(fname);%jsonData是个struct结构  
  pirVal=jsonData.u';
```
