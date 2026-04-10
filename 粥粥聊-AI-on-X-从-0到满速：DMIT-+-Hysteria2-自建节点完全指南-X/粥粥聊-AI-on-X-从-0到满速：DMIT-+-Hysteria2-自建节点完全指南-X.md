---
title: "粥粥聊 AI on X: "从 0到满速：DMIT + Hysteria2 自建节点完全指南" / X"
source: "https://x.com/boniusex/status/2041890327506944029"
saved_at: "2026-04-10"
tags: ["X/Twitter"]
---

# 粥粥聊 AI on X: "从 0到满速：DMIT + Hysteria2 自建节点完全指南" / X

Title: 粥粥聊 AI on X: "从 0到满速：DMIT + Hysteria2 自建节点完全指南" / X

URL Source: https://x.com/boniusex/status/2041890327506944029

Published Time: Fri, 10 Apr 2026 04:27:37 GMT

Markdown Content:
> 一份从买服务器到连上小火箭的完整教程。全程 Mac 操作，新手友好，跟着做就行。 预计耗时：30 分钟 · 月成本：$9.99 起

为什么选这个组合

Hysteria2 是目前主流翻墙协议里速度最快的之一，基于 QUIC over UDP，抗丢包能力强，几乎能榨干你 VPS 的全部带宽。配合 sing-box 服务端（一个程序支持几乎所有主流协议），未来想加其他协议也不用重装。

DMIT 是精品 IDC，主打 CN2 GIA 等高端回国线路，晚高峰不掉速，跨境延迟低。贵但值——Hysteria2 的速度上限完全取决于 VPS 本身的线路质量，普通 VPS 跑 Hysteria2 和 DMIT 上跑，体感差距是数量级的。

架构图

[你的 Mac / iPhone] ←→ [DMIT 洛杉矶服务器] ←→ [互联网] 小火箭客户端 Debian 12 + sing-box

你在本地设备上用小火箭连接节点，服务器负责中转流量到目标网站。

步骤 1：打开官网

访问

注册账号并登录。

步骤 2：选择套餐

推荐路径：Cloud → Los Angeles →

系列

三个套餐对比：

套餐 月付 CPU 内存 硬盘 带宽 月流量 TINY $9.99 1核 2GB 20GB 1Gbps 1000GB Pocket $14.90 2核 2GB 40GB 4Gbps 1500GB STARTER $29.90 2核 2GB 80GB 10Gbps 3000GB

怎么选：

*   个人轻度使用、日常上网 + AI 工具 + 偶尔视频 → TINY

*   经常刷 4K、多设备家庭共用 → Pocket

*   重度用户 / 多人共用 → STARTER

注意：网络类型必须选 Premium（包含 CN2 GIA，DMIT 的核心价值），不要选 Eyeball 或 Tier 1。

步骤 3：配置系统

*   VM Template：选 Debian 12（最稳定、最轻量，后续教程全基于此）

*   Extra IPv4：保持 0

*   付款周期：月付最灵活，年付更便宜（通常有 15-25% 优惠码）

步骤 4：优惠码

在结账页的 "Promotional Code" 栏可以试这些码（有时效性，请现场验证）：

*   2025-XMAS-LAX-PRO-EB-10-OFF-RECURRING — Pro 系列 10% 折扣 + 5% 返现

*   2025-XMAS-LAX-PRO-EB-ANNUALLY-STARTER-AND-HIGHER-15OFF-RECURRING — STARTER 以上年付 15% 折扣 + 10% 返现

如果码失效，去 DMIT 官网首页 Banner 或 Telegram 频道（

）看最新活动。

步骤 5：付款

DMIT 支持支付宝、微信、PayPal、信用卡。付款后进入后台 Services → My Services 就能看到实例。

步骤 1：在 DMIT 后台下载 SSH 密钥

进入实例详情页 → 点击 「前往"訪問"」 按钮 → 弹窗显示 "新的 SSH 金鑰" → 点绿色 「下載」 按钮。

