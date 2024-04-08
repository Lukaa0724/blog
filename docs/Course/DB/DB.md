# 数据库系统

主要关于实验五 [图书管理系统](https://www.yuque.com/yingchengjun/ozqlqv/gnwbgi9my2ci7has?singleDoc=#abv8Q)

这里记录一些问题及其解决

## IDEA的安装
程序的安装倒是没有那么困难，困难的地方在于**学生认证**和**Vim**插件安装，
学生认证不能直接使用邮箱认证或者Github学生认证，也不知道问题出在哪里，因此只能采用文件认证，
把学信网的报告传上去，还有一些其他的操作，由于我刚刚认证，还没通过，不知道后续情况如何。

### Vim 插件
[全网最详细IDEAvim配置(.ideavimrc)](https://blog.csdn.net/Leivzy/article/details/132001375)，关于Vim的插件的设置
主要参考了这个文档，刚刚安装的时候发现进不去插件市场，可能是梯子的问题吧。
Settings里面有关于HTTP的设置，不太懂就先放过去了。

在安装插件的时候，一定不要只安装`IdeaVim`，只安装这个是无法修改ideavimrc的映射的，真的好难受，这个问题找了好久找不到
答案。而后`jj` `jk` `kk`全部映射到ESC，还是非常好用的。

除此以外，我觉得IDEA的Vim插件简直无敌。当Vim的快捷键和IDEA的快捷键冲突时，会让用户**自己**选择这个快捷键干什么。
比如我们习惯`CTRL + A`全选，但是Vim的快捷键和我们的全选冲突，在IDEA里就可以选择保留全选功能，此外`CTRL + C` `CTRL + V`
也是同理，让人感觉非常舒适。此外，对于我们中文用户，在中文输入法时输入jj就会非常难受，但是其Vimrc文件可以配置数据jj
自动切换英文输入法，简直无敌了。后续应该还有很多的高级功能，比*VSCode*更强。

### 自动补全关闭
码代码的时候我还以为Copilot直接复制过来了，结果是IDEA有自己的代码补全，非常难受，使用[idea关闭代码自动提示
](https://blog.csdn.net/wldds/article/details/98517106)，关掉即可。

## MySQL的使用 以及 SQL语法的补充
数据库 banking [一键建库](https://blog.csdn.net/sandalphon4869/article/details/90722996)

[简单的SQL语法速查](https://www.yiibai.com/jdbc/jdbc-sql-syntax.html)

> set password for 'root'@localhost = 'XXXX';

修改账户密码

## JDBC的使用
主要参考了[JDBC快速入门教程](https://www.yiibai.com/jdbc/jdbc_quick_guide.html)，简单而且通俗易懂。

根据教程写下了查询代码
```java
import java.sql.*;

public class FirstExample {
    static final String JDBC_DRIVER = "com.mysql.jdbc.Driver";
    static final String DB_URL = "jdbc:mysql://localhost:3306/banking?user=root";

    static final String USER = "root";
    static final String PWD = "123456";

    public static void main(String[] args) {
        Connection conn = null;
        Statement stmt = null;
        try{
            // register
            Class.forName("com.mysql.jdbc.Driver");

            // connect to the database
            System.out.println("Connect to database");
            conn = DriverManager.getConnection(DB_URL, USER, PWD);

            // excute
            System.out.println("Creating statement ...");
            stmt = conn.createStatement();
            String sql;
            sql = "select branch_name, account_number, balance from account";
            ResultSet rs = stmt.executeQuery(sql);

            while(rs.next()) {
                String branch_name = rs.getString("branch_name");
                String account_number = rs.getString("account_number");
                int balance = rs.getInt("balance");

                // display the values
                System.out.println("Branch_name is " + branch_name);
                System.out.println("Account_number is " + account_number);
                System.out.println("Balance is " + balance);
            }

            // close the recourse
            rs.close();
            stmt.close();
            conn.close();
        }catch(SQLException se) {
            // handle errors for JDBC
            se.printStackTrace();
        }catch(Exception e){
            e.printStackTrace();
        }finally {
            try{
                if(stmt != null)
                    stmt.close();
            }catch(SQLException se2){
                // do nothhing
            }

            try{
                if(conn != null)
                    conn.close();
            }catch(SQLException se3){
                se3.printStackTrace();
            }
            // end finally
        }
        // end try
        System.out.println("What can I say? The program out!");
    }
    // main end
}
// FirstExample class end
```
当然这里写的时候也存在的一定的问题

### 数据库驱动的配置
主要参考了[idea如何配置数据库驱动，使用jdbc连接mysql5](https://blog.csdn.net/C19150872001/article/details/124134509)，
在这其中，Maven仓库提供了`jar` `pom`文件，我猜测这两种方法都可以实现对于驱动的配置，jar文件通过直接导入项目进行实现，pom文件
通过设置依赖来下载到项目中（本次实验框架也是通过pom来实现），右键项目，找到Maven，reload项目即可实现依赖的下载。

### URL的设置
在WorkBench中右键账户，`Copy JDBC Connection String`即可，需要注意的是，此时复制下来的连接`jdbc:mysql://localhost:3306/?user=root`，并没有制定数据库，会导致`java.sql.SQLException: No database selected`的错误，
因此需要在**？**前添加数据库名称，正确格式为
> static final String DB_URL = "jdbc:mysql://localhost:3306/banking?user=root";

### Warning Establishing SSL connection without 
原因是MySQL在高版本需要指明是否进行SSL连接。解决方案如下：
> static final String DB_URL = "jdbc:mysql://localhost:3306/banking?user=root&&useSSL=false";

在代码后添加`&&useSSL = false`表示不使用SSL连接，这样就没有Warning了

### PreparedStatement 练习
```java title="pratice of PreparedStatement"
import java.sql.*;

public class FirstExample {
    static final String JDBC_DRIVER = "com.mysql.jdbc.driver";
    static final String DB_URL = "jdbc:mysql://localhost:3306/banking?user=root&&useSSL=false";

    static final String USER = "root";
    static final String PWD = "123456";

    public static void main(String[] args) {
        Connection connect = null;
        PreparedStatement state = null;

        try{
            // there maybe some errors and we must add
            // 'catch(Exception s)'
            Class.forName("com.mysql.jdbc.Driver");

            // connect to the database
            System.out.println("Connect to our database 'banking'");
            connect = DriverManager.getConnection(DB_URL, USER, PWD);

            // set our preparedStatement
            System.out.println("Create our statement");
            String sql = "update account set balance = ? where account_number = ?";
            state = connect.prepareStatement(sql);

            // bind the values
            // 注意类型的匹配，并且要清楚 标号从一开始
            state.setInt(1,10);
            state.setString(2, "A-101");

            int rows = state.executeUpdate();
            System.out.println("Rows impacted : " + rows);

            sql = "select * from account";
            ResultSet rs = state.executeQuery(sql);

            while(rs.next()) {
                String account_number = rs.getString("account_number");
                String branch_name = rs.getString("branch_name");
                int balance = rs.getInt("balance");

                System.out.println("account_number is " + account_number);
                System.out.println("branch_name is " + branch_name);
                System.out.println("balance is " + balance);
            }

            state.close();
            connect.close();

        }catch(Exception e) {
            System.out.println("Register is in error!");
        }
        finally{

        }
        System.out.println("The program is end!");
    }
}
```

# Vim插件问题