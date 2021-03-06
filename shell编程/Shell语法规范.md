## Shell语法规范

### 一、变量

1. 变量名命名规则：

   * 命名只能使用英文字母，数字和下划线，首个字符不能以数字开头。
   * 中间不能有空格，可以使用下划线（_）。
   * 不能使用标点符号。
   * 不能使用bash里的关键字（可用help命令查看保留关键字）

2. 使用变量：

   a. 通过**$**引用：`$varName` , 只能单独使用变量

   b. 通过**${}**引用：`${varName}`, 可在字符串中引用。如：`echo "hello ${userName}"`

3. 只读变量：`readonly`

   ```bash
   #!/bin/bash
   myName="ss-xiong"
   readonly myName
   ```

4. 删除变量，删除后不能引用，不可删除只读变量：`uset myName`

5. 变量类型：

   * **局部变量** 局部变量在脚本或命令中定义，仅在当前shell实例中有效，其他shell启动的程序不能访问局部变量
   * **环境变量** 所有的程序，包括shell启动的程序，都能访问环境变量，有些程序需要环境变量来保证其正常运行。必要的时候shell脚本也可以定义环境变量
   * **shell变量** shell变量是由shell程序设置的特殊变量。shell变量中有一部分是环境变量，有一部分是局部变量，这些变量保证了shell的正常运行



### 二、字符串

1. 复制给变量：单引号、双引号、不加引号 均可
2. 拼接字符串：单引号、双引号 均可
3. 获取长度：`echo ${#varName}`
4. 提取子串：`echo ${varName:1:4}`, 默认从头开始，必须指定结束位置
5. 查找子串：



### 三、数组

1. **声明数组：**在 Shell 中，用括号来表示数组，数组元素用"空格"符号分割开。定义数组的一般形式为：

   `数组名=(值1 值2 ... 值n)`

   如：

   ```bash
   # 1.
   array_name=(var1 var2 var3)
   # 2.
   array_name=(
   var1
   var2
   var3
   )
   # 3. 下标可不连续，没有限制
   array_name[0]=var1
   array_name[1]=var2
   array_name[2]=var3
   ```

2. **读取数组元素:** 

   单个元素：`array_name[0]`

   使用@可以获取数组中所有元素，例如：`echo ${array_name[@]}`

3. **获取数组长度:** 与获取字符串长度相同

   ```bash
   # 使用@符号
   length=${array_name[@]}
   # 使用*号
   length=${array_name[*]}
   # 获取单个元素的长度
   length=${#array_name[1]}
   ```

   