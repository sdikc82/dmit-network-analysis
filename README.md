# DMIT Looking Glass 怎么用？节点测速、路由追踪一次搞清楚，附全套餐对比

买 VPS 之前，我习惯先跑一遍 Looking Glass。上次选香港节点，就是靠 DMIT 的 LG 页面测出来本地到 CN2 GIA 的延迟只有 28ms，才下定决心下单的。如果你也在纠结 DMIT 哪个节点适合自己，这篇文章把测速工具怎么用、各节点线路特点、套餐怎么选，全部拆开说清楚。

---

## DMIT Looking Glass 是什么，能测出哪些东西

Looking Glass（简称 LG）是 DMIT 官方提供的网络诊断工具，不需要注册账号，直接在浏览器里就能用。

它能做三件事：

- **Ping 测试**：从目标节点向你的 IP 发包，看往返延迟和丢包率
- **Traceroute**：追踪数据包经过哪些路由节点，判断走的是 CN2 GIA、CN2 GT还是普通 163 骨干
- **下载测速文件**：从节点服务器直接下载测试文件，测实际带宽

DMIT 的 LG 页面地址是 `lg.dmit.io`，进去之后选节点、填 IP 或域名、选测试类型，点一下就出结果。说实话，界面比很多同类服务商干净多了，不用翻半天找入口。

---

## 各节点线路解读：CN2 GIA、Premium、Lite 有什么区别

这是买 DMIT 最容易踩坑的地方。同样是香港节点，线路不同，体验差距可以很大。

**Premium 系列（CN2 GIA 双向）**

走中国电信 CN2 GIA 线路，双向优化，这是 DMIT 旗下延迟最低、稳定性最强的档位。我自己用的是香港 Premium，晚高峰跑 YouTube 4K 基本不卡顿。Traceroute 结果里能看到 `59.43.x` 开头的 IP，那就是 CN2 GIA 的特征跳点。

**Lite 系列**

价格低一档，走的是普通直连或 CN2 GT，延迟会比 Premium 高一些，丢包在晚高峰偶尔会出现。适合预算有限、对延迟不那么敏感的场景。

**Eyeball 系列（部分节点）**

针对三网优化，电信走 CN2 GIA，联通走 AS4837，移动走 CMI，覆盖面更广。如果你的网络是联通或移动，跑 LG 的时候记得用自己的 IP 测，别用默认的测试 IP，结果会更准。

讲真，光看套餐描述不够，一定要自己跑一遍 LG 再决定。

---

## 怎么用 Looking Glass 判断节点适不适合自己

步骤很简单，但有几个细节容易忽略。

**第一步：确认自己的出口 IP**

去 `ip.sb` 或者 `ipinfo.io` 查一下当前出口 IP，记下来备用。

**第二步：选对节点做 Ping 和 Traceroute**

在 LG 页面选你感兴趣的节点，把自己的 IP 填进去，先跑 Ping，再跑 Traceroute。

Ping 结果参考标准：
- 延迟 < 50ms：非常好，CN2 GIA 典型表现
- 50–100ms：正常范围，可以接受
- > 150ms：线路可能绕路，或者走的是普通骨干

Traceroute 里重点看第 3–6 跳，出现 `59.43` 开头的 IP 就是 CN2 GIA，出现 `202.97` 开头的是 163 骨干。

**第三步：下载测速文件验证带宽**

LG 页面一般提供 100MB 和 1GB 的测速文件，直接点下载，看实际速度。这个比 Speedtest 更接近真实使用场景，因为是从 DMIT 的服务器直接拉数据。

我测香港 Premium 节点的时候，白天能跑满 200Mbps，晚高峰掉到 80–120Mbps 左右，对于日常使用完全够用。

---

## DMIT 全套餐对比

以下是 DMIT 当前在售的主要套餐，覆盖香港、日本、美国、洛杉矶等主要节点：

