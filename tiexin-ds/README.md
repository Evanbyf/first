# 小贴心 Tiexin AI 设计规范（从 Figma 提取）

- 来源文件：「同程管家组件库」 <https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/>（fileKey `tl19wuHmHOyNK2C1r7DhQo`）
- 提取方式：Figma MCP。`use_figma` 用 Plugin API 只读读取节点、变量和样式，`get_screenshot` 负责截图。设计稿**没有做任何修改**。
- 提取日期：2026-09-30

## 目录

| 文件 | 内容 |
|---|---|
| `tokens.json` | 颜色（light / dark）、字体、间距、圆角、阴影 token，按指定的列表结构 |
| `components.md` | 51 个组件：页面、节点链接、变体与属性、状态、尺寸、间距、圆角、字号及其 token、设计注释 |
| `untokenized.md` | 组件里反复出现、但没有绑定变量或样式的值 |
| `screenshots/` | 73 张 PNG：68 张组件截图，加 5 张规范页截图（封面、颜色 light、颜色 dark、字体、圆角与阴影） |
| `assets/Icons/` | 67 个图标 SVG |
| `assets/Logos/` | 2 个 Logo SVG（`_logo` 组件集的 full 和 only 两个变体） |

## 页面汇总

文件一共 **56 个页面**：

- **封面**（0:1）
- **颜色、字体、阴影效果**（0:3）：规范页，有 4 个画框：效果 46:6021、颜色库 light 2906:1101、颜色库 dark 2907:3853、文本库 2908:2757
- **3 个分隔页**（74:1545、74:1546、565:11312）：名字只有一个空格，页面是空的
- **51 个组件页**：按钮、组合按钮、弹窗、卡片、下拉菜单、输入框、链接、选择器（级联）、单选框、复选框、颜色选择器、日期时间选择器、开关、滑块、表单、数字输入框、评分、选择器␠（名字末尾带一个空格，是 Select）、穿梭框、上传、头像、徽标 / 角标、日历、轮播图、折叠面板、描述列表、空状态、图片、分页、进度条、结果页、表格、标签、时间线、树形控件、统计数值、面包屑导航、菜单、页头、步骤条、标签页、警告提示、抽屉、加载、消息提示（含 Toast）、弹框、通知提醒、气泡确认框、气泡卡片、文字提示气泡框、分割线

## 数量

| 项目 | 数量 |
|---|---|
| 组件（按页面 / 章节） | **51** |
| 变量：「颜色」集合（light 22:2 / Dark 37:4）里列出的 | **49** |
| 变量：孤立变量（已从面板删除，但仍绑定在组件上，见下文） | **35**：「颜色」集合里颜色 24、Size 3、Radius 5，旧「Radius」集合 21:772 里 3 个 |
| 变量：文件里绑定到的远程库变量 | **13**：「Tiexin」3 个（bg4、text1、text4）、「同程管家组件库」3 个、「Color」2 个、「小新的组件库」5 个（只用在规范页装饰上） |
| 文本样式 | **22**：regular / medium / bold 各 6 个档位，加 regular/ts、bold/ts、regular/txyidongzhengwen、regular/IMqipao |
| 效果样式（阴影） | **4** |
| 颜色样式 | **1**：渐变 `jianbain`，见 untokenized.md |
| tokens.json 里的 token 总数 | **123**：颜色 86（列出 49 + 孤立 24 + 远程 13）、字体 22、spacing 3、radius 8、shadow 4 |

## Token 命名规则

- Figma 路径转成小写，`/` 换成 `-`。例如 `Color/Primary/brand` 写成 `color-primary-brand`。
- 中文「气泡」写成 `-qipao`，例如 `bg4气泡` 写成 `color-background-bg4-qipao`。
- 远程库变量加 `remote-` 前缀。
- 旧「Radius」集合（21:772）里的变量加 `legacy-` 前缀。
- 文本样式 `regular/base` 写成 `regular-base`。效果样式 `light/box-shadow-*` 写成 `shadow-*`。
- 每个 token 的 `usage` 字段都写了原始 Figma 名称和规范页上的中文标注。

## 没能提取、或需要注意的地方

