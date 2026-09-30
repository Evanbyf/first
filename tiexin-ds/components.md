# 小贴心 Tiexin AI · 组件清单

来源：Figma「同程管家组件库」 `tl19wuHmHOyNK2C1r7DhQo`（通过 Figma MCP / Plugin API 只读提取，2026-09-30）。

阅读说明：

- **节点链接**指向组件集（COMPONENT_SET）或独立组件（COMPONENT）。
- **属性**：`VARIANT` = 变体属性；`BOOLEAN` / `TEXT` / `INSTANCE_SWAP` = 组件属性（Figma 中名称带 `#id` 后缀，这里保留原名便于对照）。
- **尺寸与间距**：取自每个变体属性“只改这一项、其他保持默认”的代表变体。内边距写作 `上/右/下/左`，圆角多值写作 `左上/右上/右下/左下`。
- **Token 引用**写作 `{token-name}`，名字与 `tokens.json` 一致（Figma 名 `Color/Primary/brand` → `color-primary-brand`，`bg4气泡` → `bg4-qipao`）。没有绑定变量的原始值会直接写出数值，并在 `untokenized.md` 里汇总。
- 标 ⚠️ 的 token 在 Figma 中是**孤立变量**：已从变量面板删除（不在集合列表里），但仍绑定在组件上。详见 README。
- 文字样式写作 `regular/base` 等 Figma 文本样式名（tokens.json 中为 `regular-base`）。
- 设计稿里组件集的 description 字段全部为空；各组件页除标题外也没有找到说明文字，因此「使用说明」统一写「设计稿未说明」，除非另有标注。

---

## 1. Button 按钮

- 页面：按钮 · 节点：[86:8266](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=86-8266) · 共 1116 个变体
- 页面分区：`主变量-亮色`、`主变量-暗色`、`子部件`

**属性**

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| style | VARIANT | basic / text / icon / link / circle | basic |
| round | VARIANT | off / on | off |
| size | VARIANT | small / default / large | default |
| icon | VARIANT | none / left / right / only | none |
| type | VARIANT | default / primary / danger | primary |
| plain | VARIANT | off / on | off |
| background | VARIANT | on / off | on |
| state | VARIANT | default / hover / active | default |
| disabled | VARIANT | off / on | off |
| loading | VARIANT | off / on | off |
| focus#90:0 | BOOLEAN | true / false | false |
| value#92:771 | TEXT | 按钮文字 | "Button" |

**状态**：默认、悬停（state=hover）、按下（state=active）、禁用（disabled=on）、加载（loading=on）、聚焦（focus 布尔）。没有错误态。

**尺寸与间距**

| 变体 | 高度 | 内边距 | 间距 | 圆角 | 文字 | 填充 / 描边 |
|---|---|---|---|---|---|---|
| 默认（primary, default） | 32 `{size-common-component-size-default}`⚠️ | 5/16/5/16 | 6 | 8 `{radius-border-radius-base}`⚠️ | medium/base 14 · `{color-overlay-white}` | `{color-primary-brand}` |
| size=small | 24 `{size-common-component-size-small}`⚠️ | 2/12/2/12 | 8 | 8 | medium/extra-small 12 | 同上 |
| size=large | 40 `{size-common-component-size-large}`⚠️ | 9/20/9/20 | 8 | 8 | medium/base 14 | 同上 |
| round=on | 32 | 5/16/5/16 | 6 | 999 `{radius-border-radius-circle}`⚠️ | medium/base | 同上 |
| style=text | 32 | 5/16/5/16 | 6 | 4 `{legacy-border-radius-base}`⚠️ | medium/base · `{color-primary-brand}` | `{color-background-bg4-qipao}` |
| type=default | 32 | 5/16/5/16 | 6 | 8 | medium/base · `{color-text-text3}` | `{color-background-fill-color-blank}`⚠️ / 描边 1px `{color-border-border2}` |
| type=danger | 32 | 5/16/5/16 | 6 | 8 | medium/base · white | `{color-success-danger}` |
| plain=on | 32 | 5/16/5/16 | 6 | 8 | medium/base · `{color-primary-brand}` | `{color-primary-brand5}` |
| state=hover | 32 | — | — | 8 | white | `{color-primary-brand1}` |
| state=active | 32 | — | — | 8 | white | `{color-primary-link}` |
| disabled=on | 32 | — | — | 8 | white | `{color-primary-brand3}` |
| loading=on | 32 | — | — | 8 | white | `{color-primary-brand1}`（宽 97，含加载图标） |
| icon=left / right | 32 | 5/16/5/16 | 6 | 8 | — | 宽 97（含图标） |

**使用说明**：设计稿未说明。

---

## 2. Button Group 组合按钮

- 页面：组合按钮 · 节点：[449:15290](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=449-15290) · 共 6 个变体

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| type | VARIANT | confirm / delete / primary / default / split-primary / split-default | confirm |

**状态**：组件集没有状态变体（内部嵌套 Button 实例，状态沿用 Button）。

**尺寸与间距**

| 变体 | 尺寸 | 间距 | 文字 |
|---|---|---|---|
| confirm | 175×32 | 12 | medium/base 14 · `{color-text-text3}` |
| delete | 165×32 | 12 | medium/base · `{color-text-text3}` |
| primary | 296×32 | 0（相连） | medium/base · white |
| default | 296×32 | 0 | medium/base · `{color-text-text3}` |
| split-primary | 143×32 | 0 | white |
| split-default | 143×32 | 0 | `{color-text-text3}` |

用到的 token：`{color-primary-brand}`、`{color-success-danger}`、`{color-border-border2}`、`{color-background-fill-color-blank}`⚠️、`{radius-border-radius-base}`⚠️、`{size-common-component-size-default}`⚠️。

**使用说明**：设计稿未说明。

---

## 3. Dialog 弹窗

- 页面：弹窗 · 页面分区：`Component`、`Copy me - light`、`Copy me - dark`
- 组件集 Dialog：[409:2171](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=409-2171) · 2 个变体
- 独立组件：Dialog [2928:14343](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=2928-14343)（331×180）、Dialog [3006:6449](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=3006-6449)（320×229）、Frame 5394 [3008:6688](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=3008-6688)（320×532）、编组 32备份 27 [2917:8564](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=2917-8564)（510×680）

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| align | VARIANT | center / default | default |

**状态**：没有状态变体。

**尺寸与间距**

| 组件 / 变体 | 尺寸 | 内边距 | 圆角 | 标题文字 | 填充 | 阴影 |
|---|---|---|---|---|---|---|
| Dialog align=default / center | 600×300 | 0 | — | medium/large 18 · `{color-text-text2}` | `{color-background-bg-color}`⚠️ | — |
| Dialog 2928:14343 | 331×180 | 0 | 8（未绑定变量） | bold/medium 16 · `#222329`（未绑定） | `{color-background-bg-color}`⚠️ | light/box-shadow-lighter |
| Dialog 3006:6449 | 320×229 | 0/0/6/0 | 8 | regular/base 14 · `{color-text-text5}` | `{color-background-bg-color}`⚠️ | light/box-shadow-lighter |
| Frame 5394 | 320×532 | 0，间距 10 | 8 | bold/medium 16 · `#222329` | `{color-overlay-white}` | light/box-shadow-light |
| 编组 32备份 27 | 510×680 | — | — | 14 · `#323233`（未绑定，混合字重） | — | — |

页面里还用到：`{color-mask-080}`（遮罩）、`{color-primary-brand2}`、`{color-primary-brand5}`、`{color-border-border3}`、`{remote-tiexin-color-background-bg4}`（远程集合「Tiexin」）、示例「创建频道」的文字 `{remote-tiexin-color-text-text1}` / `{remote-tiexin-color-text-text4}`（远程集合「Tiexin」）、`{radius-border-radius-none}`⚠️。

**使用说明**：设计稿未说明。

---

## 4. Card 卡片

- 页面：卡片 · 节点：[419:13809](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=419-13809) · 6 个变体

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| type | VARIANT | image / default / simple | default |
| state | VARIANT | hover / default | default |
| title#638:0 | TEXT | 标题文字 | "Card name" |
| description#638:7 | TEXT | 描述文字 | "Display richer content by adding some configs." |

**状态**：默认、悬停（state=hover，加阴影 light/box-shadow）。

**尺寸与间距**

| 变体 | 尺寸 | 内边距 / 间距 | 圆角 | 文字 | 填充 / 描边 | 阴影 |
|---|---|---|---|---|---|---|
| default | 400×248 | 0 | 8 `{radius-border-radius-base}`⚠️ | regular/medium 16 · `{color-text-text2}` | `{color-background-bg-color}`⚠️ / 1px `{color-border-border3}` | — |
| image | 300×304 | 0 | 8 | regular/medium 16 | 同上 | — |
| simple | 400×304 | 20/20/20/20，间距 16 | 8 | regular/base 14 | `{color-background-bg-color}`⚠️（无描边） | — |
| state=hover | 400×248 | 0 | 8 | regular/medium 16 | 同 default | light/box-shadow |

**使用说明**：设计稿未说明。

---

## 5. Dropdown 下拉菜单

- 页面：下拉菜单 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Dropdown：[463:15658](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=463-15658) · 6 个变体
- 子部件：`_dropmenu_item` [155:10835](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=155-10835)（54 个变体）、`_dropmenu_item`（分组标题 / 分割线）[161:10853](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=161-10853)（2 个变体）
- 独立组件：`_dropmenu` 448:6523（200×232）、`_dropmenu_group` 448:6520、`_dropmenu_Icon` 448:6519、`_dropmenu_multiple` 448:6521、`_dropmenu_description` 448:6522、Dropdown Menu [448:7350](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=448-7350)（220×238，light/box-shadow-light）、Frame 5090 [2925:3689](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=2925-3689)（188×96）、Frame 5329 [2983:36584](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=2983-36584)（188×71）

**Dropdown 属性**

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| type | VARIANT | button / link / split button | link |
| state | VARIANT | default / active | default |

**_dropmenu_item 属性**

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| size | VARIANT | default / large / small | default |
| selected | VARIANT | off / on | off |
| multiple | VARIANT | off / on | off |
| description | VARIANT | off / on | off |
| state | VARIANT | default / hover | default |
| disabled | VARIANT | off / on | off |
| icon#445:0 | BOOLEAN | true / false | false |

`_dropmenu_item`（161:10853）：type = group title / divider（默认 group title）。

**状态**：触发器：默认、展开（state=active）。菜单项：默认、悬停、选中、禁用。

**尺寸与间距**

| 组件 / 变体 | 尺寸 | 内边距 | 间距 | 文字 | 填充 |
|---|---|---|---|---|---|
| Dropdown link | 90×22 | 0 | 4 | medium/base 14 · `{color-primary-link}` | — |
| Dropdown button | 120×32 | 0 | 4 | medium/base · `{color-text-text3}` | — |
| Dropdown split button | 143×32 | 0 | 4 | medium/base · white | — |
| 菜单项 default | 240×32 | 5/16/5/16 | 6 | regular/base 14 · `{color-text-text3}` | — |
| 菜单项 large | 240×40 | 9/20/9/20 | 6 | regular/base | — |
| 菜单项 small | 240×24 | 2/12/2/12 | 6 | regular/extra-small 12 | — |
| 菜单项 selected | 240×32 | 5/16/5/16 | 10 | medium/base · `{color-primary-brand}` | — |
| 菜单项 hover | 240×32 | 5/16/5/16 | 10 | regular/base | `{color-background-bg4-qipao}` |
| 菜单项 disabled | 240×32 | 5/16/5/16 | 10 | `{color-text-text6}` | — |
| 菜单项 description=on | 240×32 | 5/36/5/16 | 10 | regular/base | — |
| 分组标题 | 240×24 | 2/16/2/16 | 10 | regular/extra-small · `{color-text-text4}` | — |
| 分割线 | 240×17 | 8/16/8/16 | 0 | — | — |
| 菜单容器 `_dropmenu` | 200×232 | 4/0/4/0 | 0 | — | — |
| Frame 5090 / 5329 | 188×96 / 188×71 | 6/4/6/4，间距 4 | — | 14 · `#222329` / `{color-text-text1}` | `#ffffff`，描边 1px `#dde2e9`，圆角 8，阴影 `0 8px 12px #121317 10%`（均未绑定） |

