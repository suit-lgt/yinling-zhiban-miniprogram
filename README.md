# 银龄智伴 - 老年人智能助手

银龄智伴是一款专为老年人设计的智能助手应用，基于 uni-app (Vue 2) 开发。

## 项目结构

```
yinling-zhiban/
├── src/
│   ├── api/                    # API接口层
│   ├── common/
│   │   ├── components/        # 公共组件（yl-前缀）
│   │   ├── css/               # 全局样式
│   │   ├── rules/             # 全局规则（防耦合核心）
│   │   └── utils/             # 工具函数
│   ├── pages/                 # 主包页面
│   ├── pagesA/                # 登录注册分包
│   ├── pagesB/                # 使用指南分包
│   └── static/                # 静态资源
├── skills/                    # 开发参考文档
├── package.json
└── README.md
```

## 开发规范

### 全局规则文件 (src/common/rules/)

项目内置了5个全局规则文件，用于确保代码规范和防止功能耦合：

1. **naming.js** - 命名规范
2. **module-interface.js** - 模块接口规范（防耦合核心）
3. **coding-standard.js** - 代码编写标准
4. **accessibility-rules.js** - 适老化设计规则
5. **state-management.js** - 状态管理规范

### 组件命名规范

- 公共组件：`yl-` 前缀（如 yl-button, yl-card）
- 组件文件：kebab-case（如 yl-button.vue）

### 模块解耦机制

所有模块间通信必须通过 EventBus：
```javascript
import { eventBus, EVENTS } from '@/common/rules/module-interface'

// 发送事件
eventBus.publish(EVENTS.MEMO_ADD, { id: 1 })

// 监听事件
eventBus.subscribe(EVENTS.MEMO_ADD, (data) => {
  console.log('备忘录新增:', data)
})
```

## 安装与运行

### 安装依赖

```bash
npm install
```

### 开发模式

```bash
# H5
npm run dev:h5

# 微信小程序
npm run dev:mp-weixin

# Android App
npm run dev:app-android
```

### 构建发布

```bash
# H5
npm run build:h5

# 微信小程序
npm run build:mp-weixin

# Android App
npm run build:app-android
```

## 推荐开发工具

- **VS Code** - 代码编辑器
- **HBuilderX** - uni-app 官方开发工具（推荐用于编译）
- **微信开发者工具** - 微信小程序预览

## 功能模块

| 模块 | 说明 |
|------|------|
| 首页 | 欢迎、天气、AI助手入口、备忘录提醒 |
| 健康 | 血压血糖记录、用药提醒、快捷功能 |
| 问答 | AI智能问答 |
| 备忘录 | 分类备忘录管理 |
| 我的 | 个人中心、设置、反馈 |

## 适老化设计

项目遵循以下适老化设计规范：

- 字体大小 ≥18px
- 按钮最小尺寸 48x48px
- 高对比度颜色方案
- 禁止滑动删除、长按等复杂操作
- 操作步骤最多3步

## 参考文档

- [老年应用开发规范](./skills/老年应用开发规范.md)
- [uni-app模块化开发](./skills/uni-app模块化开发.md)
- [无障碍设计指南](./skills/无障碍设计指南.md)

## License

MIT
