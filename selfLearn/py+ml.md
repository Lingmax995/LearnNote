### 变量与运算
#### 变量
变量的表示分为三种，单引号、双引号、三引号
也可以同时赋予多个变量

**注：三引号可以多行输入**

        name = "文件管理系统"
        name2 = '文件管理系统'
        long_text = """
        这是一段长文本，
        有多长的，
        是真的很长。
        """
        name1, name2, name3 = "文件", "系统", "管理"

####  运算

|   运算符    |	              描述|	              例子    |
| ---------- | ----------------- | ------------------------------ | 
|+	    |加	    |3+4=7|
|-	    |减	    |3-4=-1|
|*	    |乘	    |3*4=12|
|/	    |除	    |3/2=1.5|
|%	    |取模	    |103%100=3|
|**	    |幂	   |3**2=9|
|//	    |取整除	|10//3=3|

### 条件循环
1. if  else     /       if-elif-else
2. for / while
3. continue/break

###  数据种类

1. List

        l = [1, "file", ["2", 3.2]]
能够修改

1. Dict

        files = {"ID": 111, "passport": "my passport", "books": [1,2,3]}

在字典中的元素不像列表，字典元素是没有顺序的

3. Tuple

不可变

        files = ("file1", "file2", "file3")

4. Set

在集合中的元素，其实是没有顺序的，也没有重复

        my_files = set(["file1", "file2", "file3"])

5. 循环

查看长度，使用Len（）

也可直接将数据类型的名称放入循环，字典也能和 for 进行简化的应用。我们只需要调用 dict.items(), dict.keys(), dict.values() 

6. 自带功能

append和pop

        files = []
        for i in range(5):
            files.append("f"+str(i)+".txt") # 添加
            print("has", files)

        for i in range(len(files)):
            print("pop", files.pop())   # 从最后一个开始 pop 出
            print("remain", files)



            files = ["f1.txt", "f2.txt"]

            # 扩充入另一个列表
            files.extend(["f3.txt", "f4.txt"])
            print("extend", files)

            # 按位置添加
            files.insert(1, "file5.txt")     # 添加入第1位（首位是0哦）
            print("insert", files)

            # 移除某索引
            del files[1]
            print("del", files)

            # 移除某值 
            files.remove("f3.txt")
            print("remove", files)

字典也存在

        files = {"ID": 111, "passport": "my passport", "books": [1,2,3]}

        # 按key拿取，并在拿取失败的时候给一个设定好的默认值
        print('files["ID"]:', files["ID"])
        print('files.get("ID"):', files.get("unknown ID", "不存在这个 ID"))

        # 将另一个字典补充到当前字典
        files.update({"files": ["1", "2"]})
        print('update:', files)

        # pop 调一个item，和列表的 pop 类似
        popped = files.pop("ID")
        print('popped:', popped)
        print("remain:", files)

