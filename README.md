# zhaoshuai-sup.github.io
## .gitignore的目的
### themes
保存主题样式的文件  
主题用其他的仓库管理
所以在.gitignore中忽略它
### .deploy_git
```hexo d``` 自动生成的文件夹，用于部署项目
### public
public是公开展示的渲染文件资源  
通过```hexo g```生成，```hexo d``` 自动提交到主页分之上，不是该提交到后台管理分之上的资源