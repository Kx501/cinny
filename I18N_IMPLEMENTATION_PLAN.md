# Cinny i18n 国际化实施计划

## 📋 项目概述

**目标**: 将Cinny Matrix客户端从英文硬编码转换为完整的国际化支持
**当前状态**: 基础设施完整，核心UI翻译完成，聊天界面翻译进行中
**预期完成时间**: 4-6周

---

## 📊 现状分析

### ✅ 已完成的基础设施

1. **i18n框架配置**
   - ✅ i18next (v23.12.2) 核心框架
   - ✅ react-i18next (v15.0.0) React集成
   - ✅ i18next-browser-languagedetector 语言检测
   - ✅ i18next-http-backend 翻译文件加载
   - ✅ 配置文件: `src/app/i18n.ts`

2. **翻译文件结构**
   - ✅ 支持语言: 英语(en), 中文(zh), 德语(de)
   - ✅ 文件路径: `public/locales/{{lng}}.json`
   - ✅ 默认回退语言: 英语
   - ✅ 语言持久化: localStorage

3. **代码集成**
   - ✅ 在 `src/index.tsx` 中正确导入i18n
   - ✅ 在 `vite.config.js` 中配置静态文件复制

4. **语言选择功能**
   - ✅ 语言选择器集成到设置页面
   - ✅ 语言切换逻辑实现
   - ✅ 语言设置持久化
   - ✅ 语言切换后UI立即更新

### ✅ 已完成的翻译模块

1. **认证模块 (100% 完成)**
   - ✅ 登录页面 (`src/app/pages/auth/login/Login.tsx`)
   - ✅ 密码登录表单 (`src/app/pages/auth/login/PasswordLoginForm.tsx`)
   - ✅ Token登录 (`src/app/pages/auth/login/TokenLogin.tsx`)
   - ✅ 错误消息和提示信息

2. **设置界面 (95% 完成)**
   - ✅ 通用设置 (`src/app/features/settings/general/General.tsx`)
   - ✅ 通知设置 (`src/app/features/settings/notifications/`)
   - ✅ 设备管理 (`src/app/features/settings/devices/`)
   - ✅ 开发者工具 (`src/app/features/settings/developer-tools/`)
   - ✅ 表情包设置 (`src/app/features/settings/emojis-stickers/`)
   - ✅ 账户数据编辑器 (`src/app/components/AccountDataEditor.tsx`)
   - ✅ 设置主页面 (`src/app/features/settings/Settings.tsx`)
   - [ ] 账户设置 (Profile, MatrixId, ContactInfo, IgnoredUserList)
   - [ ] 关于页面

3. **导航组件 (80% 完成)**
   - ✅ 侧边栏导航 (`src/app/pages/client/SidebarNav.tsx`)
   - ✅ 收件箱页面 (`src/app/pages/client/inbox/Inbox.tsx`)
   - ✅ 空间页面 (`src/app/pages/client/space/Space.tsx`)
   - [ ] 房间列表
   - [ ] 搜索功能

### ❌ 当前问题

1. **聊天界面翻译未开始**
   - 房间时间线、消息组件、编辑器等核心功能仍为硬编码

2. **错误处理翻译缺失**
   - 网络错误、认证错误、设备管理错误等

3. **部分设置页面未翻译**
   - 账户设置、关于页面等

---

## 🎯 实施目标

### 阶段目标

- **阶段1**: 核心UI国际化 ✅ 完成
- **阶段2**: 聊天界面国际化 🔄 进行中
- **阶段3**: 错误处理和高级功能 📋 待办
- **阶段4**: 边缘功能和第三方集成 📋 待办

### 最终目标

- 支持多语言切换 ✅
- 完整的翻译覆盖率 (>95%) 🔄 进行中
- 良好的用户体验 ✅
- 可维护的翻译系统 ✅

---

## 📝 详细工作流程

### 阶段1: 基础设施完善 ✅ 完成

#### 1.1 语言选择器实现 ✅

- ✅ 在设置页面添加语言选择组件
- ✅ 实现语言切换逻辑
- ✅ 添加语言设置持久化
- ✅ 测试语言切换功能

