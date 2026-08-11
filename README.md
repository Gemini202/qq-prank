# QQ 整蛊卡片 — 假情侣关系申请

在 QQ 聊天中分享一个链接，卡片看起来是**情侣关系申请**，点进去却跳到**应用市场游戏下载页**。

---

## 原理

QQ 聊天卡片显示的内容由网页的 OG（Open Graph）标签决定（标题、描述、图片），而点击后页面用 JavaScript 跳转到应用市场。QQ 不会校验二者是否一致。

---

## 快速部署（免费）

### 方式一：GitHub Pages（推荐）

1. 新建一个 GitHub 仓库，把 `index.html` 和 `heart.svg` 推上去
2. 在仓库设置中开启 **GitHub Pages**（Settings → Pages → Source: main branch）
3. 获得链接，例如：`https://你的用户名.github.io/仓库名/`

### 方式二：Vercel / Netlify

直接把项目文件夹拖进去即可。

---

## 使用

部署好之后，你的链接类似：

```
https://你的域名/qq-prank/
```

### 基础用法（默认效果）

直接分享这个链接到 QQ 私聊。对方看到的卡片：

> **申请成为你的情侣**
> 对方已向你发送情侣关系申请 💌

点进去 → 王者荣耀应用市场页。

### 自定义参数

在链接后面加 `?` 参数即可：

| 参数 | 作用 | 示例 |
|------|------|------|
| `name` | 申请者昵称 | `?name=小明` |
| `to` | 被整蛊的人 | `?to=小红` |
| `game` | 游戏包名 | `?game=com.tencent.tmgp.sgame` |
| `url` | 自定义跳转链接（会覆盖 game） | `?url=https://...` |
| `title` | 完全自定义标题 | `?title=你收到一条密信` |
| `desc` | 完全自定义描述 | `?desc=点击查看详情` |
| `delay` | 跳转延迟（毫秒，默认 2000） | `?delay=3000` |

**示例：**

```
https://你的域名/?name=老王&to=小美&game=com.tencent.tmgp.pubgmhd
```

卡片显示：「**老王 申请成为你的情侣**」，点进去跳转到和平精英下载页。

### 常用游戏包名

| 游戏 | 包名 |
|------|------|
| 王者荣耀 | `com.tencent.tmgp.sgame` |
| 和平精英 | `com.tencent.tmgp.pubgmhd` |
| 原神 | `com.miHoYo.Yuanshen` |
| 崩坏：星穹铁道 | `com.miHoYo.hkrpg` |
| 蛋仔派对 | `com.netease.party` |
| 英雄联盟手游 | `com.tencent.lolm` |
| 金铲铲之战 | `com.tencent.jkchess` |

---

## 自定义 OG 图片

默认使用 Twitter 红心 emoji 作为卡片图标。如果你想换成自己的图：

1. 把图片放到项目里（如 `icon.png`）
2. 修改 `index.html` 中的 `og:image` 为完整 URL：
   ```html
   <meta property="og:image" content="https://你的域名/icon.png">
   ```

> ⚠️ QQ 会缓存 OG 信息。如果修改后没生效，在链接后加一个随机参数（如 `?v=2`）让 QQ 重新抓取。

---

## 注意事项

- 仅供朋友间整蛊娱乐，请勿用于诈骗或恶意用途
- QQ 可能会对频繁分享的链接做安全检测
- 如果链接被大量举报，可能被 QQ 拦截
