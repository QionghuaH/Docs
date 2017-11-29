This is some commom code I used

Tools For Pyhton
-----------
* 1.进度条
```python
    import sys
    sys.stdout.write('{0}/{1}\r'.format(i + 1,n))
    sys.stdout.flush()
```
  
* 2.获取文件列表
```python
  def get_img_list(dir,img_list):
       if os.path.isfile(dir):
       img_list.append(dir.decode('gbk').encode('utf-8'))#.decode('gbk')
       elif os.path.isdir(dir):  
           for s in os.listdir(dir):
               newDir=os.path.join(dir,s)
               get_img_list(newDir, img_list)  
       return img_list
```
      
* 3.
```python
```