页面文字（非组件）：「重启实例」「用量统计」（Frame 5328 示例菜单项）。页面还用到了 `{color-background-bg-color-overlay}`⚠️、`{color-border-border5}`、`{remote-condition-jingshi}`（远程库变量 #f44837）。

**使用说明**：设计稿未说明。

---

## 6. Input 输入框

- 页面：输入框 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Input：[186:7247](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=186-7247) · 252 个变体
- Input-extend：[186:7248](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=186-7248) · 336 个变体
- 子部件：`_input_slot` 186:9762（24）、`_input_password` 119:6277（2）、`_input_clear` 112:9580（6）、`_input_cursor` 112:9586（3）、`_input_rule` 161:11231（6）、`_input_textarea` 120:6316（独立组件，12×12）

**Input 属性**

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| size | VARIANT | small / default / large | default |
| filled | VARIANT | off / on | off |
| icon | VARIANT | none / prefix / suffix | none |
| textarea | VARIANT | off / on | off |
| maxlength | VARIANT | off / on | off |
| required | VARIANT | off / on | off |
| state | VARIANT | default / hover / focus | default |
| disabled | VARIANT | off / on | off |

**Input-extend 属性**

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| size | VARIANT | default / large / small | default |
| filled | VARIANT | on / off | off |
| slot | VARIANT | off / on | off |
| type | VARIANT | password / formatter / preffix-text / preffix-icon / preffix-select / suffix-text / suffix-icon / suffix-select | password |
| required | VARIANT | off / on | off |
| state | VARIANT | default / hover / focus | default |
| disabled | VARIANT | off / on | off |

**子部件属性**：`_input_slot`：size（default/large/small，默认 default）、type（icon/text，默认 text）、layout（suffix/prefix，默认 prefix）、disabled（off/on）。`_input_password`：type（view/hide）。`_input_clear`：size（small/large/default，默认 large）、state（hover/default）。`_input_cursor`：size（large/default/small，默认 large）。`_input_rule`：size（large/default/small）、type（error/success，默认 error）。

**状态**：默认、悬停（state=hover）、聚焦（state=focus）、禁用（disabled=on）、错误 / 必填校验（required=on，描边变 danger）、已填写（filled=on）。

**尺寸与间距**

| 变体 | 高度 | 内边距 | 间距 | 圆角 | 文字 | 填充 / 描边 |
|---|---|---|---|---|---|---|
| 默认 | 32 | 5/12/5/12 | 8 | 8 `{radius-border-radius-base}`⚠️ | regular/base 14 · 占位 `{color-text-text5}` | `{color-background-fill-color-blank}`⚠️ / 1px `{color-border-border2}` |
| size=small | 24 | 2/8/2/8 | 8 | 8 | regular/extra-small 12 | 同上 |
| size=large | 40 | 9/16/9/16 | 8 | 8 | regular/base 14 | 同上 |
| filled=on | 32 | 5/12/5/12 | 8 | 8 | 文字 `{color-text-text3}` | 同上 |
| textarea=on | 60 | 5/12/5/12 | 8 | 8 | regular/base | 同上 |
| state=hover | 32 | — | — | 8 | — | 描边 `{color-text-text6}` |
| state=focus | 32 | — | — | 8 | — | 描边 `{color-primary-brand}` |
| required=on | 32 | — | — | 8（Input-extend 中为 4） | — | 描边 `{color-success-danger}` |
| disabled=on | 32 | — | — | 8（Input-extend 中为 4） | `{color-text-text6}` | `{color-background-bg4-qipao}` / `{color-border-border3}` |
| `_input_slot` 默认 | 32 | 5/16/5/16 | 10 | 8/4/4/8（`{radius-border-radius-base}` + `{radius-border-radius-none}`⚠️） | regular/base · `{color-info-color-info}`⚠️ | `{color-background-bg4-qipao}` / `{color-border-border2}` |

注意：Input 的高度没有绑定 Size 变量（和 Button 不同），是由内边距 + 行高撑出来的。

**使用说明**：设计稿未说明。

---

## 7. Link 链接

- 页面：链接 · 节点：[90:40112](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=90-40112) · 54 个变体

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| type | VARIANT | default / primary / danger | primary |
| underline | VARIANT | off / on | off |
| icon | VARIANT | left / none / right | none |
| state | VARIANT | default / hover | default |
| disabled | VARIANT | off / on | off |
| value#92:2503 | TEXT | 链接文字 | "Link" |

**状态**：默认、悬停、禁用。

**尺寸与间距**：高 22，图文间距 6，没有内边距；文字 medium/base 14。

| 变体 | 文字颜色 |
|---|---|
| primary（默认） | `{color-primary-link}` |
| default | `{color-text-text3}` |
| danger | `{color-success-danger}` |
| state=hover | `{color-primary-brand1}` |
| disabled=on | `{color-primary-brand2}` |

页面还用到 `{color-error-color-error-light-3}`⚠️ / `{color-error-color-error-light-5}`⚠️（danger 的悬停 / 禁用）。

**使用说明**：设计稿未说明。

---

## 8. Cascader 级联选择器（页面「选择器」）

- 页面：选择器 · 页面分区：`Cascader Dropmenu`、`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Cascader：[545:11554](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=545-11554) · 2 个变体
- 下拉面板：`Cascader _default` 448:4052、`Cascader _checkbox` 448:4056、`Cascader _radio` 448:4060（各 3 个变体）；`_cascader_option` 337:13872（42）；`_cascader_list` 338:15412（6）；独立组件 `Cascader Menu` 338:15499（400×300，light/box-shadow）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Cascader | state | VARIANT | focus / default | default |
| Cascader _default / _checkbox / _radio | level | VARIANT | 1 / 2 / 3 | 2 |
| _cascader_option | type | VARIANT | default / checkbox / radio | default |
| | with child | VARIANT | off / on | on |
| | selected | VARIANT | off / on | off |
| | display | VARIANT | default / active | default |
| | state | VARIANT | default / hover | default |
| | disabled | VARIANT | off / on | off |
| _cascader_list | type | VARIANT | default / checkbox / radio | default |
| | with child | VARIANT | off / on | on |

**状态**：触发器：默认、聚焦。选项：默认、悬停、选中、展开（display=active）、禁用。

**尺寸与间距**

| 组件 / 变体 | 尺寸 | 内边距 | 间距 | 文字 | 填充 / 描边 |
|---|---|---|---|---|---|
| Cascader | 200×32 | 0 | 2 | regular/base 14 · `{color-text-text5}` | （内嵌 Input） |
| 面板 level 1 / 2 / 3 | 200 / 400 / 600 × 328 | 0 | 0 | regular/base | — |
| _cascader_list | 200×328 | 4/0/4/0 | 0 | — | 分栏描边 `{color-border-border2}` |
| 选项 默认 | 240×32 | 5/16/5/16 | 10 | regular/base · `{color-text-text3}` | — |
| 选项 selected | 240×32 | — | — | medium/base · `{color-primary-brand}` | — |
| 选项 hover | 240×32 | — | — | — | `{color-background-bg4-qipao}` |
| 选项 disabled | 240×32 | — | — | `{color-text-text6}` | — |

**使用说明**：设计稿未说明。

---

## 9. Radio 单选框（含 SegmentedControls 分段控制器）

- 页面：单选框 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Radio：[91:41823](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=91-41823) · 36 个变体
- Radio Icon：[91:41774](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=91-41774) · 12
- Radio Group：[92:48060](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=92-48060) · 81
- SegmentedControls：[3051:2227](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=3051-2227) · 12；子部件 `_Segment` 3051:2480（4）、`_IconPlaceholder` 3051:2499（9）、`_TabPattern/Hug content line` 3051:2489（独立组件）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Radio | size | VARIANT | default / large / small | default |
| | checked | VARIANT | off / on | off |
| | indeterminate | VARIANT | off | off |
| | border | VARIANT | off / on | off |
| | state | VARIANT | default / hover | default |
| | disabled | VARIANT | off / on | off |
| | value#92:2680 | TEXT | 选项文字 | "Option" |
| Radio Icon | size | VARIANT | default / small | default |
| | checked / state / disabled | VARIANT | off·on / default·hover / off·on | off / default / off |
| Radio Group | size | VARIANT | small / default / large | default |
| | type | VARIANT | icon / border / button | icon |
| | num | VARIANT | 2 … 10 | 2 |
| SegmentedControls | Icon | VARIANT | False / True | False |
| | Tabs | VARIANT | 2 / 3 / 4 / 5 / 6 / 7 | 7 |
| _Segment | Active / Line / Icon / Text | VARIANT | True·False / None / False·True / True·False | True / None / False / True |
| _IconPlaceholder | Size | VARIANT | 8 / 12 / 16 / 18 / 20 / 22 / 24 / 28 / 32 | 16 |

**状态**：默认、悬停、选中、禁用。

**尺寸与间距**

| 变体 | 尺寸 | 内边距 | 间距 | 圆角 | 文字 | 填充 / 描边 |
|---|---|---|---|---|---|---|
| Radio 默认 | 67×32（高 `{size-common-component-size-default}`⚠️） | 5/0/5/0 | 8 | — | medium/base 14 · `{color-text-text3}` | — |
| Radio large | 高 40 `{size-common-component-size-large}`⚠️ | 9/0/9/0 | 8 | — | medium/base | — |
| Radio small | 高 24 | 2/0/2/0 | 8 | — | medium/extra-small 12 | — |
| Radio checked | 32 | — | — | — | 文字 `{color-text-text1}` | — |
| Radio border=on | 93×32 | 5/16/5/10 | 8 | 8 `{radius-border-radius-base}`⚠️ | medium/base | `{color-background-fill-color-blank}`⚠️ / 1px `{color-border-border1}` |
| Radio disabled | 32 | — | — | — | `{color-text-text6}` | — |
| Radio Icon 默认 | 14×14 | — | — | 999 `{radius-border-radius-circle}`⚠️ | — | `{color-background-fill-color-blank}`⚠️ / 1.5px `{color-border-border1}` |
| Radio Icon small | 12×12 | — | — | 999 | — | 同上 |
| Radio Icon checked | 14×14 | — | — | 999 | — | 描边 `{color-primary-brand}` |
| Radio Icon hover | 14×14 | — | — | 999 | — | 描边 `{color-primary-brand1}` |
| Radio Icon disabled | 14×14 | — | — | 999 | — | `{color-background-bg4-qipao}` / `{color-border-border1}` |
| Radio Group icon | 高 32 | 0 | 24 | — | medium/base | — |
| Radio Group border | 高 32 | 0 | 12 | — | medium/base | — |
| Radio Group button | 高 32 | 0 | 0 | 8 | regular/base | `{color-background-fill-color-blank}`⚠️ / `{color-border-border2}` |
| SegmentedControls | 高 32 | 0 | 0 | — | 远程样式 `Default size/Subheadline strong` 15 · `{color-text-text3}` / 选中 `{color-text-text1}` | — |
| _Segment 选中 | 48×28 | — | — | — | 同上 | 阴影 `0 3px 1px #000 4%` + `0 3px 8px #000 12%`（未绑定） |

