#### 操作系统(OperatingSystem,os)
	管理和控制计算机硬件与软件资源的计算机程序;
	直接运行在“裸机”上的最基本的系统软件;
	任何其他软件都必须在操作系统的支持下才能运行。

#### Linux中最重要的操作方式--命令行
命令对于熟练使用Linux/Unix系统而言是必不可少的;
命令行应用的可扩展性、灵活性更好;
打破了使用Windows时一个鼠标“一点到底”的简单与乏味，它提供给用户更大的灵活性与想象空间;
命令已成为Linux/Unix的典型标志，也已成为Linux/Unix的魅力所在。

#### 常用命令

- sudo apt -get update 重新载入软件目录
- sudo 权限不够的话
- pwd 查看当前路径
- ls 查看当前路径存在的文件和文件夹
- cd 进如文件夹
- cd.. 进入上一个文件夹
- mkdir + 文件夹名  创建文件夹
- touch + 文件名  创建文件
- mv +文件+路径   ：剪切文件 
- cp +文件名+路径+新文件名  ：复制文件
- rm 文件名 删除文件
- rm -r +文件夹名 删除文件夹
- --help  查看使用方法


**查看与搜索**​

- `cat`：显示文件内容
- `less`/`more`：分页查看大文件（支持上下翻页）
- `head`/`tail`：查看文件头/尾部（`tail -f` 实时跟踪日志）
- `grep`：文本搜索（`-i` 忽略大小写，`-r` 递归目录）
- `find`：按条件查找文件（如 `find /home -name "*.log"`


## VMware Tools 安装详细教程（Ubuntu 虚拟机）
https://blog.csdn.net/fuhanghang/article/details/150951043?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-1-150951043-blog-140187119.235^v43^pc_blog_bottom_relevance_base4&spm=1001.2101.3001.4242.2&utm_relevant_index=3