| 套餐名称 | 关键配置 | 价格 | 立即购买 |
| --- | --- | --- | --- |
| Hong Kong Premium（PVM.HKG.Pro） | 1 vCPU / 1GB RAM / 20GB SSD / 500GB 流量 / CN2 GIA 双向 | $14.90/月 | [ 选香港 Premium 享 CN2 GIA 优化](https://www.dmit.io/aff.php?aff=13832&pid=95) |
| Hong Kong Lite（PVM.HKG.Lite） | 1 vCPU / 1GB RAM / 20GB SSD / 500GB 流量 / 直连线路 | $6.90/月 | [ 选香港 Lite 低价入门](https://www.dmit.io/aff.php?aff=13832&pid=94) |
| Tokyo Premium（PVM.TYO.Pro） | 1 vCPU / 1GB RAM / 20GB SSD / 500GB 流量 / CN2 GIA 双向 | $14.90/月 | [ 选东京 Premium 低延迟直连](https://www.dmit.io/aff.php?aff=13832&pid=103) |
| Tokyo Lite（PVM.TYO.Lite） | 1 vCPU / 1GB RAM / 20GB SSD / 500GB 流量 / 直连线路 | $6.90/月 | [ 选东京 Lite 预算友好方案](https://www.dmit.io/aff.php?aff=13832&pid=102) |
| Los Angeles Premium（PVM.LAX.Pro） | 1 vCPU / 1GB RAM / 20GB SSD / 1TB 流量 / CN2 GIA 双向 | $14.90/月 | [ 选洛杉矶 Premium 跨太平洋优化](https://www.dmit.io/aff.php?aff=13832&pid=183) |
| Los Angeles Eyeball（PVM.LAX.EB） | 1 vCPU / 1GB RAM / 20GB SSD / 1TB 流量 / 三网优化 | $6.90/月 | [ 选洛杉矶 Eyeball 三网覆盖](https://www.dmit.io/aff.php?aff=13832&pid=182) |
| Los Angeles Lite（PVM.LAX.Lite） | 1 vCPU / 1GB RAM / 20GB SSD / 1TB 流量 / 普通直连 | $2.90/月 | [ 选洛杉矶 Lite 最低价起步](https://www.dmit.io/aff.php?aff=13832&pid=181) |
| San Jose Premium（PVM.SJC.Pro） | 1 vCPU / 1GB RAM / 20GB SSD / 1TB 流量 / CN2 GIA 双向 | $14.90/月 | [ 选圣何塞 Premium 美西优化节点](https://www.dmit.io/aff.php?aff=13832&pid=155) |

👉 [查看 DMIT 官方完整套餐配置表](https://www.dmit.io/aff.php?aff=13832)

---

## 用 Looking Glass 选节点的常见误区

**误区一：只看 Ping 值，不看 Traceroute**

延迟低不代表线路好。有些节点 Ping 值看起来不错，但 Traceroute 一跑发现绕了一大圈，实际使用中高峰期丢包严重。路由路径才是判断线路质量的核心依据。

**误区二：用 LG 测试 IP 不是自己的真实出口**

很多人直接填一个随便的 IP 测，结果没有参考价值。一定要填自己当前的出口 IP，测出来的延迟和路由才是你实际会经历的。

**误区三：只在白天测，不测晚高峰**

晚上 8 点到 11 点是国内网络最拥堵的时段。同一个节点，白天和晚高峰的表现可能差很多。我建议两个时段都测一遍，再做决定。

**误区四：Premium 一定比 Lite 好**

对于联通、移动用户，有时候 Eyeball 套餐的实际体验比 Premium 更好，因为 Eyeball 针对三网分别优化了回程路由。电信用户首选 Premium，联通移动用户可以先跑 LG 对比一下。

---

## FAQ

**Q：DMIT Looking Glass 在哪里访问？**

直接访问 `lg.dmit.io`，不需要登录账号，选节点填 IP 就能用。

**Q：Traceroute 结果里看到 59.43 开头的 IP，是什么意思？**

`59.43.x.x` 是中国电信 CN2 GIA 骨干网的 IP 段，出现这个说明数据包走的是 CN2 GIA 线路，延迟低、稳定性好。

**Q：DMIT 支持退款吗？**

DMIT 提供 72 小时内无理由退款政策，新购套餐如果测试后不满意可以申请退款，这点我觉得挺实在的。

**Q：香港节点和日本节点哪个更适合国内用户？**

物理距离上香港更近，延迟通常低 5–15ms。但如果你的运营商对香港方向有拥塞，日本节点反而可能更稳。用 LG 分别测一下，数据说话。

**Q：流量超出套餐限额怎么办？**

超出后带宽会被限速，不会直接断线。可以在控制面板购买额外流量包，或者升级套餐。

**Q：DMIT 的 VPS 支持哪些支付方式？**

支持支付宝、PayPal、信用卡，国内用户用支付宝付款最方便。

---

如果你现在还在纠结选哪个节点，最直接的办法就是先去 `lg.dmit.io` 跑一遍自己的 IP，把延迟和路由数据拿到手，再对照上面的套餐表做决定。Premium 系列适合对延迟敏感的场景，Lite 和 Eyeball 适合预算有限或者联通移动用户。数据跑出来了，选哪个一目了然。

[👉 一键直达 DMIT 官方下单页，按需选套餐](https://www.dmit.io/aff.php?aff=13832)
