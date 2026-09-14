# sr-conf

Shadowrocket（小火箭）分流配置文件，基于 [lazy_group](https://github.com/lowertop/Shadowrocket) 修改。

## 订阅地址

```
https://xxbb678.github.io/sr-conf/lazy_group.conf
```

## 使用方法

1. 打开 Shadowrocket，首页右上角 `+` → 类型选 **Subscribe（订阅）**
2. URL 填入上面的订阅地址 → 保存
3. 首页下拉刷新，节点会自动按地区分组
4. 设置 → 延迟测试方法，选择 **CONNECT**
5. 首页 → 连通性测试 → 选择可用节点连接

首次启动会提示【安装 VPN 配置文件】，点击【好】和【允许】。

## 节点分组

**自动测速分组**（`url-test`，每 600 秒测一次，自动选延迟最低）：

| 分组 | 匹配关键词 |
|------|-----------|
| 香港节点 | 🇭🇰 HK Hong 香港 深港 沪港 京港 港 |
| 台湾节点 | 🇹🇼 TW TWN Taiwan Taipei 台湾 台灣 台北 台中 新北 彰化 |
| 日本节点 | 🇯🇵 JP Japan Tokyo 日本 东京 大阪 京日 苏日 沪日 上日 川日 深日 广日 日 |
| 新加坡节点 | 🇸🇬 SG Sing 新加坡 狮城 沪新 京新 深新 杭新 广新 |
| 韩国节点 | 🇰🇷 KR Korea KOR 韩国 首尔 韩 韓 春川 |
| 美国节点 | 🇺🇸 US USA America United States 美国 凤凰城 洛杉矶 西雅图 芝加哥 纽约 沪美 美 |
| **德国节点** | 🇩🇪 Germany 德国 法兰克福 柏林 波恩 法兰 Frankfurt Falkenstein Nuremberg Hetzner DE节点 -德- |
| **法国节点** | 🇫🇷 France FR节点 -法- 法国 巴黎 马赛 里昂 Paris Marseille Lyon OVH Scaleway Gravelines Roubaix |

**策略分组**（`select`，手动选择）：AI、YouTube、Netflix、Disney+、Max、TikTok、Spotify、Telegram、Twitter、Facebook、PayPal、Amazon、苹果服务、谷歌服务、微软服务、哔哩哔哩、游戏平台

## 分流规则

- **走代理**：AI、YouTube、Netflix、Disney+、Max、Spotify、Telegram、Twitter、Facebook、PayPal、Amazon、TikTok、GitHub、谷歌服务、微软服务、游戏平台、Global 规则集
- **直连**：苹果服务、哔哩哔哩、网易云音乐、百度、豆瓣、微信、新浪、知乎、小红书、抖音、国内 IP（GEOIP,CN）
- **兜底**：`FINAL,PROXY`（未匹配走代理）

## 相对原版的改动

1. **新增德国节点分组**（原版只有港台日新韩美六组）
2. **新增法国节点分组**
3. **16 个 select 分组加入德国、法国节点选项**
3. **`update-url` 改为本仓库地址**（原为原作者地址）
4. **移除 `[MITM]` 段的 CA 证书**（`ca-passphrase` / `ca-p12`），避免私钥泄露；`enable` 改为 `false`

## 关于 HTTPS 解密

本配置**不包含** CA 证书。如需 HTTPS 解密（抓包调试用）：

1. 小火箭 → 配置 → 点配置文件后的 ⓘ → HTTPS 解密 → 证书 → 生成新的 CA 证书
2. 系统设置 → 已下载描述文件 → 安装
3. 系统设置 → 通用 → 关于本机 → 证书信任设置 → 开启对应证书信任

## 更新方式

修改 `lazy_group.conf` 后推送，GitHub Pages 约几十秒自动重建，小火箭下拉刷新即可。

## 目录

```
lazy_group.conf    配置文件
README.md          本说明
```

## 致谢

配置结构与规则集源自 [lowertop/Shadowrocket](https://github.com/lowertop/Shadowrocket)（lazy_group），规则集使用 [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script)。
