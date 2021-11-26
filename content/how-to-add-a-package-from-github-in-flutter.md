# 如何从github导入包?
[How to add a package from GitHub in Flutter?](https://stackoverflow.com/questions/54022704/how-to-add-a-package-from-github-in-flutter)

___



> 1

**1. 本地保存在某个文件夹**

```yaml
dependencies:
  library_name:
   path: /path/to/library_name
```

------

**2.  Github, Gitlab etc.**

```yaml
dependencies:
  library_name:
   git: https://github.com/username/library_name
```

target exact branch

```yaml
dependencies:
  library_name:
   git:
    url: https://github.com/username/library_name.git
    ref: dev    #branch name
```

 target exact commit

```yaml
dependencies:
  library_name:
   git:
    url: https://github.com/username/library_name.git
    ref: e234072340    #commit reference id
```

Where '*library_name*' has to be the same as the '*name*' declared in pubspec.yaml of that pub.





