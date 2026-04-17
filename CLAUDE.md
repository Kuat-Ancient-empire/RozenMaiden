# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

这是一个《 Stellaris 》游戏 mod，添加《蔷薇少女》动漫/漫画系列的角色内容。
- **支持版本：** v4.3.*
- **mod 标签：** Buildings, Events, Leaders, Technologies, Spaceships, Military

## 项目结构

```
RozenMaiden/
├── common/              # 游戏定义脚本（.txt），按类型分子目录
├── events/              # 事件链脚本
├── flags/               # 旗帜图片资源
├── gfx/                  # 图形资源（portraits/models/effects/ships）
├── interface/           # UI/GUI 定义（.gui 和 .gfx）
├── localisation/        # 本地化文件
│   ├── english/         # 英文翻译
│   └── simp_chinese/    # 简体中文翻译
├── sound/               # 音效资源
├── descriptor.mod      # mod 元数据
└── thumbnail.png        # mod 预览图
```

## 核心文件类型

### Paradox 脚本 (.txt)
- `common/` 下按功能分类：ascension_perks、armies、buildings、component_templates、country_types、decisions、edicts、governments、megastructures、relics、ship_sizes、section_templates、situations、solar_system_initializers、technology、traits 等
- `common/scripted_effects/`、`common/scripted_triggers/`、`common/scripted_modifiers/` 存放可复用的脚本逻辑
- `events/` 目录下为事件定义，使用 `country_event`、`ship_event` 等关键字

### 界面文件
- `interface/` 中的 `.gui` 文件定义 UI 布局
- `.gfx` 文件定义图形元素

### 本地化 (.yml)
- 使用 YAML 格式，`l_key` 字段用于索引，`l_english`、`l_simp_chinese` 提供翻译
- 格式示例：`l_english: "TEXT" l_simp_chinese: "文本"`

## 架构特点

### 角色/领袖系统
- 多个《蔷薇少女》角色作为领袖包添加（Suigintou、Shinku、Kirakishou、Hinaichigo 等）
- 定义文件：`common/leader_classes/`、`common/traits/LLK_leader_traits.txt`

### 舰船系统
- 自定义舰船设计在 `common/ship_sizes/` 和 `common/section_templates/`
- 使用 `ship_size` 和 `section_template` 定义舰船类

### 游戏机制
- 自定义觉醒 perks、科技、遗物、决议、巨构
- 使用 `scripted_effect` 和 `scripted_trigger` 实现复用逻辑

## 开发说明

**无构建命令** — 这是纯数据 mod，没有编译过程。Stellaris 直接从脚本和资源文件加载 mod。

**测试方式：** 将 mod 目录软链接到 Stellaris mod 目录（`Paradox Interactive/Stellaris/mod/`），游戏内启用后即可测试。

**常用操作：**
- 增删角色：修改 `common/leader_classes/` 和 `common/traits/`
- 添加事件：在 `events/` 创建新 `.txt`，使用 `country_event` 等关键字
- 添加舰船：在 `common/ship_sizes/` 和 `common/section_templates/` 定义
- 翻译：编辑 `localisation/` 下对应语言的 `.yml` 文件

## 注意事项

- 部分中文 commit 记录显示开发历史，但不影响代码结构
- `.idea/` 目录为 IntelliJ IDEA 配置，无需关注
