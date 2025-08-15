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
