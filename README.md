# Ronda 28 · 最小可部署原型

纯静态单页，没有后端、没有外部依赖（字体、脚本、样式全部内联），断网也能跑。

## 文件
- `index.html` 整个原型（默认西语，右上角可切 ES / 中文 / EN）
- `robots.txt`、`_headers` 防止被搜索引擎收录（原型阶段）

## 部署（任选一种）
- 任意静态托管：把这个文件夹整个上传，访问根路径即可（Netlify / Vercel / Cloudflare Pages / GitHub Pages / S3 / OSS 都行）。
- Nginx：`root` 指到这个文件夹，`index index.html;`。
- 本地预览：`python3 -m http.server 8080`，打开 http://localhost:8080 。

## 链接参数
- `?lang=zh` 中文打开，`?lang=en` 英文，`?lang=es` 西语（默认）。

## 演示：公开计划（社交 / KOL）
默认打开 `demoSocial: true`。顶栏在「我的计划」后面有「Planes públicos / 公开计划」。演示里有 3 个虚构认证账号的对照计划；关注后可在本局用筹码确认下注。确认只对这一局有效，不会自动复制到后面的局，也不会占用「我的计划」名额。取消则什么也不做。只能在开放下注时使用。

## 原型边界（上线前必须处理）
- 余额是演示钱包 $1,000 MXN，存在浏览器本地，不连真实账户。
- 开奖是前端 HMAC 自开奖，只用于演示；正式版必须由服务端开奖并结算。
- 多人下注热度是模拟数据，页面已标注「Datos de ejemplo (demo)」。接真实数据时设置
  `window.R28_CONFIG = { betsFeed: <真实推送适配器> }` 并去掉 `demoHeat`，接口说明见源码 heat.js。
- 公开计划同样是演示数据，已标注「Datos de ejemplo (demo)」。接真实数据时设置
  `window.R28_CONFIG = { kolFeed: <适配器> }` 并去掉 `demoSocial`，接口说明见源码 social.js。
- 不含 Pozo/Jackpot。不含自动跟注。
