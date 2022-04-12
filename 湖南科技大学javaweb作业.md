# 湖南科技大学javaweb作业

by rick hqh  (做的垃圾,大佬勿喷)

## 项目结构



![image-20220412104245519](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204121042794.png)

![image-20220412104453428](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204121044763.png)



## 技术

1. 前端 :vue3.0 +vuerouter + elementplus
2. 后端 :spring+springmvc +mybatis

## 前端

1. 前端代码截图

   ![image-20220412102446115](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204121029584.png)

2. 前端界面展示

   ![image-20220412103354079](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204121033376.png)

![image-20220412103402292](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204121034580.png)

![image-20220412103411950](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204121034147.png)

![image-20220412103422997](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204121034211.png)

![image-20220412103427205](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204121034445.png)





## 数据库

1. 数据库代码举例(详见hqh.sql)

   ```mysql
   DROP TABLE IF EXISTS `hqh_teacher`;
   CREATE TABLE `hqh_teacher`  (
     `teacher_id` bigint(20) NOT NULL AUTO_INCREMENT COMMENT '老师ID',
     `teacher_name` varchar(30) NOT NULL COMMENT '老师账号',
     `nick_name` varchar(30)  NOT NULL COMMENT '老师昵称',
     `email` varchar(50)  NULL DEFAULT '' COMMENT '老师邮箱',
     `phonenumber` varchar(11)  NULL DEFAULT '' COMMENT '手机号码',
     `sex` char(1)  NULL DEFAULT '0' COMMENT '老师性别（0男 1女 2未知）',
     `avatar` varchar(100)  NULL DEFAULT '' COMMENT '头像地址',
     `password` varchar(100)  NULL DEFAULT '' COMMENT '密码',
     `status` char(1)  NULL DEFAULT '0' COMMENT '帐号状态（0正常 1停用）',
     `del_flag` char(1)  NULL DEFAULT '0' COMMENT '删除标志（0代表存在 2代表删除）',
     `login_ip` varchar(128)  NULL DEFAULT '' COMMENT '最后登录IP',
     `login_date` datetime NULL DEFAULT NULL COMMENT '最后登录时间',
     `create_by` varchar(64)  NULL DEFAULT '' COMMENT '创建者',
     `create_time` datetime NULL DEFAULT NULL COMMENT '创建时间',
     `update_by` varchar(64)  NULL DEFAULT '' COMMENT '更新者',
     `update_time` datetime NULL DEFAULT NULL COMMENT '更新时间',
     PRIMARY KEY (`teacher_id`) USING BTREE
   ) ENGINE = InnoDB CHARACTER SET = utf8mb4 COLLATE = utf8mb4_0900_ai_ci COMMENT = '老师信息表';
   
   -- ----------------------------
   -- 增加几条老师信息
   -- ----------------------------
   INSERT INTO `hqh_teacher` VALUES (1, 'admin', '宋浩', '253546544@qq.com', '18888888888', '0', '', 'xxxxxx', '0', '0', '10.25.245.45', '2022-01-23 15:50:27', 'admin', '2022-01-23 15:50:48', 'hqh', '2022-01-26 15:50:53');
   INSERT INTO `hqh_teacher` VALUES (2, 'zs', '张三', '253546544@qq.com', '18888888888', '0', '', 'xxxxxx', '0', '0', '10.25.245.45', '2022-01-23 15:50:27', 'admin', '2022-01-23 15:50:48', 'hqh', '2022-01-26 15:50:53');
   INSERT INTO `hqh_teacher` VALUES (3, 'ls', '李四', '253546544@qq.com', '18888888888', '0', '', 'xxxxxx', '0', '0', '10.25.245.45', '2022-01-23 15:50:27', 'admin', '2022-01-23 15:50:48', 'hqh', '2022-01-26 15:50:53');
   ```

   

2. 数据库截图

![image-20220412103754973](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204121037137.png)



## 后端

1. 后端接口

   ![image-20220412104631149](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204121046436.png)

   ![image-20220412104635678](https://cdn.jsdelivr.net/gh/rickhqh/pic/img/202204121046890.png)

2.后端web.xml



```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">
    <!--容器初始化时，负责启动spring容器  配置spring 的监听器-->
    <listener>
        <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
    </listener>
    <!--加载springmvc.xml配置文件-->
    <context-param>
        <param-name>contextConfigLocation</param-name>
        <param-value>classpath:application.xml</param-value>
    </context-param>
    <!--配置前端过滤器-->
    <!--注册DispatcherServlet，这是springmvc的核心，就是个servlet 启动服务器-->
    <servlet>
        <servlet-name>springmvc</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>classpath:application.xml</param-value>
        </init-param>
        <!--加载时先启动-->
        <load-on-startup>1</load-on-startup>
    </servlet>

    <!--/ 匹配所有的请求；（不包括.jsp）-->
    <!--/* 匹配所有的请求；（包括.jsp）-->
    <servlet-mapping>
        <servlet-name>springmvc</servlet-name>
        <url-pattern>/</url-pattern>
    </servlet-mapping>
</web-app>

```



## 项目运行

1. 前端运行 在hqh-ui 子项目下

   npm install

   npm run serve

2. 后端运行 在system-admin 子项目下 

   启动tomcat