说明：SegmentedControls 用了**远程库**里的文本样式 `Default size/Subheadline strong`、`Default size/Caption 1 strong`，本文件里没有它们的定义。

**使用说明**：设计稿未说明。

---

## 10. Checkbox 复选框

- 页面：复选框 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Checkbox：[91:41554](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=91-41554) · 54 个变体
- Checkbox Icon：[91:41372](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=91-41372) · 18
- Checkbox Button：[91:41503](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=91-41503) · 12
- Checkbox Group：[92:44476](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=92-44476) · 81

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Checkbox | size | VARIANT | small / default / large | default |
| | checked | VARIANT | off / on | off |
| | indeterminate | VARIANT | off / on | off |
| | border | VARIANT | off / on | off |
| | state | VARIANT | default / hover | default |
| | disabled | VARIANT | off / on | off |
| | value#92:2625 | TEXT | 选项文字 | "Option" |
| Checkbox Icon | size | VARIANT | default / small | default |
| | checked / indeterminate / state / disabled | VARIANT | off·on / off·on / default·hover / off·on | off / off / default / off |
| Checkbox Button | size | VARIANT | small / default / large | default |
| | checked / state / disabled | VARIANT | off·on / default·hover / off·on | off / default / off |
| | value#92:2612 | TEXT | — | "Option" |
| Checkbox Group | size / type / num | VARIANT | 同 Radio Group | default / icon / 2 |

**状态**：默认、悬停、选中、半选（indeterminate）、禁用。

**尺寸与间距**

| 变体 | 尺寸 | 内边距 | 间距 | 圆角 | 文字 | 填充 / 描边 |
|---|---|---|---|---|---|---|
| Checkbox 默认 | 67×32（`{size-common-component-size-default}`⚠️） | 5/0/5/0 | 8 | — | medium/base 14 · `{color-text-text3}` | — |
| Checkbox small / large | 高 24 / 40 | 2/0/2/0 · 9/0/9/0 | 8 | — | medium/extra-small 12 / medium/base | — |
| Checkbox checked | 32 | — | — | — | `{color-primary-brand}` | — |
| Checkbox border=on | 93×32 | 5/16/5/10 | 8 | 8 `{radius-border-radius-base}`⚠️ | — | `{color-background-fill-color-blank}`⚠️ / 1px `{color-border-border2}` |
| Checkbox disabled | 32 | — | — | — | `{color-text-text6}` | — |
| Checkbox Icon 默认 | 14×14 | — | — | 4（未绑定变量） | — | `{color-background-fill-color-blank}`⚠️ / 1px `{color-border-border2}` |
| Checkbox Icon small | 12×12 | — | — | 6 `{radius-border-radius-small}`⚠️ | — | 同上 |
| Checkbox Icon checked | 14×14 | — | — | 4 | — | `{color-primary-brand}` |
| Checkbox Icon hover | 14×14 | — | — | 4 | — | 描边 `{color-primary-brand}` |
| Checkbox Icon disabled | 14×14 | — | — | 4 | — | `{color-background-bg4-qipao}` / `{color-border-border2}` |
| Checkbox Button 默认 | 76×32 | 5/16/5/16 | 10 | — | regular/base · `{color-text-text3}` | `{color-background-fill-color-blank}`⚠️ / `{color-border-border2}` |
| Checkbox Button small / large | 高 24 / 40 | 2/12/2/12 · 9/20/9/20 | 10 | — | regular/extra-small / regular/base | 同上 |
| Checkbox Button checked | 32 | — | — | — | white | `{color-primary-brand}` |
| Checkbox Button hover | 32 | — | — | — | `{color-primary-brand}` | — |
| Checkbox Button disabled | 32 | — | — | — | `{color-text-text6}` | `{color-background-bg4-qipao}` |
| Checkbox Group | 高 32 | 0 | 24（icon）/ 12（border）/ 0（button） | button 型 8 | — | — |

**使用说明**：设计稿未说明。

---

## 11. Color Picker 颜色选择器

- 页面：颜色选择器 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Color Picker：[419:1271](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=419-1271) · 6 个变体
- 子部件：`_color_picker_panel` 419:1164（3）、`_color_picker_trigger` 419:1167（12）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Color Picker | state | VARIANT | default / active | default |
| | type | VARIANT | default / alpha / predefined | default |
| _color_picker_panel | type | VARIANT | predefined / default / alpha | default |
| _color_picker_trigger | size | VARIANT | default / large / small | default |
| | default value | VARIANT | off / on | on |
| | state | VARIANT | default / hover | default |

**状态**：默认、悬停（触发器）、展开（state=active）。

**尺寸与间距**

| 组件 / 变体 | 尺寸 | 内边距 | 间距 | 圆角 | 填充 / 描边 | 阴影 |
|---|---|---|---|---|---|---|
| 触发器 default | 32×32（宽高都是 `{size-common-component-size-default}`⚠️） | 6 | 10 | 8 `{radius-border-radius-base}`⚠️ | `{color-background-fill-color-blank}`⚠️ / `{color-border-border2}` | — |
| 触发器 large / small | 40×40 / 24×24（Size large / small） | 6 / 4 | 10 | 8 | 同上 | — |
| 触发器 hover | 32×32 | 6 | — | 8 | 描边 `{color-text-text6}` | — |
| 面板 default | 314×232 | 8 | 12 | 8 | `{color-background-bg-color-overlay}`⚠️ / `{color-border-border3}` | 远程样式 `box-shadow-light` |
| 面板 predefined / alpha | 318×312 / 318×256 | 10 | 12 | 8 | 同上 | 同上 |

面板文字：regular/extra-small 12 · `{color-text-text5}`。

**使用说明**：设计稿未说明。

---

## 12. Datetime Picker 日期时间选择器

- 页面：日期时间选择器 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Datetime Picker：[362:56585](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=362-56585) · 32 个变体
- 子部件：`_datetime_text` 345:22168（15）、`_datetime_select` 345:22428（252）、`_time_item` 350:2298（9）、`_time_picker_dropmenu` 350:6638（4）、`_datetime_picker_footer` 360:9672（2）、`_date_arrow_button` 361:39284（3）、`_date_table_th` 361:39342（7）、`_date_table_td` 361:39447（16）、`_date_picker_dropmenu` 361:41522（6）、`_datetime_select` 362:42250（2）、`_date_shortcut` 362:44413（2）、`_datetime_picker_dropmenu` 362:45775（6）、独立组件 `_datetime_picker_header` 361:39310

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Datetime Picker | type | VARIANT | datetime / date / time | datetime |
| | focus | VARIANT | off / on | off |
| | selected | VARIANT | off / on | off |
| | range | VARIANT | off / on | off |
| | shortcut | VARIANT | on / off | off |
| _datetime_select（345:22428） | size | VARIANT | default / large / small | default |
| | range / selected / required / disabled | VARIANT | off / on | off |
| | type | VARIANT | date / time / date&time | date |
| | state | VARIANT | default / hover / focus | default |
| _datetime_text | size / state / selected / disabled | VARIANT | default·large·small / default·focus / off·on / off·on | default / default / off / off |
| | Text#345:0 | TEXT | — | "Date" |
| _time_item | type | VARIANT | number / arrow / placeholder | number |
| | selected / state / disabled | VARIANT | off·on / default·hover / on·off | off / default / off |
| _date_table_td | today / range / selected / disabled | VARIANT | off / on | off |
| | selected-type | VARIANT | start / end / middle / default | default |
| | state | VARIANT | default / hover | default |
| | date#361:0 | TEXT | — | "29" |
| _date_table_th | date | VARIANT | Sun … Sat | Sun |
| _date_arrow_button | state | VARIANT | placeholder / default / hover | default |
| _date_picker_dropmenu / _datetime_picker_dropmenu | range / selected / shortcut | VARIANT | off / on | off |
| _time_picker_dropmenu | with arrow / range | VARIANT | on·off / off·on | off / off |
| _datetime_picker_footer | type | VARIANT | date / time | time |
| _date_shortcut | state | VARIANT | default / hover | default |

**状态**：默认、悬停、聚焦、已选、错误 / 必填（required=on，描边 danger）、禁用；日期格：今天、选中、区间起止 / 中间、悬停、禁用。

**尺寸与间距**

| 组件 / 变体 | 尺寸 | 内边距 | 间距 | 圆角 | 文字 | 填充 / 描边 / 阴影 |
|---|---|---|---|---|---|---|
| 输入框 default | 400×32 | 5/12/5/12 | 8 | 8 `{radius-border-radius-base}`⚠️ | regular/base 14 · `{color-text-text5}` | `{color-background-fill-color-blank}`⚠️ / `{color-border-border2}` |
| 输入框 large / small | 高 40 / 24 | 9/16/9/16 · 2/8/2/8 | 8 | 8 | regular/base / regular/extra-small | 同上 |
| 输入框 hover / focus | 32 | — | — | 8 | — | 描边 `{color-text-text6}` / `{color-primary-brand}` |
| 输入框 required=on | 32 | — | — | 4 | — | 描边 `{color-success-danger}` |
| 输入框 disabled | 32 | — | — | 4 | `{color-text-text6}` | `{color-background-bg4-qipao}` / `{color-border-border3}` |
| 日期面板 | 312×335（range 624） | 0 | 0 | — | 头部 medium/medium 16 · `{color-text-text3}` | light/box-shadow |
| 日期时间面板 | 312×415（range 624） | 0 | 0 | — | — | light/box-shadow |
| 时间面板 | 165×240（range 378×300） | 0 | 0 | — | regular/extra-small | light/box-shadow |
| 日期格 td | 40×36 | 0 | — | — | regular/extra-small 12 · `{color-text-text3}`；today → medium · `{color-primary-brand}`；selected → white；disabled → `{color-text-text6}` | — |
| 表头 th | 40×40 | 10/8/10/8 | — | — | regular/extra-small | — |
| 时间项 | 48×32 | 6/16/6/16 | — | — | regular/extra-small；selected → medium · `{color-text-text2}` | hover `{color-background-bg4-qipao}` |
| 面板底栏 time / date | 240×32 / 240×40 | 4 / 8/12/8/12 | 4 | — | medium/extra-small | `{color-background-bg-color-overlay}`⚠️ / `{color-border-border2}` |
| 快捷项 | 98×32 | 5/12/5/12 | — | — | regular/base；hover `{color-primary-brand}` | — |
| 翻页按钮 | 24×24 | 6 | — | — | — | — |

**使用说明**：设计稿未说明。

---
## 13. Switch 开关

- 页面：开关 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Switch：[234:8425](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=234-8425) · 72 个变体
- 子部件：`_switch_basic` 232:19145（96）、`_switch_click` 232:21088（9，滑块圆点）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Switch | size | VARIANT | small / default / large | default |
| | type | VARIANT | default / text / text-inline / icon / icon-inline / action-icon | default |
| | switch | VARIANT | off / on | on |
| | custom | VARIANT | off / on | off |
| _switch_basic | size | VARIANT | small / default / large | default |
| | type | VARIANT | default / action-icon / icon-inline / text | default |
| | switch | VARIANT | off / on | on |
| | custom-color | VARIANT | off / on | off |
| | disabled | VARIANT | off / on | off |
| | loading | VARIANT | off（只有这一个值） | off |
| _switch_click | type | VARIANT | check / none / icon | none |
| | size | VARIANT | default / large / small | default |

