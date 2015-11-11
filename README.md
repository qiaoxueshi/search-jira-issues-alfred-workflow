# Search Jira Issues - Alfred 2 Workflow


该 Workflow 改自[Search Jira Issues](https://github.com/swissmanu/search-jira-issues-alfred-workflow), 主要是在它的基础上支持了 HTTP 服务器的验证。它的主要作用是可以在 Alfred 2 里直接查看 JIRA 上的 issue，查询条件和身份验证信息可以通过配置文件指定，使用如图：

![Workflow](screenshots/workflow.png)
![Workflow](screenshots/workflow.png)

##安装
1. 使用 brew 安装依赖库
```bash
$ brew install curl jsawk
```

2. 双击 jira.alfredworkflow 文件安装

3. 打开 Alfred -> Workflows -> JIRA, 右键 “Show in Finder”，找到 workflow 对应的文件夹, copy 一份 config.sample.json 文件为 config.json

4. 修改 config.json 里的

| Item              |    Value |
| :--------         | :--------|
| authUser          | HTTP 验证用户名，比如我们的是 waterboy |
| authPassword      | HTTP 验证密码 |
| jiraUser          | JIRA 登陆账号 |
| jiraPassword      | JIRA 登陆密码|
| jiraUrl           | JIRA的地址，唱吧内部员工填 http://jira.changbagroup.com|
| maxResults        | 最多一次显示多少结果，比如50|
| emptySearchJql    | 默认的搜索语句, 比如我的是 `"project = 'IP' and affectedVersion = 'v7.0' and status  != Resolved && status != Closed && assignee=qiaoxueshi"`|
| searchJql         | 条件查询语句，查询语句是 `"project = 'IP' and affectedVersion = 'v7.0' AND (text~'{query}') && assignee=qiaoxueshi"`， 让我们输入“jira 视频特效”时, 查询语句中的 `{query}` 会被替换为“视频特效”，查询出所有 7.0 版本 iOS 项目的任务中包含“视频特效“的 issues|

5. 呼出 Alfred 2，键入 ”jira“ 或者 ”jira 关键字” 就会显示出搜索结果

> PS:
具体的搜索语句可以在 JIRA 上通过 ”问题” -> "搜索问题"，选择要搜索的条件后，点击上方 “切换到高级搜索模式”，就会在右侧显示出 JQL，copy 到上方 emptySearchJql 处即可。
