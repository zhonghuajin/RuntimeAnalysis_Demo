# RuntimeAnalysis_EducationalVersion

---

RuntimeAnalysis是本人基于10多年工作遇到的问题的经验总结，原创开发的一套的源码分析工具套件，可应用于源码阅读分析、系统重构、软件国产化、二次开发、BUG定位等场景。

RuntimeAnalysis目前支持以下语言：

1. c。项目地址；https://github.com/zhonghuajin/RuntimeAnalysis_C_CPP

2. c++。项目地址；https://github.com/zhonghuajin/RuntimeAnalysis_C_CPP

3. objective-c（理论上支持，没验证）。项目地址；https://github.com/zhonghuajin/RuntimeAnalysis_C_CPP

4. js\ts（包含vue\react\Angular的支持）。项目地址；https://github.com/zhonghuajin/RuntimeAnalysis_JS

5. go。项目地址：https://github.com/zhonghuajin/RuntimeAnalysis_GO

6. java（对andriod的支持不完整）。动态插桩项目地址：https://github.com/zhonghuajin/RuntimeAnalysis_JAVA_D；静态插桩项目地址：https://github.com/zhonghuajin/RuntimeAnalysis_JAVA；安卓插桩项目地址：https://github.com/zhonghuajin/RuntimeAnalysis_FRIDA

7. c#。项目地址：https://github.com/zhonghuajin/RuntimeAnalysis_CSHARP

8. python。项目地址：https://github.com/zhonghuajin/RuntimeAnalysis_PYTHON

9. rust。项目地址：https://github.com/zhonghuajin/RuntimeAnalysis_Rust

RuntimeAnalysis的核心概念是场景，场景定义为某个操作触发系统的一系列相应。

通过RuntimeAnalysis可以捕捉基于上述语言实现的系统、框架、第三方库在各种场景下的响应，获得场景触发的核心源码，并对源码做出分析、展示。

RuntimeAnalysis工作套件主要包含插桩、日志解析、日志分析三部分，本项目（RuntimeAnalysis_EducationalVersion）简化了RuntimeAnalysis工具套件中日志分析的功能，只提供源码分析结果的例子，用于展示RuntimeAnalysis分析源码的效果。<mark>具体针对各种语言的分析请使用上面列表提供的对应的工具。</mark>

## 体验方法：

### 自行搭建环境

1. 执行call_logs.sql文件(<mark>不支持mysql 8，请使用mysql 5.7</mark>)
   
   ```sql
   mysql --max_allowed_packet=500M -u root -p call_logs < call_logs.sql
   ```

2. 启动程序
   
   ```
   java -jar logs-analysis-1.0.jar
   ```
   
   系统启动后，通过浏览器访问 http://localhost:8087

3. 选择语言及场景查看各种场景触发的核心代码
   
   点击下拉菜单，选择场景即可观看各种场景涉及的核心代码的解析。
   
   ![ ](https://github.com/zhonghuajin/RuntimeAnalysis_EducationalVersion/blob/master/%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E.png)

---

## 补充：

### 一、RuntimeAnalysis架构图

RuntimeAnalysis的核心技术路线是代码插桩。RuntimeAnalysis基于各种**语言的生态中对插桩的支持**以及**ChatGPT**，实现了各种语言的代码插桩以及源码分析相关的功能。以下是RuntimeAnalysis的架构图：

![ ](https://github.com/zhonghuajin/RuntimeAnalysis_EducationalVersion/blob/master/%E6%8F%92%E6%A1%A9%E5%A5%97%E4%BB%B6%E6%9E%B6%E6%9E%84.jpg)

### 二、github项目列表

以下是RuntimeAnalysis工具套件的github项目列表：

1. RuntimeAnalysis_JAVA_D
   
   java动态插桩；

2. RuntimeAnalysis_FRIDA
   
   andriod动态插桩；

3. RuntimeAnalysis_JAVA
   
   java静态插桩；

4. RuntimeAnalysis_LogsParser
   
   日志文件解析系统；

5. logs-analysis-backend
   
   后台日志分析系统；

6. logs-analysis-frontend
   
   日志分析前端展示系统；

7. RuntimeAnalysis_PYTHON
   
   python静态插桩；

8. RuntimeAnalysis_CSHARP
   
   c#静态插桩；

9. RuntimeAnalysis_C_CPP
   
   包含c、cpp、objective-c静态插桩 以及 c、cpp动态插桩的功能；

10. RuntimeAnalysis_GO
    
    go静态插桩

11. RuntimeAnalysis_JS
    
    js静态插桩

12. RuntimeAnalysis_Rust

   rust静态插桩。

### 三、示例列表

RuntimeAnalysis目前支持的语言本项目中都提供了示例：

1. **c语言**
   
   以redis 7.0.0 添加和读取一条字符串的场景为例子；

2. **c++**
   
   以mysql 8.0.26 innobase建表、innobase插入一条记录、innobase查询记录、innobase修改一条记录、innobase删除一条记录等场景为例子；

3. **js**
   
   以element-ui 2.13.0（vue）的Input-输入字符、Select-点击下拉菜单、Select-选中菜单、DatePicker-点击DatePicker、DatePicker-选择日期等场景为例子；

4. **ts**
   
   以nestjs 10.3.2 的内置sample中的mvc为例子，分析了mvc_sample-启动、mvc_sample-访问根url等场景；

5. **java**
   
   以activiti 6.0.0 的activiti-engine创建流程引擎、activiti-engine获取流程存储服务、activiti-engine获取运行时服务、activiti-engine获取流程任务、activiti-engine部署流程、activiti-engine启动流程、activiti-engine查询第一个任务、activiti-engine完成第一个任务、activiti-engine查询第二个任务、activiti-engine查询任务个数、activiti-engine关闭流程引擎等场景为例子；

6. **go语言**
   
   以k8s 1.28.2 的删除和创建pod为分析场景，分析这两个场景下kubelet、kube-scheduler、kube-controller-manager、kube-apiserver触发的核心代码；

7. **python**
   
   以jupyter_server 2.13.0 的notebook启动、创建新的notebook、执行单元格等场景为例子；

8. **c#**
   
   以ShareX截图工具的Sharex主项目-启动、ShareX主项目-截取矩形区域、ShareX主项目-截图活动窗口等场景为例子。

9. **rust**

   以bat(rust版本的cat命令)的查看文件内容等场景为例子。