**状态**：开、关、禁用（`_switch_basic` disabled=on）、自定义颜色。loading 属性存在，但只有 off 一个值，设计稿里没有加载态。

**尺寸与间距**

| 变体 | 尺寸 | 内边距 | 间距 | 圆角 | 填充 |
|---|---|---|---|---|---|
| 轨道 default（开） | 40×20 | 2 | 4 | 100（未绑定变量） | `{color-primary-brand}` |
| 轨道 small / large | 30×16 / 50×24 | 2 | 2 / 6 | 100 | 同上 |
| 轨道 switch=off | 40×20 | 2 | 4 | 100 | `{color-border-border2}` |
| 轨道 custom-color | 40×20 | — | — | 100 | `{color-success-safety}` |
| 轨道 disabled | 40×20 | — | — | 100 | `{color-primary-brand2}` |
| 轨道 type=text | 40×20 | — | — | 100 | 内文字 regular/extra-small 12 · white |
| 圆点 default / large / small | 16 / 20 / 12 | — | — | 999 `{radius-border-radius-circle}`⚠️ | `{color-overlay-white}` |
| Switch 外框 default / small / large | 高 32 / 24 / 40（Size 变量⚠️） | 5/0/5/0 · 4/0/4/0 · 5/0/5/0 | 10 | — | — |
| Switch type=text | 134×32 | 5/0/5/0 | 10 | — | 旁侧文字 medium/base 14 · `{color-text-text2}` |

页面还用到 `{color-error-color-error-light-5}`⚠️、`{color-success-color-success-light-5}`⚠️、`{color-success-danger}`。

**使用说明**：设计稿未说明。

---

## 14. Slider 滑块

- 页面：滑块 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Slider：[229:5343](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=229-5343) · 24 个变体
- 子部件：`_handle` 229:5032（3）、`_progress` 229:5059（12）、`_progress_handle` 229:5064（6）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Slider | % | VARIANT | 100 / 0 / 50 / Default | 0 |
| | state | VARIANT | default / hover | default |
| | disabled | VARIANT | off / on | off |
| | type | VARIANT | default / step | default |
| | range | VARIANT | off / on | off |
| | marks#568:21 | BOOLEAN | true / false | false |
| _handle | state / disabled | VARIANT | default·hover / off·on | default / off |
| _progress | type / select / disabled / vertical | VARIANT | step·default / off·on / off·on / off·on | default / off / off / off |
| _progress_handle | start / state / disabled | VARIANT | off·on / default·hover / off·on | on / default / off |

**状态**：默认、悬停（显示数值气泡）、禁用。

**尺寸与间距**

| 部件 | 尺寸 | 圆角 | 填充 / 描边 | 文字 |
|---|---|---|---|---|
| 轨道 | 500×6（竖向 6×50） | — | 已选段 `{color-primary-brand}` | — |
| 手柄 | 20×20 | 100（未绑定） | `{color-overlay-white}` / 2px `{color-primary-brand}` | — |
| 手柄 hover（含气泡） | 40×66，间距 4 | — | — | regular/extra-small 12 · white |
| 手柄 disabled | 20×20 | 100 | white / 2px `{color-text-text5}` | — |

页面还用到 `{color-border-border2}`、`{color-border-border3}`、`{color-border-border5}`、`{color-info-color-info}`⚠️、`{color-overlay-black}`、`{radius-border-radius-base}`⚠️。

**使用说明**：设计稿未说明。

---

## 15. Form 表单

- 页面：表单 · 页面分区：`Component`、`_parts`、`Copy me - light`、`Copy me - dark`
- Form：[410:22217](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=410-22217) · 3 个变体
- Form-item-right 410:16854（32）、Form-item-left 410:22219（32）、Form-item-top 410:23420（32）、`_form_label` 409:4743（6）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Form | align | VARIANT | top / right / left | right |
| Form-item-right / left / top | type | VARIANT | input / password / formatter / http: / select / checkbox / options / radio / textarea / switch / upload / datetime | input |
| | size | VARIANT | default / large / small | default |
| _form_label | size | VARIANT | default / large / small | default |
| | align | VARIANT | right / left | left |
| | info#409:26 | BOOLEAN | true / false | false |
| | required#409:33 | BOOLEAN | true / false | false |
| | value#409:40 | TEXT | 标签文字 | "Basic form" |

**状态**：表单本身没有状态变体（状态由里面嵌套的输入类组件提供）。

**尺寸与间距**

| 组件 / 变体 | 尺寸 | 间距 | 文字 |
|---|---|---|---|
| Form right / left | 432×320 | 行间距 20 | regular/base 14 · `{color-text-text3}` |
| Form top | 432×500 | 20 | 同上 |
| Form-item-right / left | 432×32（large 40、small 24、textarea 60） | 标签与控件间距 12 | regular/base（small 为 regular/extra-small） |
| Form-item-top | 432×62（large 70、small 52、textarea 90） | 8 | 同上 |
| _form_label | 120×32 / 40 / 24（`{size-common-component-size-*}`⚠️） | 4 | regular/base · `{color-text-text3}` |

页面非组件文字：「Here’s a description of the form.」（示例文案）。

**使用说明**：设计稿未说明。

---

## 16. Input Number 数字输入框

- 页面：数字输入框 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Input Number：[229:3618](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=229-3618) · 48 个变体
- 子部件：`_number_button` 229:26（36）、`_number_input` 229:3282（9）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Input Number | size | VARIANT | default / large / small | default |
| | position | VARIANT | right / default | default |
| | disabled | VARIANT | off / on | off |
| | state | VARIANT | default / hover / focus | default |
| | minimum | VARIANT | off / on | on |
| _number_button | size / position / control / state / disabled | VARIANT | default·large·small / right·default / -·+ / default·hover / off·on | default / default / - / default / off |
| _number_input | size / state / disabled | VARIANT | default·large·small / default·focus / off·on | default / default / off |
| | number#229:0 | TEXT | — | "0" |

**状态**：默认、悬停、聚焦、禁用、到达最小值（minimum=on，减号置灰）。

**尺寸与间距**

| 变体 | 尺寸 | 圆角 | 文字 | 填充 / 描边 |
|---|---|---|---|---|
| 默认 | 120×32 | 8 `{radius-border-radius-base}`⚠️ | regular/base 14 · `{color-text-text3}` | `{color-background-bg4-qipao}` / 1px `{color-border-border5}` |
| large / small | 144×40 / 90×24 | 8 | regular/base / regular/extra-small | 同上 |
| hover / focus | 120×32 | 8 | — | 描边 `{color-text-text6}` / `{color-primary-brand}` |
| disabled | 120×32 | 8 | `{color-text-text6}` | 描边 `{color-border-border3}` |
| 加减按钮 default / large / small | 32×32 / 40×40 / 24×24 | — | — | 内边距 9 / 13 / 6；`{color-background-bg4-qipao}` / `{color-border-border5}` |
| 加减按钮 position=right | 32×16 | — | — | 内边距 1/9/1/9 |
| 数值区 | 72×32（40 / 24） | — | 内边距 5/0/5/0（9 / 2） | — |

**使用说明**：设计稿未说明。

---

## 17. Rate 评分

- 页面：评分 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Rate：[441:32298](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=441-32298) · 6 个变体；子部件 `_rate_star` 441:32148（5）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Rate | selected | VARIANT | off / on | off |
| | half | VARIANT | on / off | off |
| | state | VARIANT | default / hover | default |
| | text#441:0 | BOOLEAN | true / false | false |
| _rate_star | selected / half / state | VARIANT | off·on / off·on / default·hover | off / off / default |

**状态**：默认、悬停、已选、半星。

**尺寸与间距**：Rate 124×20，星间距 6；单星 20×20，内边距 1。星的颜色是矢量填充，没有在节点层读到绑定变量；页面里出现了 `{color-border-border-color-darker}`⚠️（未选中星）和 `{color-border-border2}`。

**使用说明**：设计稿未说明。

---

## 18. Select 选择器（页面「选择器 」，名字末尾带空格）

- 页面：选择器␠ · 页面分区：`Component`、`Copy me - light`、`Copy me - dark`
- Select：[166:1516](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=166-1516) · 210 个变体（下拉面板复用「下拉菜单」页的 `_dropmenu_*`）

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| size | VARIANT | default / large / small | default |
| selected | VARIANT | off / on | off |
| multiple | VARIANT | off / on | off |
| collapse | VARIANT | off / on | off |
| filterable | VARIANT | off / on | off |
| required | VARIANT | off / on | off |
| state | VARIANT | default / hover / focus | default |
| disabled | VARIANT | off / on | off |

**状态**：默认、悬停、聚焦、已选、错误 / 必填（required=on）、禁用。

**尺寸与间距**：和 Input 一样。默认 300×32，内边距 5/12/5/12，间距 8，圆角 8 `{radius-border-radius-base}`⚠️，占位文字 regular/base · `{color-text-text5}`，已选文字 `{color-text-text3}`；large 40（9/16/9/16），small 24（2/8/2/8，regular/extra-small）；描边 默认 `{color-border-border2}` / hover `{color-text-text6}` / focus `{color-primary-brand}` / required `{color-success-danger}` / disabled `{color-border-border3}` + 填充 `{color-background-bg4-qipao}`。多选标签用到 `{color-info-color-info-light-9}`⚠️、`{radius-border-radius-small}`⚠️。

**使用说明**：设计稿未说明。

---
## 19. Transfer 穿梭框

- 页面：穿梭框 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Transfer：[363:65309](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=363-65309) · 8 个变体
- 子部件：`_transfer` 363:64456（4）、`_transfer_option` 363:64304（4）、`_transfer_header` 363:64329、`_transfer_footer` 363:64328（独立组件）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Transfer | button type | VARIANT | text / icon | icon |
| | operation | VARIANT | off / on | off |
| | selected | VARIANT | off / on | off |
| _transfer | type | VARIANT | target / source | source |
| | empty | VARIANT | off / on | off |
| | operations#363:17 | BOOLEAN | true / false | false |
| _transfer_option | state / selected / disabled | VARIANT | default·hover / off·on / off·on | default / off / off |

**状态**：选项：默认、悬停、选中、禁用；列表：空状态（empty=on）。

**尺寸与间距**

| 部件 | 尺寸 | 内边距 | 间距 | 圆角 | 文字 | 填充 / 描边 |
|---|---|---|---|---|---|---|
| Transfer icon / text | 492×300 / 599×300 | 0 | 16 | — | medium/base 14 | — |
| 列表面板 | 180×272 | 0 | 0 | 8 `{radius-border-radius-base}`⚠️ | medium/base · `{color-text-text3}` | `{color-background-fill-color-blank}`⚠️ / 1px `{color-border-border4}` |
| 表头 | 160×32 | 5/16/5/16 | 8 | — | medium/base | `{color-background-bg4-qipao}` / `{color-border-border4}` |
| 表尾 | 160×40 | 8/16/8/16 | 8 | — | medium/extra-small 12 | 描边 `{color-border-border4}` |
| 选项 | 160×32 | 5/16/5/16 | 8 | — | medium/base；hover / 选中 `{color-primary-brand}`；禁用 `{color-text-text6}` | — |

