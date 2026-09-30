# 未 token 化的重复值

这些值在组件里反复出现，但设计稿没有给它们绑定变量（Variable），也没有做成样式（Style）。按要求，它们**不写进** `tokens.json`，只在这里列出，方便以后决定要不要收编成 token。

每一行都是从 Figma 节点上直接读到的原始值（Plugin API 只读读取），没有估算。「出处」对应 `components.md` 的章节。

## 1. 颜色

| 值 | 用在哪里 | 出处 | 说明 |
|---|---|---|---|
| `#222329` | Dialog 标题文字（bold/medium 16）、Dropdown 菜单项文字 | §3 Dialog、§5 Dropdown | 与远程变量 `remote-neutral-text-neirong` 的 light 值相同，但这些节点没有绑定它 |
| `#323233` | Dialog 示例「编组 32备份 27」正文 | §3 Dialog | |
| `#ffffff` | Dropdown 菜单浮层填充 | §5 Dropdown | 与 `color-overlay-white` 的 light 值相同，但没有绑定 |
| `#dde2e9` | Dropdown 菜单浮层描边 1px | §5 Dropdown | |
| `#000000` | Description 标题文字 | §26 Description | |
| `#d1dbe7` | Carousel 占位图填充 | §24 Carousel | |
| `#1f2d3d` 不透明度 11%；hover 23% | Carousel 左右箭头底色 | §24 Carousel | CSS：`rgba(31,45,61,0.11)` / `rgba(31,45,61,0.23)` |
| `#4050FF` | Sparkles 图标描边（实例覆盖值） | assets/Icons/Sparkles.svg | 与 `color-primary-brand` 相同，但只是覆盖色，没有绑定变量；图标主组件本身的描边是黑色 |

## 2. 阴影

| 值（CSS） | 用在哪里 | 出处 |
|---|---|---|
| `0 8px 12px 0 rgba(18,19,23,0.1)` | Dropdown 菜单浮层 | §5 Dropdown |
| `0 3px 1px 0 rgba(0,0,0,0.04), 0 3px 8px 0 rgba(0,0,0,0.12)` | SegmentedControls 选中块 | §9 Radio / SegmentedControls |

## 3. 圆角

| 值 | 用在哪里 | 出处 |
|---|---|---|
| 8 | Dialog 2928:14343、Frame 5394、Dropdown 菜单浮层 | §3、§5 |
| 4 | Checkbox 图标、Tag「_tag_add」、Upload 拖拽区 | §10、§33、§20 |
| 6 | Upload 图片列表项 | §20 |
| 14 | Toast | §45 |
| 100 | Switch 轨道、Slider 手柄 | §13、§14 |

注：8 / 6 / 20 / 999 恰好等于 `radius-border-radius-base` / `-small` / `-round` / `-circle` 的值，4 等于 `legacy-border-radius-base`，但上面这些节点**没有绑定**它们，所以仍然算作未 token 化。

## 4. 间距（内边距 / 间距）

设计稿里**没有任何间距变量**，所有 padding 和 itemSpacing 都是直接写的数值。唯一的尺寸类变量是组件高度 `Size/common-component-size-*`（24/32/40），已经放在 `tokens.json` 的 `spacing` 里。

反复出现的内边距（上/右/下/左）：

- `5/16/5/16`（16 处）：Button 默认及 round / text / type 各变体、Dropdown 菜单项默认等
- `5/12/5/12`（8 处）：Input 默认 / filled / textarea、DatetimePicker 输入框
- `2/12/2/12`（4 处）：Button small、Dropdown 菜单项 small、CheckboxButton、Tag「_tag_add」
- `2/8/2/8`（4 处）：Input small、DatetimePicker 输入框、Select、Pagination 每页条数选择
- `9/20/9/20`（3 处）：Button large、Dropdown 菜单项 large、CheckboxButton
- `9/16/9/16`（3 处）：Input large、DatetimePicker 输入框、Select
- `8/16/8/16`（3 处）：Dropdown 分割线、Transfer 表尾、Alert
- `13/16/13/16`：Message

反复出现的间距（Auto Layout itemSpacing）：`4`、`6`、`8`、`10`、`12`、`16`、`20`、`24`、`30`。

每个组件具体用到的数值见 `components.md` 各节的「尺寸与间距」表。

## 5. 有样式、但 tokens.json 结构里没有对应字段

| 样式 | 类型 | 值 |
|---|---|---|
| `jianbain`（渐变） | Paint Style | 线性渐变 `#f5f6ff` → `#b1c3ff`；Figma gradientTransform `[[1.514, 0.854, -0.759], [-6.18, 0.595, 3.599]]` |

`tokens.json` 规定的结构里没有渐变这一类，所以这个样式记在这里，没有塞进 `color`。