#### 1.2 翻译键命名规范设计 ✅

```
格式: {模块}.{组件}.{功能}
示例:
- auth.login.title
- settings.general.language
- room.message.send
- error.network.connection
```

#### 1.3 翻译文件结构优化 ✅

- ✅ 设计模块化的翻译文件结构
- ✅ 创建翻译键模板
- ✅ 设置翻译质量检查工具

### 阶段2: 核心UI组件 ✅ 完成

#### 2.1 认证模块 (登录/注册) ✅

**优先级**: 🔴 高
**文件范围**:

- `src/app/pages/auth/login/`
  - ✅ `Login.tsx` - 主登录页面
  - ✅ `PasswordLoginForm.tsx` - 密码登录表单
  - ✅ `TokenLogin.tsx` - Token登录

**翻译键**:

- `auth.login.title`: "Login"
- `auth.login.username`: "Username"
- `auth.login.password`: "Password"
- `auth.login.loginButton`: "Login"
- `auth.login.forgotPassword`: "Forget Password?"
- `auth.login.noAccount`: "Do not have an account?"
- `auth.login.register`: "Register"
- `auth.login.errors.*`: 各种错误消息

#### 2.2 设置页面 ✅

**优先级**: 🔴 高
**文件范围**:

- `src/app/features/settings/`
  - ✅ `Settings.tsx` - 设置主页面
  - ✅ `general/General.tsx` - 通用设置
  - ✅ `notifications/` - 通知设置
  - ✅ `devices/` - 设备管理
  - ✅ `developer-tools/` - 开发者工具
  - ✅ `emojis-stickers/` - 表情包设置
  - [ ] `account/` - 账户设置
  - [ ] `about/` - 关于页面

**翻译键**:

- `settings.general.*`: 通用设置
- `settings.appearance.*`: 外观设置
- `settings.dateAndTime.*`: 日期时间
- `settings.editor.*`: 编辑器
- `settings.messages.*`: 消息
- `settings.notifications.*`: 通知
- `settings.devices.*`: 设备
- `settings.developerTools.*`: 开发者工具
- `settings.emojisStickers.*`: 表情包

#### 2.3 导航组件 ✅

**优先级**: 🟡 中
**文件范围**:

- `src/app/pages/client/`
  - ✅ `SidebarNav.tsx` - 侧边栏导航
  - ✅ `inbox/Inbox.tsx` - 收件箱
  - ✅ `space/Space.tsx` - 空间页面
  - [ ] 房间列表组件
  - [ ] 搜索功能

**翻译键**:

- `navigation.search`: "Search"
- `navigation.inbox`: "Inbox"
- `navigation.notifications`: "Notifications"
- `navigation.lobby`: "Lobby"
- `navigation.messageSearch`: "Message Search"

### 阶段3: 聊天界面 🔄 进行中

#### 3.1 房间时间线

**优先级**: 🔴 高
**文件范围**:

- `src/app/features/room/`
  - [ ] `RoomTimeline.tsx` - 房间时间线
  - [ ] `Message.tsx` - 消息组件
  - [ ] `MessageEditor.tsx` - 消息编辑器

**翻译键**:

- `room.message.*`: 消息相关
- `room.editor.*`: 编辑器相关
- `room.media.*`: 媒体相关

#### 3.2 消息组件

**优先级**: 🔴 高
**文件范围**:

- `src/app/components/message/`
  - [ ] 消息显示组件
  - [ ] 消息操作组件
  - [ ] 媒体显示组件

#### 3.3 编辑器

**优先级**: 🟡 中
**文件范围**:

- `src/app/components/editor/`
  - [ ] 文本编辑器
  - [ ] 表情选择器
  - [ ] 文件上传

### 阶段4: 错误处理和高级功能 📋 待办

#### 4.1 错误消息翻译

**优先级**: 🔴 高
**文件范围**:

- 所有错误处理组件
- 网络错误
- 认证错误
- 设备管理错误

**翻译键**:

- `error.network.*`: 网络错误
- `error.auth.*`: 认证错误
- `error.device.*`: 设备错误