**使用说明**：设计稿未说明。

---

## 20. Upload 上传

- 页面：上传 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Upload：[408:757](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=408-757) · 10 个变体
- 子部件：`_upload_file` 407:19611（8）、`_upload_description` 408:382（2）、`_upload_img` 407:19827（3）、`_upload_photo` 407:19996（3）、`_upload_trigger` 407:20942（4）、`_upload_dragged` 408:170（3）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Upload | type | VARIANT | button / drag / photo | button |
| | uploaded | VARIANT | on / off | off |
| | thumbnail | VARIANT | off / on | off |
| | description#408:0 | BOOLEAN | true / false | true |
| | server#408:10 | BOOLEAN | true / false | false |
| _upload_file | size / type / state | VARIANT | default·small / default·loading / default·hover | default / default / default |
| _upload_description | type | VARIANT | default / error | default |
| _upload_img / _upload_photo | state | VARIANT | loading / default / hover | default |
| _upload_trigger | background / state | VARIANT | off·on / default·hover | off / default |
| _upload_dragged | state | VARIANT | active / default / hover | default |

**状态**：默认、悬停、上传中（loading）、拖入激活（active）、错误（description type=error）、已上传。

**尺寸与间距**

| 部件 | 尺寸 | 内边距 | 间距 | 圆角 | 文字 | 填充 / 描边 |
|---|---|---|---|---|---|---|
| Upload button | 233×60 | 0 | 8 | — | medium/base 14 · white（按钮） | — |
| Upload drag | 360×228 | 0 | 8 | — | regular/base | — |
| 文件行 default / small | 360×26 / 360×24 | 2/4/2/4 | 0 | hover 时 8 `{radius-border-radius-base}`⚠️ | medium/base / medium/extra-small · `{color-text-text3}`；hover `{color-primary-brand}` | hover `{color-background-bg4-qipao}` |
| 描述文字 | 64×20 | 0 | — | — | regular/extra-small · `{color-text-text4}`；error `{color-success-danger}` | — |
| 图片列表项 | 300×90 | 10 | 12 | 6（未绑定） | regular/base | `{color-background-fill-color-blank}`⚠️ / `{color-border-border2}` |
| 照片墙 / 触发器 | 148×148 | 0 | 0 | 8 `{radius-border-radius-base}`⚠️ | — | 同上；hover 描边 `{color-primary-brand}`；background=on 填充 `{color-background-fill-color-lighter}`⚠️ |
| 拖拽区 | 360×200 | 0 | 8 | 4（未绑定） | regular/base | 默认同上；hover 描边 `{color-primary-brand}`；active 填充 `{color-primary-brand5}` + 描边 brand |

**使用说明**：设计稿未说明。

---

## 21. Avatar 头像

- 页面：头像 · 节点：[100:7344](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=100-7344) · 24 个变体

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| size | VARIANT | small / default / large | default |
| type | VARIANT | default / icon / text / image | default |
| shape | VARIANT | square / circle | circle |

**状态**：没有交互状态。

**尺寸与间距**

| 变体 | 尺寸 | 内边距 | 圆角 | 填充 / 文字 |
|---|---|---|---|---|
| default | 40×40 | 8 | 999 `{radius-border-radius-circle}`⚠️ | `{color-text-text6}` |
| small / large | 24×24 / 56×56 | 5 / 12 | 999 | 同上 |
| type=icon | 40×40 | 11 | 999 | 同上 |
| type=text | 40×40 | 9/4/9/4 | 999 | regular/base 14 · white |
| type=image | 40×40 | 0 | 999 | 图片 |
| shape=square | 40×40 | 8 | 8 `{radius-border-radius-base}`⚠️ | 同上 |

页面示例文字：「Alice」「User」。

**使用说明**：设计稿未说明。

---

## 22. Badge 徽标 / 角标

- 页面：徽标 / 角标 · 节点：[92:50131](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=92-50131) · 8 个变体

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| type | VARIANT | primary / success / warning / danger | primary |
| dot | VARIANT | off / on | off |
| value#92:760 | TEXT | 数字 / 文字 | "1" |

**状态**：没有交互状态。

**尺寸与间距**：数字徽标 17×18，内边距 0/6/0/6，圆角 999 `{radius-border-radius-circle}`⚠️，描边 1px `{color-overlay-white}`，文字 regular/extra-small 12 · white。dot=on 为 18×18 容器，内边距 5。

| type | 填充 |
|---|---|
| primary | `{color-primary-brand}` |
| success | `{color-success-safety}` |
| warning | `{color-success-warning}` |
| danger | `{color-success-danger}` |

**使用说明**：设计稿未说明。

---
## 23. Calendar 日历

- 页面：日历 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Calendar（独立组件）：[464:27189](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=464-27189)（776×540）
- 子部件：`_calendar_header` 464:27151（2）、`_calendar_day` 463:16771（10）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| _calendar_header | type | VARIANT | year / month | month |
| _calendar_day | selected | VARIANT | off / on | off |
| | today | VARIANT | off / on | off |
| | state | VARIANT | hover / default | default |
| | disabled | VARIANT | off / on | **on**（设计稿里默认变体就是禁用态） |

**状态**：日期格：默认、悬停、选中、今天、禁用（非本月）。

**尺寸与间距**

| 部件 | 尺寸 | 内边距 | 间距 | 文字 | 填充 / 描边 |
|---|---|---|---|---|---|
| 头部 | 776×48 | 12/20/12/20 | 8 | regular/medium 16 · `{color-text-text2}` | 下描边 `{color-border-border4}` |
| 日期格 | 110×84 | 8 | 10 | regular/medium 16 · 可用 `{color-text-text3}` / 禁用 `{color-text-text6}` | `{color-background-fill-color-blank}`⚠️ / 1px `{color-border-border4}`；hover 填充 `{color-primary-brand5}` |

**使用说明**：设计稿未说明。

---

## 24. Carousel 轮播图

- 页面：轮播图 · 页面分区：`_parts`、`Component`（这一页没有 light / dark 示例）
- Carousel：[399:18415](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=399-18415) · 10 个变体
- 子部件：`_carousel_arrow` 397:17378（4）、`_carousel_indicator_item` 397:17430（12）、`_carousel_indicator` 399:17874（4）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Carousel | align | VARIANT | vertical / horizontal | horizontal |
| | indicator | VARIANT | outside / inside | inside |
| | arrow | VARIANT | on / off | on |
| | card | VARIANT | off / on | off |
| _carousel_arrow | arrow / hover | VARIANT | right·left / off·on | left / off |
| _carousel_indicator_item | theme / state / align | VARIANT | dark·light / default·hover·active / horizontal·vertical | dark / active / vertical |
| _carousel_indicator | theme / align | VARIANT | light·dark / horizontal·vertical | dark / horizontal |

**状态**：箭头：默认、悬停；指示点：默认、悬停、激活。

**尺寸与间距**

| 部件 | 尺寸 | 内边距 | 圆角 | 填充 |
|---|---|---|---|---|
| Carousel | 900×200（indicator=outside 时 900×230，间距 4） | — | — | 占位图 `#d1dbe7`（未绑定） |
| 箭头 | 36×36 | 12 | 999 `{radius-border-radius-circle}`⚠️ | `#1f2d3d` 11%，hover 23%（未绑定） |
| 指示点项 竖排 / 横排 | 38×26 / 26×23 | 12/4/12/4 · 4/12/4/12 | — | — |
| 指示器 横排 / 竖排 | 228×26 / 26×138 | — | — | — |

**使用说明**：设计稿未说明。

---

## 25. Collapse 折叠面板

- 页面：折叠面板 · 节点：[363:65360](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=363-65360) · 2 个变体

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| unfold | VARIANT | on / off | off |
| icon#363:22 | BOOLEAN | true / false | false |
| description#640:14 | TEXT | 展开内容 | "Consistent with real life: in line with the process and logic of real life, and comply with languages and habits that the users are used to; Consistent within interface: all elements should be consistent, such as: design style, icons and texts, position of elements, etc." |

**状态**：收起、展开。

**尺寸与间距**：收起 900×48，内边距 13/8/13/0，下描边 `{color-border-border4}`；展开 900×116。标题 medium/small 13 · `{color-text-text2}`，正文 `{color-text-text3}`。

**使用说明**：设计稿未说明。

---

## 26. Description 描述列表

- 页面：描述列表 · 页面分区：`Component`、`Copy me - light`、`Copy me - dark`
- Description：[503:11237](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=503-11237) · 8 个变体
- Description Item：[483:1111](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=483-1111) · 24 个变体

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Description | border | VARIANT | on / off | off |
| | direction | VARIANT | vertical / horizontal | horizontal |
| | icon | VARIANT | off / on | off |
| | title#503:44 | BOOLEAN | true / false | true |
| Description Item | size | VARIANT | default / large / small | default |
| | type | VARIANT | text / tag | text |
| | border | VARIANT | off / on | off |
| | direction | VARIANT | horizontal / vertical | horizontal |
| | icon#503:10 | BOOLEAN | true / false | false |

**状态**：没有交互状态。

**尺寸与间距**

| 变体 | 尺寸 | 内边距 | 间距 | 文字 |
|---|---|---|---|---|
| Item default | 280×36 | 7/0/7/0 | 16 | regular/base 14 · `{color-text-text2}` |
| Item large / small | 280×40 / 280×32 | 9/0/9/0 · 6/0/6/0 | 16 | regular/base / regular/extra-small |
| Item border=on | 280×40 | 0 | 0 | 标签 medium/base · `{color-text-text3}`，底色 `{color-background-bg4-qipao}`，描边 `{color-border-border4}` |
| Item vertical | 280×66 | 8/0/8/0 | 6 | regular/base |
| Description | 900×448（border 492、vertical 382） | 0 | 20 | 标题 medium/medium 16 · `#000000`（未绑定） |

type=tag 的标签用了 `{color-primary-brand4-qipao}`、`{color-primary-brand5}`、`{color-success-color-success-light-8}`⚠️ / `-light-9`⚠️、`{color-success-safety}`。

**使用说明**：设计稿未说明。

---

## 27. Empty 空状态

- 页面：空状态 · 页面分区：`Component`、`Copy me - light`；另有画框「空状态」[2930:3005](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=2930-3005)（1376×872）和 9 组插画（见 assets/Illustrations）
- Empty：[423:17534](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=423-17534) · 3 个变体

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| type | VARIANT | custom / default / icon | default |
| button#423:18 | BOOLEAN | true / false | false |
| description#423:21 | TEXT | 描述文字 | "A network change was detected." |

**状态**：没有交互状态。

**尺寸与间距**：default / custom 214×242，icon 214×106；纵向间距 20；描述 regular/base 14 · `{color-text-text3}`。

页面原文（画框「空状态」）：「暂无数据」「灵珠/魔丸等待你的召唤」。这一页还引用了**远程库**变量 `{remote-neutral-text-fuzhu1}`（#75797e）、`{remote-neutral-text-neirong}`（#222329 / 暗 #d6d7dd）（本文件的「颜色」集合里没有定义，来自远程集合「同程管家组件库」）和 `{color-background-bg5}`。

**使用说明**：设计稿未说明（除上面的示例文案外没有规则说明）。

---

## 28. Image 图片

- 页面：图片 · 节点：[318:48](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=318-48) · 14 个变体

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| size | VARIANT | 1:1 / 4:3 / 3:2 / 16:10 / 0.618 / 5:3 / 16:9 | 1:1 |
| type | VARIANT | image / icon | icon |

