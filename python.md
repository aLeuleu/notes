![image](https://user-images.githubusercontent.com/97832618/183249983-d0f7122c-d03f-4960-8d8d-d40a42834942.png)
# python : a bash-script substitute 

## **OS module**
| Syntax | Description |
| ----------- | ----------- |
| os.mkdir(*path,mode*) | mkdir + chmod| 
| os.makedirs(*path,mode*) | just like mkdir -p : creates the parents folder if neccessary | 
| os.remove(*path*) | delete file |  
| os.rmdir(*path*) | delete empty dir | 
| os.name | OS name |
| os.path.join(*path 1*, *path 2*) | useful to cat paths  |
| os.popen(*path_file*, *'w'*) | returns a file we can write into  |
|os.close| close the file|
|os.rename(*path_file*, *'new_name.txt'* )| |
|os.path.exists(*path_file*)| returns ture or false|
|os.path.getsize(*path_file*)| returns size of file in bytes|
|||



```python
# Directory 
directory = "GeeksforGeeks"
  
# Parent Directory path 
parent_dir = "D:/Pycharm projects/"
  
# Path 
path = os.path.join(parent_dir, directory) 

try:
    print("Creating directory '% s' " % directory)
    os.mkdir(path)
except OSError as error:
    print(error) 

#or
mode = 0o666
os.mkdir(path, mode)
```




### Ressources

https://www.geeksforgeeks.org/os-module-python-examples/