#### 4.2 设备管理翻译

**优先级**: 🟡 中
**文件范围**:

- 设备验证
- 设备列表
- 设备操作

#### 4.3 空间管理翻译

**优先级**: 🟡 中
**文件范围**:

- 空间列表
- 空间设置
- 空间操作

### 阶段5: 优化完善 📋 待办

#### 5.1 第三方集成翻译

**优先级**: 🟢 低
**文件范围**:

- 第三方服务集成
- 外部链接
- 帮助文档

#### 5.2 性能优化

**优先级**: 🟢 低
**文件范围**:

- 翻译文件懒加载
- 翻译缓存优化
- 内存使用优化

#### 5.3 完整测试

**优先级**: 🔴 高
**文件范围**:

- 单元测试
- 集成测试
- 端到端测试

---

## 🛠️ 技术实现细节

### 翻译键命名规范

```
{模块}.{组件}.{功能}
示例:
- auth.login.title
- settings.general.language
- room.message.send
- error.network.connection
```

### 翻译文件结构

```json
{
  "auth": {
    "login": {
      "title": "Login",
      "username": "Username",
      "password": "Password"
    }
  },
  "settings": {
    "general": {
      "title": "General",
      "language": "Language"
    }
  },
  "common": {
    "save": "Save",
    "cancel": "Cancel",
    "edit": "Edit"
  }
}
```

### 组件集成示例

```typescript
import { useTranslation } from 'react-i18next';

function MyComponent() {
  const { t } = useTranslation();
  
  return (
    <div>
      <h1>{t('auth.login.title')}</h1>
      <button>{t('common.save')}</button>
    </div>
  );
}
```

### 语言切换实现

```typescript
// 语言选择器组件
const handleLanguageChange = (language: string) => {
  i18n.changeLanguage(language);
  localStorage.setItem('cinny-language', language);
};
```

---

## 📊 进度统计

### 翻译覆盖率

- **总文件数**: 736个
- **已翻译文件**: 25+个
- **翻译覆盖率**: 约15%

### 翻译键统计

- **当前翻译键**: 350+个
- **目标翻译键**: 500-1000个
- **完成度**: 35%

### 支持语言

- ✅ 英语 (en)
- ✅ 中文 (zh)
- ✅ 德语 (de)
- [ ] 其他语言 (待定)

---

## 🎯 里程碑

### 里程碑1: 基础设施完成 ✅

- **完成标准**: 语言选择器可用，翻译键规范确定
- **状态**: ✅ 完成

### 里程碑2: 核心UI完成 ✅

- **完成标准**: 登录、设置、导航完全翻译
- **状态**: ✅ 完成

### 里程碑3: 聊天界面完成 🔄

- **完成标准**: 房间列表、消息、编辑器翻译完成
- **状态**: 🔄 进行中

### 里程碑4: 完整翻译 📋

- **完成标准**: 95%以上UI文本翻译完成
- **状态**: 📋 待办

### 里程碑5: 测试完善 📋

- **完成标准**: 所有功能测试通过，无翻译错误
- **状态**: 📋 待办

---

## 📝 最近更新

### 2024年12月 - 主要进展

1. **完成设置界面翻译** (95%)
   - 通用设置、通知、设备、开发者工具、表情包
   - 语言选择器功能完善
   - 翻译键清理和优化

2. **完成认证模块翻译** (100%)
   - 登录页面、密码表单、Token登录
   - 错误消息和提示信息

3. **完成导航组件翻译** (80%)
   - 侧边栏、收件箱、空间页面

4. **技术改进**
   - 修复语言切换问题
   - 清理重复翻译键
   - 优化翻译文件结构

### 下一步计划

1. **完成设置界面剩余部分**
   - 账户设置翻译
   - 关于页面翻译

2. **开始聊天界面翻译**
   - 房间时间线
   - 消息组件
   - 编辑器

3. **错误处理翻译**
   - 网络错误
   - 认证错误
   - 设备管理错误

---

**最后更新**: 2025年8月
**下次更新**: 待定