**状态**：只有占位（icon）和已加载（image）两种。

**尺寸与间距**：宽固定 300；高度 1:1=300、4:3=225、3:2=200、16:10=188、0.618=185、5:3=180、16:9=169。占位态内边距 4，填充 `{color-primary-brand5}`，占位图标 `{color-primary-brand2}`。

**使用说明**：设计稿未说明。

---
## 29. Pagination 分页

- 页面：分页 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Pagination-basic：[246:11034](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=246-11034) · 16 个变体
- Pagination-extend：[246:11683](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=246-11683) · 8 个变体
- 子部件：`_pagination_button` 246:10343（48）、`_pagination_number` 246:10555（24）、`_pagination_page` 246:10754（16）、`_pagination_more` 246:10824（12）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Pagination-basic | size | VARIANT | default / small | default |
| | background / more / disabled | VARIANT | off / on | off |
| Pagination-extend | size | VARIANT | default / small | default |
| | background / disabled | VARIANT | on·off / off·on | off / off |
| | count#246:25 / quantity#246:28 / jump#246:31 | BOOLEAN | true / false | true |
| _pagination_button | size / background / type / align / state / disabled | VARIANT | default·small / off·on / more·arrow / right·left / default·hover / off·on | default / off / arrow / left / default / off |
| _pagination_number | size / background / state / checked / disabled | VARIANT | default·small / on·off / Default·default·hover / off·on / off·on | default / off / default / off / off |
| | current page#246:0 | TEXT | — | "1" |
| _pagination_page | size / type / state / disabled | VARIANT | default·small / select·input / default·hover·focus / off·on | default / select / default / off |
| _pagination_more | size / type / disabled | VARIANT | default·small / quantity·count·jump / off·on | default / count / off |

注意：`_pagination_number` 的 state 同时有 `Default` 和 `default` 两个值（设计稿命名重复）。

**状态**：默认、悬停、当前页（checked）、禁用；页码输入：聚焦。

**尺寸与间距**

| 部件 | 尺寸 | 内边距 | 圆角 | 文字 | 填充 / 描边 |
|---|---|---|---|---|---|
| 页码 / 箭头 default | 32×32（宽高 `{size-common-component-size-default}`⚠️） | 箭头 9 | background=on 时 8 `{radius-border-radius-base}`⚠️ | regular/base 14 · `{color-text-text3}`；hover `{color-primary-brand}`；当前页 medium/base · brand | background=on 填充 `{color-background-bg3}` |
| 页码 / 箭头 small | 24×24（Size small⚠️） | 箭头 6 | — | regular/extra-small 12 | — |
| 每页条数选择 | 128×32（small 97×24） | 5/12/5/12（small 2/8/2/8） | 8 | regular/base | `{color-background-fill-color-blank}`⚠️ / `{color-border-border2}`；hover `{color-text-text6}`；focus brand；disabled `{color-background-bg4-qipao}` / `{color-border-border3}` |
| 跳页输入 | 56×32 | 5/12/5/12 | 4 | regular/base | 同上 |
| 总数文字 | 69×32 | 5/0/5/0 | — | regular/base · `{color-text-text3}` | — |
| Pagination-basic | 224×32（small 168×24；background=on 272×32，间距 8） | — | — | — | — |
| Pagination-extend | 667×32（small 525×24；background=on 739×32），间距 16 | — | — | — | — |

**使用说明**：设计稿未说明。

---
## 30. Progress 进度条

- 页面：进度条 · 页面分区：`_parts`、`Component`
- Progress：[313:51027](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=313-51027) · 16 个变体
- 子部件：`_progress%` 310:50420、`_progress_internal%` 311:50720、`_progress_circle%` 313:50777、`_progress_dashboard%` 313:50785（各 7 个变体）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Progress | type | VARIANT | line / line-internal / circle / dashboard | line |
| | status | VARIANT | default / success / warning / exception | default |
| | format#546:0 | BOOLEAN | true / false | true |
| _progress* 子部件 | % | VARIANT | 0 / 10 / 30 / 50 / 70 / 90 / 100 | 0 |

**状态**：default（进度色 `{color-primary-brand}`）、success（`{color-success-safety}`）、warning（`{color-success-warning}`）、exception（`{color-success-danger}`）。

**尺寸与间距**

| 变体 | 尺寸 | 圆角 | 轨道 | 文字 |
|---|---|---|---|---|
| line | 344×22（轨道 500×6，文字间距 4） | 8 `{radius-border-radius-base}`⚠️ | `{color-border-border4}` | regular/base 14 · `{color-text-text3}` |
| line-internal | 500×24 | 999 `{radius-border-radius-circle}`⚠️ | `{color-border-border4}` | 条内 regular/extra-small 12 · white |
| circle / dashboard | 120×120 | — | — | regular/base 14 |

**使用说明**：设计稿未说明。

---

## 31. Result 结果页

- 页面：结果页 · 节点：[421:17339](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=421-17339) · 5 个变体

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| type | VARIANT | custom / info / success / warning / danger | info |
| buttons#421:0 | BOOLEAN | true / false | true |
| secondary button#421:6 | BOOLEAN | true / false | true |
| subtitle#421:12 | BOOLEAN | true / false | true |

**状态**：用 type 区分结果：info / success / warning / danger / custom。

**尺寸与间距**：600×252（custom 600×324），内边距 24/0/24/0，纵向间距 30；标题 medium/extra-large 20 · `{color-text-text2}`，副标题 `{color-text-text3}`。图标颜色：info `{color-info-color-info}`⚠️、success `{color-success-safety}`、warning `{color-success-warning}`、danger `{color-success-danger}`。

**使用说明**：设计稿未说明。

---

## 32. Table 表格

- 页面：表格 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Table Header：[234:10973](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=234-10973) · 36 个变体
- Table Cell-basic：[236:6569](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=236-6569) · 324 个变体
- Table Cell-tree：[237:11896](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=237-11896) · 60 个变体
- 子部件：`_table_sort` 234:10724（3）、`_table_filter` 234:10739（2）、`_table_tree` 237:11707（2）、`_table_actions` 236:6456（5）、`_table_buttons` 236:6281（4）、`_table_tags` 236:6241（8）、`_table_question` 234:10743（独立组件）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Table Header | size | VARIANT | default / large / small | default |
| | type | VARIANT | text / check / radio / blank | check |
| | align | VARIANT | right / left / center | left |
| | background | VARIANT | off / on | off |
| | question-icon#234:0 / sort#234:11 / filter#234:22 | BOOLEAN | true / false | true |
| Table Cell-basic | size | VARIANT | default / large / small | default |
| | type | VARIANT | check / radio / text / icon-left / icon-right / tag / input / select / time / date / button / action / switch | check |
| | state | VARIANT | hover / default | default |
| | background | VARIANT | off / on | off |
| | align | VARIANT | left / center / right | left |
| | Text#237:0 | TEXT | — | "Cell" |
| Table Cell-tree | size / fold / type / background / children / state | VARIANT | default·large·small / on·off / with text·icon / off·on / on·off / hover·default | default / off / icon / off / off / default |
| | Text#237:301 | TEXT | — | "Cell" |
| _table_sort | sort | VARIANT | descend / default / ascend | default |
| _table_filter | Property 1 | VARIANT | arrow-down / arrow-up | arrow-down |
| _table_tree | fold | VARIANT | off / on | off |
| _table_actions | num | VARIANT | 1 / 2 / 3 / 4 / more | 1 |
| _table_buttons | num | VARIANT | 1 / 2 / 3 / 4 | 1 |
| _table_tags | num / size | VARIANT | 1–4 / default·small | 1 / default |

**状态**：单元格：默认、悬停（填充 `{color-background-bg4-qipao}`）、斑马纹（background=on，填充 `{color-background-fill-color-lighter}`⚠️）；排序：升序、降序。

**尺寸与间距**

| 变体 | 高度 | 内边距 | 间距 | 文字 | 填充 / 描边 |
|---|---|---|---|---|---|
| 表头 default（check） | 40 | 13/12/13/12 | 8 | — | `{color-background-fill-color-blank}`⚠️ / 下描边 `{color-border-border4}` |
| 表头 large / small | 48 / 32 | 17/16/17/16 · 10/8/10/8 | 12 / 4 | — | 同上 |
| 表头 text | 40（宽 180） | 9/12/9/12 | 8 | medium/base 14 · `{color-text-text4}` | 同上；background=on `{color-background-bg4-qipao}` |
| 单元格 text | 40（宽 180） | 9/12/9/12 | 8 | regular/base 14 · `{color-text-text3}` | 同上 |
| 单元格 tag / input / select / time / date / button / action / switch | 40 | 8/12/8/12 | 8 | regular/extra-small 12（tag brand；input 类 `{color-text-text5}`；button medium · text3；action medium · brand） | 同上 |
| 单元格 large / small | 48 / 32 | 17/16/17/16 · 10/8/10/8 | 8 | — | — |
| 操作列 | 高 24，间距 16 | — | — | medium/extra-small · `{color-primary-brand}` | — |
| 按钮组 | 高 24，间距 12 | — | — | medium/extra-small · `{color-text-text3}` | — |
| 标签组 | 高 24（small 20），间距 8 | — | — | regular/extra-small · brand | — |

**使用说明**：设计稿未说明。

---

## 33. Tag 标签

- 页面：标签 · 页面分区：`_parts`、`Component`
- Tag：[128:273](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=128-273) · 180 个变体
- Check Tag：[129:1456](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=129-1456) · 2 个变体
- 子部件：`_tag_delete` 123:8978（60）、`_tag_add` 129:7597（4）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Tag | size | VARIANT | small / default / large | small |
| | type | VARIANT | info / success / primary / warning / danger | primary |
| | effect | VARIANT | plain / dark / light | dark |
| | closable | VARIANT | on / off | off |
| | round | VARIANT | off / on | off |
| Check Tag | checked | VARIANT | off / on | off |
| _tag_delete | size / type / effect / state | VARIANT | small·default·large / primary·success·warning·danger·info / light·dark / hover·default | small / primary / light / default |
| _tag_add | state | VARIANT | default / hover / focus / input | default |

**状态**：关闭按钮：默认、悬停；新增标签：默认、悬停、聚焦、输入中；Check Tag：未选、已选。

**尺寸与间距**

| 变体 | 高度 | 内边距 | 间距 | 圆角 | 文字 | 填充 / 描边 |
|---|---|---|---|---|---|---|
| small（默认，dark primary） | 20 | 0/8/0/8 | 4 | 8 `{radius-border-radius-base}`⚠️ | regular/extra-small 12 · white | `{color-primary-brand}` |
| default | 24 | 2/10/2/10 | 6 | 8 | 同上 | 同上 |
| large | 32 | 6/12/6/12 | 8 | 8 | 同上 | 同上 |
| round=on | 20 | 0/8/0/8 | 4 | 999 `{radius-border-radius-circle}`⚠️ | — | — |
| effect=plain | 20 | — | — | 8 | brand | 无填充 / 1px `{color-primary-brand2}` |
| effect=light | 20 | — | — | 8 | brand | `{color-primary-brand5}` / 1px `{color-primary-brand4-qipao}` |
| type=info / success / warning / danger（dark） | 20 | — | — | 8 | white | `{color-info-color-info}`⚠️ / `{color-success-safety}` / `{color-success-warning}` / `{color-success-danger}` |
| Check Tag 未选 / 已选 | 28（宽 108） | 3/16/3/16 | 4 | 8 | bold/base 14 · `{color-info-color-info}`⚠️ / brand | `{color-info-color-info-light-9}`⚠️ / `{color-primary-brand4-qipao}` |
| _tag_add 默认 / hover | 24 | 2/12/2/12 | 4 | 4（未绑定） | medium/extra-small · text3 / brand | `{color-background-fill-color-blank}`⚠️ + `{color-border-border2}` / `{color-primary-brand5}` + `{color-primary-brand3}` |
| _tag_add focus / input | 24 | 6 / 2/6/2/6 | 4 | 8 | regular/extra-small | 描边 brand |