1. **网络限制，资源 URL 下载不了。** 当前运行环境的网络策略屏蔽了 `www.figma.com`（curl 返回 403），所以 `download_assets` 和 `get_screenshot` 给出的 URL 都下载不了。改用了下面两种办法：
   - 截图：通过 `get_screenshot` 的 base64 返回拿到 PNG，最长边 1024px。大画框因此被等比缩小了，比如 Alert 原图 3740px 宽。
   - SVG：在 Plugin API 里对图标和 Logo 的**主组件**调用 `exportAsync({format:'SVG_STRING'})`，原样写入文件，没有重绘。
2. **文件里没有「小贴心」Logo。** 这个文件其实是「同程管家组件库」，基于 Element Plus 模板改的：页面里还留着 “Element Plus Template” 字样，还有 Element Plus 风格的 `color-*-light-N` 旧变量。
   - `_logo` 组件集导出的是 Element Plus 的 Logo，已改成品牌色 #4050FF。
   - 封面上的 “Logo Text” 是一个文字节点，内容是 “Design”。
   - 「小贴心」只在文本样式说明「小贴心移动正文15、25」（regular/txyidongzhengwen）里出现过。另外有一个远程变量集合叫「Tiexin」。
3. **组件没有使用说明。** 所有组件集和组件的 description 都是空的，各页面上也没有文字说明，所以 components.md 里统一写「设计稿未说明」。
4. **有孤立变量。** 35 个变量已经从变量面板删掉了，`getLocalVariablesAsync` 读不出来，但仍然绑定在组件上。
   - 我遍历节点的绑定、再按 ID 去查，拿到了它们的准确值，也写进了 tokens.json，并在 usage 里标了 ⚠️。
   - 这些变量大多是 Element Plus 留下的旧色阶，还有 Size 和 Radius。
   - `radius-border-radius-none` 的值很奇怪：light 是 4，dark 是指向 `Size/common-component-size-default`（32）的别名。已按原样记录。
5. **远程库变量只拿到解析后的值。** 13 个远程变量来自其它库：「Tiexin」「同程管家组件库」「Color」「小新的组件库」。读到了它们在本文件里的解析值，但拿不到源库的完整集合。
   - 「Color」集合只有 Light 一个模式，所以 `remote-overlay-toast` 和 `remote-text-on-primary` 在 dark 下填了相同的值。
   - 「Tiexin」和「小新的组件库」的两个模式按 light / dark 的顺序对应。其中 Tiexin 的 text1、text4 跟本地同名变量的值不一样，所以单独命名为 `remote-tiexin-*`。
   - 远程文本样式 “Default size/Subheadline strong”、“Caption 1 strong”，以及封面用的 Inter “Body/Med 20”，也不属于本文件，没有写进 tokens.json。
6. **brand3 色板和变量值对不上。** 颜色规范页上 brand3 的色块显示 **#B6C0FF**，但变量 `Color/Primary/brand3` 的 light 值是 **#d9defe**。tokens.json 以变量值为准。
7. **字重命名有歧义。** 字体规范页上写的是 “Bold 700”，但文本样式实际用的是 PingFang SC **Semibold**，所以 tokens.json 写 `fontWeight: 600`。
8. **行高 Auto 写成 `normal`。** `regular/ts`（10px）和 `bold/ts`（26px）的行高是 Auto，tokens.json 里写成 `"normal"`。
9. **没有间距变量，也没有间距规范页。** 设计稿里的 padding 和 gap 全部是写死的数值，汇总在 untokenized.md。
   - `tokens.json` 的 `spacing` 里只放了唯一的尺寸类变量：组件高度 Size（24/32/40）。
   - 要求里的「间距页截图」没有对应页面，用规范页的效果画框 `圆角与阴影-radius-shadow.png` 代替。它的内容是圆角档位和阴影，不是间距。
10. **阴影只有 light 版本。** 效果样式都叫 `light/...`，文件里没有 dark 阴影。
11. **插画没有导出 SVG。** 空状态插画等位图、复杂插画只截了图（`Empty-illustrations.png`），没有导出成 SVG。要求里的 assets 只包括 Logo 和图标。
12. **图标颜色以主组件为准。** 图标导出的是主组件，所以颜色是主组件本身的颜色，不带实例上的覆盖色。例如 Sparkles 的主组件描边是黑色，实例上覆盖成了 #4050FF。
