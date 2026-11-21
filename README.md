# 网安答题 AI 资料包

给「AI 辅助网络安全竞赛答题」准备的一套资料：方法手册 + 22 个精选 SKILL.md + 4 个无依赖工具脚本。

配套一份**一页版操作手册**，照着做就行，不需要懂技术细节。

---

## 下载

| 要什么 | 地址 |
|---|---|
| 给 AI 的资料包（5.8 MB） | [ai-pack.zip](https://github.com/你的用户名/仓库名/releases/download/v1/ai-pack.zip) |
| 给我自己看的手册 | [manual.md](https://github.com/你的用户名/仓库名/blob/main/manual.md) |
| 实测评估报告（选看） | [report.md](https://github.com/你的用户名/仓库名/blob/main/report.md) |

> 上面的链接是模板，把 `你的用户名/仓库名` 换成实际的即可。
> Release 直链最稳，`curl -L -o ai-pack.zip <地址>` 就能下。

---

## 三步用起来

```powershell
# 1. 下载
curl -L -o ai-pack.zip https://github.com/你的用户名/仓库名/releases/download/v1/ai-pack.zip

# 2. 解压到 D:\ai（必须让 D:\ai\README.md 存在）
Expand-Archive ai-pack.zip -DestinationPath D:\ai

# 3. 建题目目录
mkdir D:\work\1
```

然后打开 `manual.md`，照着【第 1 段】【第 2 段】发消息即可。

---

## 包里有什么

```
D:\ai\
  README.md             AI 入口
  00-ROUTER.md          什么题读哪个 skill（含"别读"的建议）
  01-QUICKSTART.md      环境自检 / 装包写法 / 四步法 / 输出契约
  02-TOOLBOX.md         4 个脚本怎么用
  03-PITFALLS.md        15 条实测陷阱
  skills/               22 个精选 skill（流量/日志/恶意代码/逆向）
  collections/          10 个集合的索引（818 个 Anthropic skill 等）
  toolbox/              4 个纯 Python 脚本 + 预装 python-evtx（断网可读 EVTX）
```

## 环境假设

Windows + Python 3.10+，**没有** tshark / zeek / wireshark / volatility / ghidra /
yara / pefile / scapy / pyshark / pandas。所有脚本只用 Python 标准库。

需要装包时：

```powershell
python -m pip install --no-cache-dir --disable-pip-version-check --target vendor <包名>
```

---

## 关于这批 skill 的实测结论

用真实 APT 数据（APT29 day1/day2、APT10 EVTX、APT3 样本）做过 6 组 A/B 对照：
**读 skill 的组并不比不读的组答得更好**（0 胜 2 负 4 平）。

所以包的设计是「skill 当检查清单，手册和脚本当主武器」。
细节见 `report.md`。

---

## 许可

- 各 SKILL.md 版权归原仓库作者，本包只做筛选与分类，未改动正文。
- `toolbox/` 下的脚本为原创，可随意使用。
- `toolbox/vendor/` 内含 python-evtx（Apache-2.0）。
