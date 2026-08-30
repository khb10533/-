# 苏游修改器 · 柳漪春涛正式版

《苏丹的游戏》存档编辑器。**单个 HTML 文件，下载后断网可用**，不需要安装、不需要联网、不上传你的存档。

在线使用：<https://khb10533.github.io/suyou-save-editor/>

## 功能

**卡牌 / 物品**
- 自动显示官方正确名字、称号、类型徽章与完整简介（内置 1292 张卡牌资料）
- 按分类筛选：角色 / 物品 / 苏丹卡 / 词库未收录
- 按名称、ID、存在时间、堆叠数排序（只影响显示，不改动存档数组顺序）
- 搜索覆盖官方名、称号、简介、类型、ID、UID、标签
- 按名字添加任意卡牌：输名字即可从 1292 张里挑，一键进手牌
- 变体卡（`21xxxxx`、`22xxxxx` 等）自动回退到基础 ID 取资料

**标签**
- 内置 442 条官方标签词库，含中文名、类型（增益 / 减益 / 属性）与说明
- 加标签时可搜索选择，输中文名或英文 code 都能搜到，点一下就加，不必手打
- 已添加的标签不会重复出现在候选里；词库外的自定义 code 仍可手动添加

**事件 / 仪式**
- 显示官方正确名字与类型徽章（事件表 1304 条 + 仪式表 1495 条，查不到事件时自动回退仪式表）
- 槽位内的角色也显示官方名与称号
- 按名称、ID、存在时间、槽位数排序

**名望**
- 善名 / 恶名 / 权势 / 侠名 / 灵视 / 金骰子，直接改数值
- 每项带清零、+50；另有六项一键拉满、金骰子快捷设置
- 进阶：按 ID 或名称查改 `counter` 里的任意计数器项

**图鉴查询**
- 卡牌 / 事件 / 仪式三个模式，可按类型与可堆叠状态筛选
- 卡牌可一键加入手牌，任意条目可复制 ID

**其它**
- 名称词典 557 条，全局字段与标签都显示中文名，可自行增补（存 localStorage）
- 源码页可直接查看和编辑存档 JSON
- 结构自动识别，兼容不同版本存档的字段布局
- 改动前建议先【导出备份】

## 使用

1. 打开 `index.html`（**用 Chrome / Edge**，手机上长按文件 → 打开方式 → 浏览器）
2. 点【📂 打开存档文件】选择你的存档 JSON
3. 改完点【💾 保存并下载】，把文件放回原位置

存档位置随平台和版本而异，请自行确认后再覆盖，并**务必先备份原文件**。

## 从源码构建

仓库里的 `index.html` 就是成品，直接用即可。若要重新构建：

```bash
# 依赖
npm install tailwindcss@3.4.19

# 编译 CSS（扫描 src/ 下的 HTML 与 JS 决定产出哪些类）
npx tailwindcss -i src/input.css -o build/out.css --minify

# 组装单文件
python3 build.py
```

`src/` 下拆分为 `body.html`、`main.js`、`addons.js` 与词库 JSON；`build.py` 把 CSS、JSON5、词库和脚本内联成单个 `index.html`。

## 协议

本程序是自由软件，依 [GNU GPL v3](LICENSE) 或更新版本授权发布。

```
Copyright (C) 2026  柳漪春涛

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.
```

**如果你分发修改过的版本，GPL 要求你同样以 GPL-3.0 开放源码，并保留版权与协议声明。**

### 第三方组件

| 组件 | 版本 | 协议 |
|---|---|---|
| [Tailwind CSS](https://tailwindcss.com) | 3.4.19 | MIT |
| [JSON5](https://json5.org) | 2.2.3 | MIT |

两者均为 MIT，与 GPL-3.0 兼容，以内联形式包含在 `index.html` 中。

### 内置游戏数据的版权说明

`index.html` 内嵌了《苏丹的游戏》的卡牌、事件、仪式、标签的**名称与描述文本**，用于在编辑存档时显示可读的名字，避免用户对着一串数字 ID 盲改。

**这部分数据的版权归《苏丹的游戏》开发商所有，不属于本项目的原创内容，不在上述 GPL-3.0 授权范围内。** GPL-3.0 仅覆盖本项目的程序代码。

数据仅为兼容性与可用性目的随附，不包含游戏的美术、音频、剧情脚本或任何可运行的游戏资源，也无法用于替代或重现游戏本体。若权利方认为此种随附不当，请通过 Issue 联系，将立即移除并改为由用户自行导入本地数据文件。

## 免责声明

本工具用于修改单机游戏的本地存档。使用者需自行承担存档损坏或游戏异常的风险，**改动前请务必备份**。本项目与《苏丹的游戏》开发商、发行商无任何隶属或合作关系。

## 贡献

欢迎提 Issue 反馈问题，或提 Pull Request。提交代码即表示同意以 GPL-3.0 授权你的贡献。
