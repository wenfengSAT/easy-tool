
## 项目简介
常用工具合集、常用资料汇总、常用代码、SQL汇总等。

## 项目结构

```
easy-tool  
│
├── css                             
│       └── vue                     // docsify依赖样式
│
├── js                              
│       └── docsify.min             // docsify源码          
│       └── docsify-copy-code.min   // docsify源码                   
│       └── emoji                   // emoji表情解析  
│       └── search                  // 查找插件     
│       └── zoom-image              // 图片缩放插件            
│       └── prism-bash.min          // bash代码渲染插件              
│       └── prism-c.min             // c代码渲染插件
│       └── prism-cpp.min           // c++代码渲染插件
│       └── prism-java.min          // java代码渲染插件
│       └── prism-python.min        // pathon代码渲染插件
│
├── images 
│
├── docs                            
│       └── images                      
│       └── clean-code.md           // 《代码整洁之道》            
│       └── coding-interview.md     // 《Java基础》              
│       └── effective-coding.md     // 《阿里巴巴 Java 开发手册》
│       └── effective-java.md       // 《Effective Java》 
│       └── wechat-weapp.md         // 微信小程序开发资源汇总
│       └── git-commit-rule.md      // GIT提交规范
│       └── online-tools.md         // 常用在线工具            
│       └── sql-common.md           // 常用SQL
│       └── ui-common.md            // wenfengSAT-UI
│
├── _coverpage.md                   // 文档简介
├── _navbar.md                      // 文档顶部菜单定义
├── _sidebar.md                     // 文档左侧菜单定义
├── index.html                      // 文档入口
├── README.md                       // 文档首页
```

## 简单发布

```bash

# 克隆项目
git clone https://github.com/wenfengSAT/easy-tool.git

# 切换个人分支
git checkout feat-xxx

# 提交代码
git add .
git commit -m '提交信息'

# 代码推送
git push -u origin feat-xxx

# 请求合并


```