会下载一个 ZIP 包到 Mac 的 ~/Downloads/ 文件夹，解压后里面有三个文件：

*   id_rsa.pem — Mac/Linux 用的私钥（我们用这个）

*   id_rsa.ppk — Windows PuTTY 格式（Mac 用不上）

*   id_rsa.pub — 公钥（不用管）

> ⚠️私钥一旦泄露，服务器就失去安全性。不要截图发人，不要上传到任何云盘/聊天软件。

步骤 2：把私钥放到正确位置

打开 Mac 的 终端（Cmd + 空格 → 搜 "Terminal" → 回车），执行：

bash

mkdir -p ~/.ssh cp ~/Downloads/DMIT-*-id_rsa*/id_rsa.pem ~/.ssh/dmit_key chmod 600 ~/.ssh/dmit_key ls -l ~/.ssh/dmit_key

最后一条应该输出类似 -rw------- 1 你的用户名 staff 1700 ... /Users/你的用户名/.ssh/dmit_key，权限显示 -rw------- 就对了。

步骤 3：SSH 连接服务器

把下面命令里的 你的服务器IP 替换成 DMIT 后台显示的 IPv4 地址（比如 154.21.94.7）：

bash

ssh -i ~/.ssh/dmit_key root@你的服务器IP

第一次连接会问 Are you sure you want to continue connecting (yes/no)?，输入 yes 回车。

成功后会看到 Debian 欢迎信息和一个提示符：

root@DMIT-xxxxx:~#

看到这个提示符，就说明你已经"进入"服务器了，后续所有命令都在这个终端里执行。

> 💡怎么判断自己在哪台机器上：看终端提示符。nice ~ ❯ 是你的 Mac；root@DMIT-xxxxx:~# 是远程服务器。

步骤 1：更新系统

bash

apt update && apt install -y curl wget openssl

步骤 2：安装 sing-box（从 GitHub 下载官方 .deb 包）

bash

ARCH=$(dpkg --print-architecture) VERSION=$(curl -fsSL

| grep tag_name | cut -d '"' -f 4 | sed 's/v//') wget -O /tmp/sing-box.deb "

${VERSION}/sing-box_${VERSION}_linux_${ARCH}.deb" dpkg -i /tmp/sing-box.deb sing-box version

最后一行会输出类似 sing-box version 1.13.x，看到版本号就成功了。

> 为什么不用 apt 官方源：apt 源在某些环境下会有 GPG 密钥导入问题，直接下载 .deb 包最稳定，100% 成功率。

步骤 3：开启 BBR 加速

BBR 是 Linux 内核级别的 TCP 拥塞控制算法，对提升跨境速度有明显作用。

bash

echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf sysctl -p sysctl net.ipv4.tcp_congestion_control

最后一行应该输出 net.ipv4.tcp_congestion_control = bbr。

步骤 4：生成自签名 TLS 证书

Hysteria2 必须启用 TLS，但我们不用买域名、不用申请 Let's Encrypt 证书——直接自签名，小火箭客户端打开"允许不安全"就能连。

bash

mkdir -p /etc/sing-box/cert openssl ecparam -genkey -name prime256v1 -out /etc/sing-box/cert/private.key openssl req -new -x509 -days 36500 -key /etc/sing-box/cert/private.key -out /etc/sing-box/cert/cert.pem -subj "/CN=

" chown -R sing-box:sing-box /etc/sing-box/cert

-days 36500 是证书有效期 100 年，基本相当于永久。

步骤 5：生成节点密码

bash

openssl rand -base64 16

会输出一串 24 字符的随机字符串，比如 tfnS+sRV4AHrT12iCt1Pqw==。

把这串密码记下来，后面写配置文件和客户端连接都要用。

步骤 6：写入 sing-box 配置文件

把下面这整段里的 你的密码 替换成上一步生成的密码，然后复制粘贴执行：

bash

