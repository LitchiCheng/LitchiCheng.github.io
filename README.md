# LitchiCheng.github.io

个人主页：<https://LitchiCheng.github.io>

## 结构

| 文件 | 作用 |
|------|------|
| `index.html` | 整站（单文件，CSS/JS 全内联，零外部依赖、零埋点） |
| `404.html` | 自定义 404 |
| `.nojekyll` | 关闭 Jekyll 处理，Pages 直接托管静态文件 |
| `_config.yml` | 仅站点元信息，见文件内注释 |

## 数据

项目列表由 `index.html` 里的 `const REPOS = [...]` 提供 —— 这是构建时从
`GET /users/LitchiCheng/repos` 导出的快照；页面加载后会再尝试用同一接口实时刷新 star /
更新时间，接口限流或离线时静态快照照常显示。

刷新快照（需要网络，可选）：

```bash
curl -s "https://api.github.com/users/LitchiCheng/repos?per_page=100&sort=pushed" \
  | python3 -c "import json,sys;print(json.dumps([{k:r[k] for k in ('name','stargazers_count','forks_count','language','pushed_at')} for r in json.load(sys.stdin)],ensure_ascii=False))"
```

## 本地预览

```bash
python3 -m http.server 8000   # http://127.0.0.1:8000
```

## 隐私

页面只展示昵称，不含邮箱、姓名、地理位置、雇主等任何个人信息；联系入口统一走 GitHub。
