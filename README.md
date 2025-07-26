# MemoFlux ADVX（AdventureX 2025）参赛项目

*该仓库为主仓库，在您git clone**主仓库**之后您需要执行额外的命令。*

```
git clone https://github.com/TokiyaSzk/MemoFlux.git
cd MemoFlux
git submodule update --init --recursive
```

*主仓库并不会自动更新子模块的提交，更新引用可以执行额外命令*

```
cd MemoFluxServer
git pull origin main
cd ..
cd MemoFluxIOS
git pull origin main
git add . 
git commit -m "Update server & client submodule to latest version"
git push
```

## ReMake 重新发明

## 赛道
- Paraflow 没有设计师
- Kimi For Vibe Coding
- YouWare 脑洞狂欢节：召唤未来AI App
- 让AI真正进入生活，生活中的每个需求都能被开发者重做一次。
