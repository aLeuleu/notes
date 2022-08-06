![image](https://user-images.githubusercontent.com/97832618/183249983-d0f7122c-d03f-4960-8d8d-d40a42834942.png)
# OS module in python : a bash-script substitute 
## Directories
### get the current working directorie
```python
# Get the current working 
# directory (CWD) 
cwd = os.getcwd() 
```
### create a directorie

- os.mkdir(*path,mode*)  
- os.makedirs()    

| Syntax | Description | Bash equivalent
| ----------- | ----------- | ----------- |
| os.mkdir(*path,mode*) | simply create dir with an optional access mode| mkdir ... && chmod ...
| os.makedirs(*path,mode*) | just like mkdir -p : this creates the parents folder if neccessary | mkdir -p ... && chmod ...
| os.remove(*path*) | delete file | rm ...
| os.rmdir(*path*) | delete empty dir | ?
| os.name | OS name : 
 - RISC OS
    Portable Operating System Interface (POSIX)
    OS/2
    JavaOS
    Windows Embedded Compact (CE)
    Windows NT
 | ?
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
# mode
mode = 0o666
os.mkdir(path, mode)
```

# Ressources

https://www.geeksforgeeks.org/os-module-python-examples/
