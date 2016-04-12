title:【Java】基于JDBC的学生会管理应用




# 开发环境配置

- [Mac下配置J2EE开发环境](http://www.jikexueyuan.com/course/465.html)
- [chmod shell命令详解](http://blog.csdn.net/codingkid/article/details/6567831)

![](http://7xi6qz.com1.z0.glb.clouddn.com/djlblogapache.png)

# 需求分析

## 系统管理员模块
## 学生会干部信息管理模块
## 财务管理模块
## 日常事务管理模块
## 文件管理模块



# 数据库设计

## 1．建立数据库


create table User（


	DepMemSum  int(20)		null,
# 技术点分析



# 开发步骤

## 工程解释：

 - jkxystudent
    - src
       - com.jkxy.conn（数据库连接类）
       - com.jkxy.model（数据模型类）
       - com.jkxy.service（数据操作服务类）
       - com.jkxy.test（测试类）
    - JRE Library（Java库函数，JRE包资源）
    	- mysql-connector-java-5.1.12-bin.jar
    	- ...
    - WebRoot
       - css （前端界面样式）
       - .jsp （前端Web界面）
       
       
       
## 程序入口：

- index.jsp  -> validate.jsp，根据用户在index.jsp表单中提交的数据，生成com.jkxy.model.userTable实例，调用com.jkxy.service.userservice类，从数据库中验证管理员信息，判定是否准许登陆。登陆成功则跳转至menu.jsp，登陆失败则跳转至error.jsp。
- menu.jsp里面有四个分类，根据系统功能需求分为：1、学生会干部信息管理 。2、财务管理。3、部门管理。4、事务管理。这四个大模块。
- （1）`进入学生会干部信息管理模块`，对应跳转至main_people.jsp,之后能看到页面分成了三大块，左边是信息管理功能菜单栏，对应main_left.jsp，右边是数据操作栏，对应main_right.jsp，上方是一个消息轮播栏，对应top.jsp。注意，main_people.jsp中除了引入上述几个页面外，还引入了islogin.jsp文件，这个文件是用来从session中判断管理员是否登陆成功，没登陆直接访问的用户将被强制跳转到登录页。
- `左侧功能菜单`：First_inputstuinfo.jsp对应录入学生干部信息操作，First_displaystuinfo.jsp对应查看学生干部信息操作，First_modifystuinfo.jsp对应修改学生干部信息操作，First_deletestuinfo.jsp对应删除学生干部信息操作，First_exit.jsp对应退出系统操作。
-  `进入学生会干部信息录入页`，按照表单填写，点击提交，调用post方法，提交数据到First_inputstuinfo_result.jsp 中进行com.jkxy.model.stuInfo和com.jkxy.service.stuInfoService的java类调用，将新录入的学生会干部信息数据存储在数据库中，返回成功/失败的用户提示信息。
- `进入学生会干部信息查询页`，调用com.jkxy.service.stuInfoService数据操作类，将数据库中存储的学生会干部信息用数据迭代器Iterator通过List形式递归输出，打印在First_displaystuinfo.jsp中。
- `进入学生会干部信息修改页`，这里逻辑稍微复杂一点，首先进入的是First_modifystuinfo.jsp进行所有信息的表格遍历，在每条信息背后都有一个“修改”按钮，点击“修改”后进入First_modifyOneStu.jsp，针对其中一条数据进行修改，修改后提交至First_modifyOneStu_result.jsp中调用com.jkxy.model.stuInfo和com.jkxy.service.stuInfoService方法进行数据重写，存储更新至数据库，再根据成功/失败反馈给用户提示信息。
- `进入学生会干部信息删除页`，和上面修改很类似，首先先将所有信息进行表格遍历，在每条信息背后都有一个“删除”按钮，点击“删除”后进入First_deleteOneStu.jsp，进行学生信息数据的删除。
- （2）财务管理

       
# 参考资料
- [VideoStudio](http://my.jikexueyuan.com/2964203668/record/)