cat > /etc/sing-box/config.json <<'EOF' { "log": { "level": "warn", "timestamp": true }, "inbounds": [ { "type": "hysteria2", "tag": "hy2-in", "listen": "::", "listen_port": 33443, "users": [ { "password": "你的密码" } ], "masquerade": "

", "tls": { "enabled": true, "alpn": ["h3"], "certificate_path": "/etc/sing-box/cert/cert.pem", "key_path": "/etc/sing-box/cert/private.key" } } ], "outbounds": [ { "type": "direct", "tag": "direct" } ] } EOF

> 如果懒得手动替换，也可以先执行上面的命令，然后用 nano /etc/sing-box/config.json 打开文件编辑，把 你的密码 改成真实密码，Ctrl+O 保存、Ctrl+X 退出。

配置说明：

*   端口 33443 可以改成其他值（建议 10000-65535 之间的随机数）

*   masquerade 是伪装地址，外人探测时会看到 Bing 首页

*   listen: "::" 表示同时监听 IPv4 和 IPv6

步骤 7：校验配置并启动

bash

sing-box check -c /etc/sing-box/config.json

没有任何输出 = 配置正确（Unix 哲学：no news is good news）。如果有报错就根据提示检查配置文件。

启动服务并设置开机自启：

bash

systemctl enable --now sing-box systemctl status sing-box

重点看这两行：

*   ● sing-box.service 前面是 绿色圆点

*   Active: active (running) 是 绿色

按 q 退出状态显示界面。

步骤 8：验证端口监听

bash

ss -ulnp | grep 33443

应该看到类似 UNCONN 0 0 *:33443 *:* users:(("sing-box",pid=xxxxx,fd=8)) 的输出，说明 UDP 端口已就位。

方法一：URL 一键导入（推荐）

按你的实际信息拼接这个链接（密码里的 + 要编码成 %2B，= 要编码成 %3D）：

hysteria2://你的密码@你的IP:33443/?sni=

&insecure=1#DMIT-LAX-Hy2

示例（假设密码是 tfnS+sRV5AHrT12iCt1Pww==，IP 是 154.21.94.7）：

hysteria2://tfnS%2BsRV5AHrT12iCt1Pww%3D%3D@154.21.94.7:33443/?sni=

&insecure=1#DMIT-LAX-Hy2

操作：

1.   Mac 上复制这行链接

2.   用隔空投送 / 微信文件传输发到 iPhone

3.   在 iPhone 上复制这行

4.   打开小火箭，会自动弹窗询问是否添加节点，点"添加"

方法二：手动添加

小火箭右上角 + → 类型选 Hysteria2，依次填：

字段 值 类型 Hysteria2 备注 DMIT-LAX-Hy2 地址 你的 VPS IP 端口 33443 密码 你生成的密码 SNI

允许不安全⚠️必须开启（自签名证书）

保存后回到首页，点击节点选中，打开顶部的总开关。iPhone 会弹"允许添加 VPN 配置"的权限请求，允许并输入手机密码即可。

测速

*   延迟测试：小火箭自带的"测试延迟"

*   速度测试：Safari 打开 
*   综合体验：打开 YouTube 4K 视频，看能不能秒开

Hysteria2 + DMIT Premium 的组合通常能跑出非常漂亮的速度，家宽千兆的话很容易跑满下行。

一个节点可以同时给多台设备用，互不影响。支持的客户端：

*   iPhone / iPad：小火箭（Shadowrocket）、Stash、Loon、sing-box

*   Mac：ClashX Meta、Stash、sing-box、Surge

*   Android：NekoBox、sing-box、Clash Meta

*   Windows：v2rayN、sing-box、Clash Verge

*   Linux / 路由器：sing-box

把同一个节点 URL 或配置导入到不同设备就行，所有设备 共享同一份月流量额度。

常用命令

所有命令都在 SSH 连接到服务器后执行：

操作 命令 启动服务 systemctl start sing-box 停止服务 systemctl stop sing-box 重启服务 systemctl restart sing-box 查看状态 systemctl status sing-box 查看实时日志 journalctl -u sing-box -f（Ctrl+C 退出） 校验配置 sing-box check -c /etc/sing-box/config.json 编辑配置 nano /etc/sing-box/config.json

修改配置后的标准流程

bash

nano /etc/sing-box/config.json # 修改配置 sing-box check -c /etc/sing-box/config.json # 校验语法 systemctl restart sing-box # 重启生效 systemctl status sing-box # 确认运行中

升级 sing-box

bash

ARCH=$(dpkg --print-architecture) VERSION=$(curl -fsSL

| grep tag_name | cut -d '"' -f 4 | sed 's/v//') wget -O /tmp/sing-box.deb "

${VERSION}/sing-box_${VERSION}_linux_${ARCH}.deb" dpkg -i /tmp/sing-box.deb systemctl restart sing-box

跟安装命令完全一样，dpkg 会自动处理升级。

客户端连不上

依次检查：

1.   VPS 是否在线：DMIT 后台看实例状态是否"運行中"

2.   sing-box 是否运行：SSH 上去执行 systemctl status sing-box，看是不是绿色 active

3.   端口是否监听：ss -ulnp | grep 33443

4.   小火箭配置：特别检查"允许不安全"是否开启、密码是否正确、端口是否匹配

5.   防火墙：DMIT 默认无外部防火墙，但如果你自己装过 ufw/iptables，确认 UDP 33443 已放行

速度不理想

*   确认 BBR 已启用：sysctl net.ipv4.tcp_congestion_control 应返回 bbr

*   换端口试试：某些运营商会对非标 UDP 端口 QoS 限速，可以尝试改成 443（修改配置后重启 sing-box）

*   晚高峰问题：DMIT Premium 线路已经很优了，如果还是慢，大概率是你本地宽带到洛杉矶的国际出口拥塞

*   看日志：journalctl -u sing-box -f 看有没有报错

IP 被墙

DMIT 政策是 每 15 天可免费换一次 IP，其他情况 $5/次。在 DMIT 后台提交工单申请即可。

换个客户端测试

如果怀疑是小火箭的问题，可以在 Mac 上装 sing-box 客户端或 Stash 试试同一个节点，排除客户端 bug。

加一条 VLESS-Reality 备用线路

Hysteria2 唯一的软肋是 UDP 可能被 QoS 限速。可以在同一个 sing-box 配置里多加一个 TCP 协议的 inbound，比如 VLESS-Reality，作为兜底线路。两条线路并存，互不影响。

多用户管理

在 users 数组里加多个密码就行：

json

"users": [ { "name": "me", "password": "密码1" }, { "name": "friend", "password": "密码2" } ]

不同人用不同密码，方便统计和随时禁用。

流媒体解锁

DMIT 洛杉矶 IP 大概率能解锁 Netflix、YouTube Premium、Disney+ 等，但不保证（IP 封禁名单动态变化）。实测为准。

1.   不要公开你的 IP + 端口 + 密码组合，发节点给别人时记得说明仅供本人/朋友使用

2.   定期备份配置文件：cp /etc/sing-box/config.json ~/config.json.bak

3.   SSH 私钥好好保管：如果私钥泄露，立即在 DMIT 后台重置密钥

4.   禁用密码登录（DMIT 默认就是禁用的，保持现状即可）

5.   流量监控：DMIT 后台能看实时流量，避免月底超额被限速

项目 值 服务器系统 Debian 12 部署工具 sing-box（官方 .deb 包） 协议 Hysteria2 默认端口 UDP 33443 TLS 自签名证书（CN:

伪装域名

配置文件路径 /etc/sing-box/config.json 证书路径 /etc/sing-box/cert/ 服务管理 systemd (systemctl) 日志查看 journalctl -u sing-box -f

教程到此结束。 有问题欢迎反馈，祝你冲浪愉快 🚀
