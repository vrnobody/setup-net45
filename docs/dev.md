#### 更新 node 运行时版本

修改 action.yml 的 runs.using

#### 开发命令

```bash
# 查看 npm 新版本
npm outdated

# 根据 package.json 规则更新包版本
npm update

# 直接更新到最新版
npm install xxx/yyy@latest
```

#### notes

npm run build 时，不用管下面这行警告：  
`(!) "this" has been rewritten to "undefined"`
