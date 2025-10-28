参考csdn博主：https://blog.csdn.net/weixin_35695879/article/details/85254422?ops_request_misc=%257B%2522request%255Fid%2522%253A%25229c15325e681b44aed5c062fca6ccd888%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=9c15325e681b44aed5c062fca6ccd888&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-85254422-null-null.142^v102^pc_search_result_base5&utm_term=ros%2Bvscode&spm=1018.2226.3001.4187



## 配置环境
包括头文件目录的配置，catkin_make命令的配置，GDB debug的配置，以及ROS插件

### vscode头文件目录配置

1. 安装“c/c++”插件
2. 生成c_cpp_properties.json
    
    根据cpp文件include报错，在.vscode文件夹中生成文件
3. 输出编译命令文件
    可能还存在找不到头文件的时候

    命令行
```
catkin_make -DCMAKE_EXPORT_COMPILE_COMMANDS=Yes
```
修改后的文件内容

    {
        "configurations": [
            {
                "name": "Linux",
                "includePath": [
                    "${workspaceFolder}/**"
                ],
                "defines": [],
                "compilerPath": "/usr/bin/gcc",
                "cStandard": "c11",
                "cppStandard": "c++17",
                "intelliSenseMode": "clang-x64",
                "compileCommands": "${workspaceFolder}/build/compile_commands.json"
            }
        ],

        "version": 4
    }


#### ROS+VSCODE

使用vscode打开工作空间会输出一个compile_commands.json文件在ROS工作空间的build文件夹下面

在命令行中输入

```
catkin_make -DCMAKE_EXPORT_COMPILE_COMMANDS=Yes

```

修改.json文件

```
{
    "configurations": [
        {
            "name": "Linux",
            "includePath": [
                "${workspaceFolder}/**"
            ],
            "defines": [],
            "compilerPath": "/usr/bin/gcc",
            "cStandard": "c11",
            "cppStandard": "c++17",
            "intelliSenseMode": "clang-x64",
            "compileCommands": "${workspaceFolder}/build/compile_commands.json"
        }
    ],

    "version": 4
}

```

#### catkin_make设置

vscode没有内置make功能，需要借助Task功能进行配置

Ctrl+shift+P进入命令模式，键入tasks: Configure Task

此时会在.vscode文件夹下面自动生成task.json文件，如下所示

```
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "catkin_make", //代表提示的描述性信息
            "type": "shell",  //可以选择shell或者process,如果是shell代码是在shell里面运行一个命令，如果是process代表作为一个进程来运行
            "command": "catkin_make",//这个是我们需要运行的命令
            "args": [],//如果需要在命令后面加一些后缀，可以写在这里，比如-DCATKIN_WHITELIST_PACKAGES=“pac1;pac2”
            "group": {"kind":"build","isDefault":true},//代表将我们定义的这个task添加到build组里面，这样就可以中Ctrl+Shift+B快捷键来找到编译命令
            "presentation": {
                "reveal": "always"//可选always或者silence，代表是否输出信息
            },
            "problemMatcher": "$msCompile"
        },
    ]
}


```

参考博客：https://blog.csdn.net/weixin_35695879/article/details/85254422

rviz
rosrun rviz rviz -d $(rospack find turtle_tf)/rviz/turtle_rviz.rviz

没有yaml文件
udo apt install python-is-python3

----

参考bilibili机器人工匠阿杰

终端工具terminator快捷键

CTRL+SHIIFT+E   左右分屏

CTRL+SHIIFT+O   上下分屏

CTRL+SHIIFT+W   关闭分屏

ALT + 方向键    移动焦点