light / plain 效果下各 type 的浅色底和描边用的是旧版 Element 色阶：`color-info-light-3/5/8/9`、`color-success-light-3/5/8/9`、`color-warning-light-3/5/8/9`、`color-error-light-3/5/8/9`（都是孤立变量⚠️）。

**使用说明**：设计稿未说明。

---

## 34. Timeline 时间线

- 页面：时间线 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Timeline：[429:49469](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=429-49469) · 6 个变体
- 子部件：`_timeline_node` 429:48735（3）、`_timeline_item` 429:48846（6）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Timeline | align | VARIANT | top / center | top |
| | type | VARIANT | card / default / time | default |
| _timeline_item | align / type | VARIANT | center·top / card·title·time | top / title |
| _timeline_node | type | VARIANT | border / icon / default | default |

**状态**：没有交互状态。

**尺寸与间距**：节点 24×24（`{size-common-component-size-small}`⚠️），内边距 6（icon 型 4）；条目 149×51，间距 8，标题 regular/base 14 · `{color-text-text2}`，时间 regular/extra-small 12 · `{color-text-text4}`；card 型条目 391×126；Timeline 149×400（card 型 391×735）。页面用到 `{radius-border-radius-round}`⚠️（20）、`{color-background-bg-color-overlay}`⚠️、`{color-success-safety}`。

**使用说明**：设计稿未说明。

---

## 35. Tree 树形控件

- 页面：树形控件 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Tree：[425:28877](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=425-28877) · 6 个变体
- Tree Item：[425:26630](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=425-26630) · 108 个变体
- 子部件：`_tree_arrow` 425:25965（3）、`_tree_list` 425:25995（3）、`_tree_buttons` 425:26419（4）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Tree | type | VARIANT | buttons / default / checkbox | default |
| | dropdown | VARIANT | off / on | off |
| | filter#425:38 | BOOLEAN | true / false | false |
| Tree Item | level | VARIANT | 1 / 2 / 3 / 4 / 5 / 6 | 1 |
| | with fold | VARIANT | off / on | on |
| | unfold | VARIANT | on / off | off |
| | state | VARIANT | default / hover / active | default |
| | dropdown | VARIANT | off / on | off |
| | buttons#425:28 | BOOLEAN | true / false | false |
| _tree_arrow | unfold / placeholder | VARIANT | on·off / off·on | off / off |
| _tree_list | checked / indeterminate | VARIANT | on·off / off·on | off / off |
| | checkable#425:24 | BOOLEAN | true / false | true |
| _tree_buttons | size | VARIANT | 1 / 2 / 3 / 4 | 4 |

**状态**：默认、悬停（`{color-background-bg4-qipao}`）、选中（active，`{color-primary-brand5}`）、展开 / 收起、勾选 / 半选。

**尺寸与间距**：Tree Item 400×26，内边距 1/0/1/0，每级缩进 18（level 2→18，3→36 … 6→90）；dropdown=on 时左右内边距 8；文字 regular/base 14 · `{color-text-text3}`；箭头 24×24，内边距 6；操作按钮组高 24，内边距 0/8/0/8，间距 8，medium/extra-small · brand。Tree 400×442。

**使用说明**：设计稿未说明。

---
## 36. Statistic 统计数值

- 页面：统计数值 · 节点：[516:21708](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=516-21708) · 3 个变体；子部件 `_statistic_countdown_additional` 516:21715（2）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Statistic | type | VARIANT | card / basic / countdown | basic |
| | more#516:0 | BOOLEAN | true / false | false |
| | label icon#516:5 | BOOLEAN | true / false | false |
| | additional#516:9 | BOOLEAN | true / false | true |
| | content icon#516:13 | BOOLEAN | true / false | false |
| _statistic_countdown_additional | type | VARIANT | Button / date | Button |

**状态**：没有交互状态。

**尺寸与间距**：basic 240×76，间距 4，标签 regular/extra-small 12 · `{color-text-text3}`；card 240×128，内边距 20，间距 16，圆角 8 `{radius-border-radius-base}`⚠️，填充 `{color-background-bg-color}`⚠️；countdown 240×92，间距 8。倒计时附加：按钮 70×32（medium/base · white）或日期 90×24（regular/medium 16 · `{color-text-text2}`）。

**使用说明**：设计稿未说明。

---

## 37. Breadcrumbs 面包屑导航

- 页面：面包屑导航 · 节点：[259:17518](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=259-17518) · 6 个变体
- 子部件：`_breadcrumb_item` 259:17474（6）、`_breadcrumb_seperator` 259:17469（2）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Breadcrumbs | seperator | VARIANT | default / icon | default |
| | pages | VARIANT | 4 / 2 / 3 | 2 |
| _breadcrumb_item | state | VARIANT | hover / default | default |
| | seperator | VARIANT | default / icon | default |
| | current page | VARIANT | off / on | off |
| | Text#259:34 | TEXT | — | "Page" |
| | show seperator#260:38 | BOOLEAN | true / false | true |
| _breadcrumb_seperator | type | VARIANT | icon / default | default |

**状态**：默认、悬停、当前页。

**尺寸与间距**：高 22，项间距 8（icon 分隔符 6）；链接 regular/base 14 · `{color-text-text4}`，当前页 medium/base · `{color-text-text2}`；分隔符 "/" 7×14，图标 14×14。Breadcrumbs 宽：2 页 184、3 页 284、4 页 384。

**使用说明**：设计稿未说明。

---

## 38. Navigator 菜单

- 页面：菜单 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Navigator：[303:12289](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=303-12289) · 75 个变体；子部件 `_navigator_group` 303:13509（2）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Navigator | align | VARIANT | vertical / horizontal | vertical |
| | level | VARIANT | 1 / 2 / 3 | 1 |
| | openable | VARIANT | on / off | on |
| | selected | VARIANT | on / off | off |
| | collapse | VARIANT | off / on | off |
| | state | VARIANT | default / hover | default |
| | disabled | VARIANT | on / off | off |
| | with icon#303:0 | BOOLEAN | true / false | true |
| _navigator_group | collapse | VARIANT | off / on | off |

**状态**：默认、悬停（`{color-primary-brand5}`）、选中、禁用（`{color-text-text6}`）、折叠。

**尺寸与间距**：菜单项 200×48（横向 180×48），内边距 13/20/13/20，二级左缩进 40，图文间距 8，填充 `{color-background-fill-color-blank}`⚠️，文字 regular/base 14 · `{color-text-text2}`；折叠态 58×48，内边距 15/20；分组标题 200×32，内边距 5/20/5/40，regular/base · `{color-text-text4}`。

页面示例文字：「Element Plus Template」「Alice」——这一页照搬了 Element Plus 的菜单模板。

**使用说明**：设计稿未说明。

---

## 39. Page Header 页头

- 页面：页头 · 页面分区：`_parts`、`Components`、`Copy me - light`、`Copy me - dark`
- Title：[304:25844](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=304-25844) · 2 个变体
- 子部件：`_pageHeader_content` 304:25761（4）、`_pageHeader_additional_operation` 304:25762（独立组件）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Title | breadcrumbs | VARIANT | off / on | off |
| | additional operation#304:86 | BOOLEAN | true / false | false |
| _pageHeader_content | back / back icon | VARIANT | off / on | on / on |
| | avatar#304:77 / additional#304:80 / tag#304:83 / subtitle#304:89 | BOOLEAN | true / false | true |

**状态**：没有交互状态。

**尺寸与间距**：Title 1160×32（带面包屑 1160×70，间距 16）；内容区 278×32，间距 16；返回文字 medium/base 14 · `{color-text-text3}`，标题 medium/large 18 · `{color-text-text2}`；附加操作 166×32，间距 12。

**使用说明**：设计稿未说明。

---

## 40. Steps 步骤条

- 页面：步骤条 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Steps：[429:48415](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=429-48415) · 12 个变体
- 子部件：`_step_icon` 323:3817（8）、`_step_divider` 323:3832（5）、`_step_line` 330:843（16）、`_step_item` 429:47184（32）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Steps | step level | VARIANT | 1 / 2 / 3 | 1 |
| | type | VARIANT | status / default | default |
| | align | VARIANT | horizontal / vertical | horizontal |
| _step_item | status | VARIANT | have done / on going / to do / error | to do |
| | last step | VARIANT | off / on | off |
| | type / align | VARIANT | status·default / horizontal·vertical | status / horizontal |
| | description#522:17 | BOOLEAN | true / false | true |
| _step_icon | status / type | VARIANT | have done·default·to do·error / default·status | have done / status |
| _step_divider | status | VARIANT | success / default / to do / error / placeholder | success |
| _step_line | align / type / status | VARIANT | horizontal·vertical / default·status / to do·have done·default·error | horizontal / status / have done |

**状态**：已完成、进行中、待办、错误。

**尺寸与间距**

| 部件 | 尺寸 | 圆角 | 填充 / 描边 |
|---|---|---|---|
| 图标 已完成 | 24×24（`{size-common-component-size-small}`⚠️），内边距 5 | 999 `{radius-border-radius-circle}`⚠️ | `{color-success-color-success-light-9}`⚠️ / `{color-success-color-success-light-8}`⚠️ |
| 图标 进行中（default） | 24×24，内边距 1/6 | 999 | `{color-primary-brand}` |
| 图标 待办 | 24×24 | 999 | `{color-info-color-info-light-9}`⚠️ / `{color-info-color-info-light-8}`⚠️ |
| 图标 错误 | 24×24 | 999 | `{color-error-color-error-light-9}`⚠️ / `{color-error-color-error-light-8}`⚠️ |
| 图标 type=default（数字） | 24×24 | 999 | `{color-primary-brand5}` / `{color-primary-brand4-qipao}`，数字 medium/base · brand |
| 分隔线 | 200×1 | — | 完成 `{color-success-safety}` / 进行中 brand / 待办 `{color-border-border3}` / 错误 `{color-success-danger}` |
| 步骤项 | 200×78（竖向 200×68），间距 8 | — | 标题 regular/base 14 · `{color-text-text3}` |
| Steps | 664×98（竖向 200×360），间距 12 | — | — |

**使用说明**：设计稿未说明。

---
## 41. Tabs 标签页

- 页面：标签页 · 页面分区：`_parts`、`Component`、`Copy me - light`、`Copy me - dark`
- Tabs：[287:1136](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=287-1136) · 14 个变体
- 子部件：`_tabs_items` 286:20536（24）、`_tabs_add` 287:436（2）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Tabs | type | VARIANT | default / card / border-card | default |
| | closable | VARIANT | off / on | off |
| | positon（原文拼写） | VARIANT | default / left / right | default |
| | custom-icon | VARIANT | off / on | off |
| | add | VARIANT | off / on | off |
| _tabs_items | type | VARIANT | default / card / border-card | default |
| | tab-on | VARIANT | on / off | off |
| | closable | VARIANT | off / on | off |
| | position | VARIANT | left / default / right | default |
| | state | VARIANT | default / hover | default |
| | custom-icon#286:45 | BOOLEAN | true / false | false |
| _tabs_add | state | VARIANT | hover / default | default |

**状态**：默认、悬停（brand）、选中（tab-on=on，brand）。

**尺寸与间距**：标签项 高 40，左右内边距 20，medium/base 14 · `{color-text-text2}`，选中 / 悬停 `{color-primary-brand}`；Tabs 1000×40（左右竖排 65×400），底线描边 `{color-border-border3}`；card 型描边 `{color-border-border2}`；border-card 型底色 `{color-background-bg4-qipao}`；新增按钮 20×20，内边距 5，圆角 8 `{radius-border-radius-base}`⚠️，描边 `{color-border-border2}`。

**使用说明**：设计稿未说明。

---

## 42. Alert 警告提示

- 页面：警告提示 · 节点：[306:37054](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=306-37054) · 60 个变体；页面另有 3 个「Container」画框（2944:1048 / 1056 / 1064，用量提示示例）

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| type | VARIANT | info / primary / success / warning / error | info |
| close type | VARIANT | icon / text | icon |
| align center | VARIANT | off / on | off |
| description | VARIANT | off / on | off |
| theme | VARIANT | dark / light | light |
| icon#306:99 | BOOLEAN | true / false | true |
| closable#306:105 | BOOLEAN | true / false | true |

**状态**：用 type 区分信息 / 主色 / 成功 / 警告 / 错误；theme=dark 为实色底。

**尺寸与间距**：600×38（description=on 600×64），内边距 8/16/8/16，间距 8，圆角 8 `{radius-border-radius-base}`⚠️；文字 regular/small 13（带描述时标题 medium/small）。

| type（light） | 底色 | 文字 |
|---|---|---|
| info | `{color-info-color-info-light-9}`⚠️ | `{color-info-color-info}`⚠️ |
| primary | `{color-primary-brand5}` | `{color-primary-brand}` |
| success | `{color-success-color-success-light-9}`⚠️ | `{color-success-safety}` |
| warning | `{color-warning-color-warning-light-9}`⚠️ | `{color-success-warning}` |
| error | `{color-error-color-error-light-9}`⚠️ | `{color-success-danger}` |
| theme=dark（info） | `{color-info-color-info}`⚠️ | white |

页面原文（用量提示示例）：「本月用量」「剩余 35%」「剩余 15%」「已耗尽」——这些示例用到了新版语义色 `{color-success-warning-bg}` / `{color-success-warning-text}` / `{color-success-danger-bg}` / `{color-success-danger-text}`。

**使用说明**：设计稿未说明。

---

## 43. Drawer 抽屉

- 页面：抽屉 · 页面分区：`Component`、`_parts`、`Copy me - light`、`Copy me - dark`
- Drawer（独立组件）：[409:1736](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=409-1736)（1120×900）
- 子部件：`_drawer_header` 409:2107（2）、`_drawer_footer` 409:1720（独立组件）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| _drawer_header | type | VARIANT | custom / default | default |
| | placeholder#409:20 | BOOLEAN | true / false | false |

**状态**：没有状态变体。

**尺寸与间距**：Drawer 1120×900，填充 `{color-background-bg-color}`⚠️，遮罩 `{color-mask-080}`；面板宽 520；头部 520×56（custom 62），内边距 20/20/10/20，标题 medium/large 18 · `{color-text-text2}`；底栏 520×62，内边距 10/20/20/20，按钮间距 8。

**使用说明**：设计稿未说明。

---

## 44. Loading 加载

- 页面：加载 · 页面分区：`Component`、`Copy me - light`、`Copy me - dark`
- Loading：[407:19941](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=407-19941) · 3 个变体
- Loading-fullscreen：[407:19954](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=407-19954) · 2 个变体

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Loading | size | VARIANT | default / large / small | small |
| | text#407:0 | BOOLEAN | true / false | true |
| Loading-fullscreen | theme | VARIANT | light / dark | dark |

**状态**：本身就是加载态。

**尺寸与间距**：Loading small 50×40 / default 50×64 / large 56×80，图标与文字间距 4，文字 regular/extra-small 12 · `{color-primary-brand}`；全屏遮罩 800×400，dark `{color-mask-080}`、light `{color-mask-f90}`。

**使用说明**：设计稿未说明。

---

## 45. Message 消息提示（含 Toast）

- 页面：消息提示 · 页面分区：`Component`、`Copy me - light`、`Copy me - dark`
- Message：[306:38640](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=306-38640) · 5 个变体
- Toast（独立组件）：[4070:2439](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=4070-2439)（160×94）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Message | type | VARIANT | info / primary / success / warning / error | info |
| | icon#306:99 | BOOLEAN | true / false | true |
| | closable#306:105 | BOOLEAN | true / false | true |
| | Text#695:1 | TEXT | — | "Here's a message" |

**状态**：用 type 区分类型，没有交互状态。

**尺寸与间距**：Message 201×48，内边距 13/16/13/16，间距 8，圆角 8 `{radius-border-radius-base}`⚠️，描边 1px，文字 regular/base 14。

| type | 底色 / 描边 | 文字 |
|---|---|---|
| info | `{color-overlay-white}` / `{color-info-color-info-light-8}`⚠️ | `{color-info-color-info}`⚠️ |
| primary | `{color-primary-brand5}` / `{color-primary-brand4-qipao}` | brand |
| success | `{color-success-color-success-light-9}`⚠️ / `-light-8`⚠️ | `{color-success-safety}` |
| warning | `{color-warning-color-warning-light-9}`⚠️ / `-light-8`⚠️ | `{color-success-warning}` |
| error | `{color-error-color-error-light-9}`⚠️ / `-light-8`⚠️ | `{color-success-danger}` |

Toast：160×94，内边距 20/0/18/0，间距 12，圆角 14（未绑定变量），填充绑定 `{remote-overlay-toast}`（rgba(31,35,41,0.8784)），文字 regular/extra-small 12 · `{remote-text-on-primary}`（#ffffff）——这两个变量**不在**本文件的「颜色」集合里（来自远程集合「Color」），见 README。

**使用说明**：设计稿未说明。

---

## 46. Message Box 弹框

- 页面：弹框 · 页面分区：`Component`、`_parts`、`Copy me - light`、`Copy me - dark`
- Message Box：[370:221](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=370-221) · 2 个变体
- 独立组件：`message_box_text` 370:184、`message_box_confirm` 370:183、`message_box_prompt` 370:182、`_message_box_header` 369:38667、`_message_box_footer` 369:38666

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Message Box | confirm | VARIANT | off / on | on |
| | content#409:23 | INSTANCE_SWAP | message_box_text / confirm / prompt | （实例） |

**状态**：没有状态变体。

**尺寸与间距**：520×286，圆角 8 `{radius-border-radius-base}`⚠️，填充 `{color-background-bg-color}`⚠️，遮罩 `{color-mask-080}`；头部 476×50，内边距 16/16/8/16，标题 regular/large 18 · `{color-text-text2}`；正文 regular/medium 16 · `{color-text-text3}`；底栏 476×56，内边距 8/16/16/16，按钮间距 8；prompt 型内容 480×64。

**使用说明**：设计稿未说明。

---
## 47. Notification 通知提醒

- 页面：通知提醒 · 节点：[371:13940](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=371-13940) · 5 个变体

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| type | VARIANT | danger / info / primary / success / warning | info |
| icon#371:2 | BOOLEAN | true / false | true |
| close button#371:8 | BOOLEAN | true / false | true |

**状态**：用 type 区分类型（只有图标颜色不同）。

**尺寸与间距**：400×108，内边距 16/24/16/24，间距 12，圆角 8 `{radius-border-radius-base}`⚠️，填充 `{color-background-bg-color}`⚠️，阴影 light/box-shadow-light；标题 bold/medium 16 · `{color-text-text2}`。

**使用说明**：设计稿未说明。

---

## 48. Popconfirm 气泡确认框

- 页面：气泡确认框 · 节点：[306:36550](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=306-36550) · 12 个变体

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| placement | VARIANT | top-start / top / top-end / right-start / right / right-end / bottom-start / bottom / bottom-end / left-start / left / left-end | left-start |
| text | VARIANT | on（只有一个值） | on |

**状态**：没有交互状态（用 12 个方位区分）。

**尺寸与间距**：240×82（上下方位含箭头 240×88），阴影 light/box-shadow-light，正文 regular/base 14 · `{color-text-text3}`。

**使用说明**：设计稿未说明。

---

## 49. Popover 气泡卡片

- 页面：气泡卡片 · 节点：[304:34110](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=304-34110) · 12 个变体
- 可替换内容（独立组件）：`text` 304:34692（200×80）、`table` 304:34690（300×240）、`avatar` 304:34689（260×202）

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| placement | VARIANT | 12 个方位，同 Popconfirm | left-start |
| Instance#568:46 | INSTANCE_SWAP | text / table / avatar | （实例） |

**状态**：没有交互状态。

**尺寸与间距**：200×104（上下方位 200×110），阴影 light/box-shadow-light；text 内容间距 12，regular/medium 16 · `{color-text-text2}`；avatar 内容内边距 8，间距 16。

**使用说明**：设计稿未说明。

---

## 50. Tooltips 文字提示气泡框

- 页面：文字提示气泡框 · 页面分区：`_parts`（这一页用的是 FRAME，不是 SECTION）、`Components`、`Copy me - light`、`Copy me - dark`
- Tooltips：[147:2495](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=147-2495) · 72 个变体
- 子部件：`_arrow_placement` 138:2078（36）、`_arrow_style` 138:1910（3）

| 组件 | 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|---|
| Tooltips | effect | VARIANT | dark / light / custom | dark |
| | placement | VARIANT | 12 个方位 | top-start |
| | multiple | VARIANT | off / on | off |
| _arrow_placement | placement / effect | VARIANT | 12 个方位 / dark·light·border | top-start / dark |
| _arrow_style | effect | VARIANT | border / dark / light | dark |

**状态**：没有交互状态。

**尺寸与间距**：上下方位 129×38，左右方位 135×32，多行 160×58；阴影 light/box-shadow-light；文字 regular/extra-small 12，dark / custom 为 white，light 为 `{color-text-text2}`；箭头 12×6，横向容器 32×6（内边距 0/16），纵向容器 6×32（内边距 8/0）。

**使用说明**：设计稿未说明。

---

## 51. Divider 分割线

- 页面：分割线 · 节点：[522:32508](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=522-32508) · 5 个变体

| 属性 | 类型 | 可选值 | 默认 |
|---|---|---|---|
| type | VARIANT | dashed / basic / custom | basic |
| custom | VARIANT | default / text-left / text-right / icon | default |

**状态**：没有交互状态。

**尺寸与间距**：640×49，上下内边距 24（线本身 1px）。页面示例正文是 Lorem ipsum 占位文字。

**使用说明**：设计稿未说明。

---

## 附：其它页面

- 封面（0:1）：只有一个 1920×1080 的封面画框 [2902:799](https://www.figma.com/design/tl19wuHmHOyNK2C1r7DhQo/?node-id=2902-799)，没有组件。
- 颜色、字体、阴影效果（0:3）：规范页，内容见 tokens.json。
- 三个名字只有一个空格的页面（74:1545、74:1546、565:11312）：都是空页，只用来分组。
