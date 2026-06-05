# Version Control Manager Skill

> 项目版本控制与管理技能 - 提供完整的版本创建、回滚、变更记录功能  
> Project Version Control & Management Skill - Complete version creation, rollback, and change tracking functionality

---

## 📋 技能概述 / Project Overview

### 功能描述 / Feature Description

`version-control-manager` 是一个强大的项目版本控制与管理技能，旨在帮助开发者高效管理项目的多个版本，支持版本创建、回滚、变更追踪等核心功能。

`version-control-manager` is a powerful project version control and management skill designed to help developers efficiently manage multiple versions of their projects, supporting core functions such as version creation, rollback, and change tracking.

### 核心特性 / Core Features

| 特性 / Feature | 说明 / Description |
|---------------|-------------------|
| **版本创建 / Version Creation** | 支持语义化版本号，自动生成唯一标识符 |
| **版本回滚 / Version Rollback** | 安全回滚到历史版本，自动创建回滚前快照 |
| **强制版本说明 / Mandatory Version Notes** | 必须填写功能说明、改进点、兼容性等信息 |
| **变更记录 / Change Log** | 完整记录版本间修改内容与时间戳 |
| **自动版本创建 / Auto Version Creation** | 检测构建/提交/CI完成事件，经用户确认后自动创建 |

### 应用场景 / Use Cases

- **项目发布管理 / Project Release Management**: 在每次发布前创建版本快照
- **开发回溯 / Development Rollback**: 快速回滚到稳定版本
- **团队协作 / Team Collaboration**: 追踪团队成员的代码变更
- **CI/CD集成 / CI/CD Integration**: 构建成功后自动创建版本

---

## 🛠️ 环境要求 / Environment Requirements

### 系统要求 / System Requirements

| 项目 / Item | 要求 / Requirement |
|------------|-------------------|
| 操作系统 / OS | Windows 10+/Linux/macOS |
| Python | 3.8+ |
| Node.js | 16+（可选 / Optional） |

### 依赖工具 / Dependencies

- `Write`: 文件写入操作 / File write operations
- `Read`: 文件读取操作 / File read operations  
- `Glob`: 文件路径匹配 / File path matching
- `RunCommand`: 命令执行 / Command execution

---

## 📦 安装与配置 / Installation & Configuration

### 安装步骤 / Installation Steps

1. **克隆仓库 / Clone Repository**
```bash
git clone https://github.com/jeanmycn/skills.git
cd skills/version-control-manager
```

2. **配置环境 / Configure Environment**
```bash
# 确保 Python 3.8+ 已安装 / Ensure Python 3.8+ is installed
python --version
```

### 目录结构 / Directory Structure

```
version-control-manager/
├── SKILL.md              # 技能定义文件 / Skill definition file
├── README.md             # 项目说明文档 / Project documentation
└── evals/                # 测试用例目录 / Test cases directory
    └── evals.json        # 测试用例配置 / Test case configuration
```

---

## 🚀 使用方法 / Usage

### 命令接口 / Command Interface

#### 1. 创建新版本 / Create New Version

```bash
vc create <版本号> [选项]
vc create <version> [options]
```

**参数说明 / Parameters**:

| 参数 / Parameter | 缩写 / Short | 类型 / Type | 必填 / Required | 说明 / Description |
|-----------------|-------------|-------------|----------------|-------------------|
| `<版本号>` | - | string | ✓ | 语义化版本号，如 `v1.0.0` |
| `<version>` | - | string | ✓ | Semantic version, e.g., `v1.0.0` |
| `--name` | `-n` | string | | 版本名称 / Version name |
| `--description` | `-d` | string | | 版本描述 / Version description |
| `--features` | `-f` | string | ✓ | 新增功能，逗号分隔 / New features, comma-separated |
| `--improvements` | `-i` | string | | 改进点，逗号分隔 / Improvements, comma-separated |
| `--known-issues` | `-k` | string | | 已知问题，逗号分隔 / Known issues, comma-separated |
| `--compatibility` | `-c` | string | ✓ | 兼容性信息 / Compatibility information |

**示例 / Example**:
```bash
vc create v1.0.0 -n "初始版本" -f "用户登录,数据导入" -i "性能优化" -k "移动端适配待完善" -c "Python 3.8+"
vc create v1.0.0 -n "Initial Release" -f "User login,Data import" -i "Performance optimization" -k "Mobile adaptation pending" -c "Python 3.8+"
```

#### 2. 查看版本列表 / List Versions

```bash
vc list [选项]
vc list [options]
```

**参数说明 / Parameters**:

| 参数 / Parameter | 缩写 / Short | 说明 / Description |
|-----------------|-------------|-------------------|
| `--all` | `-a` | 显示所有版本 / Show all versions |
| `--limit <数量>` | `-l` | 限制显示数量（默认10） / Limit display count (default 10) |

**示例 / Example**:
```bash
vc list
vc list -a
vc list -l 5
```

#### 3. 查看版本详情 / Show Version Details

```bash
vc show <版本号>
vc show <version>
```

**示例 / Example**:
```bash
vc show v1.0.0
```

#### 4. 版本回滚 / Rollback Version

```bash
vc rollback <版本号>
vc rollback <version>
```

> **注意 / Note**: 回滚前会自动创建当前状态的版本快照 / Auto-creates snapshot before rollback

**示例 / Example**:
```bash
vc rollback v0.9.0
```

#### 5. 删除版本 / Delete Version

```bash
vc delete <版本号>
vc delete <version>
```

> **注意 / Note**: 不能删除当前活跃版本 / Cannot delete active version

**示例 / Example**:
```bash
vc delete v0.8.0
```

#### 6. 查看变更记录 / View Change Log

```bash
vc changelog [选项]
vc changelog [options]
```

**参数说明 / Parameters**:

| 参数 / Parameter | 缩写 / Short | 说明 / Description |
|-----------------|-------------|-------------------|
| `--from <版本号>` | `-f` | 起始版本 / Start version |
| `--to <版本号>` | `-t` | 结束版本 / End version |

**示例 / Example**:
```bash
vc changelog
vc changelog -f v1.0.0 -t v2.0.0
```

#### 7. 自动版本创建配置 / Auto Version Configuration

```bash
vc auto [enable|disable|status]
```

**示例 / Example**:
```bash
vc auto enable    # 启用自动版本创建 / Enable auto version creation
vc auto disable   # 禁用自动版本创建 / Disable auto version creation
vc auto status    # 查看状态 / Check status
```

---

## 📝 实际操作示例 / Practical Examples

### 示例1：创建初始版本 / Example 1: Create Initial Version

```bash
# 创建版本 v1.0.0
vc create v1.0.0 \
  -n "MVP版本" \
  -f "用户注册功能,产品列表展示,订单管理系统" \
  -i "数据库查询优化20%" \
  -k "暂无已知问题" \
  -c "兼容Node.js 16+, MongoDB 4.0+"
```

**输出 / Output**:
```
✅ 版本创建成功！
版本号: v1.0.0
版本ID: VER-a1b2c3d4-202401151030
创建时间: 2024-01-15 10:30:00

✅ Version created successfully!
Version: v1.0.0
Version ID: VER-a1b2c3d4-202401151030
Created: 2024-01-15 10:30:00
```

### 示例2：查看版本列表 / Example 2: List Versions

```bash
vc list
```

**输出 / Output**:
```
┌─────────┬──────────────────────┬─────────────────────┐
│ 版本号  │ 版本名称             │ 创建时间            │
├─────────┼──────────────────────┼─────────────────────┤
│ v1.0.0  │ MVP版本              │ 2024-01-15 10:30   │
│ v0.9.0  │ Beta版本             │ 2024-01-10 14:20   │
│ v0.8.0  │ Alpha版本            │ 2024-01-05 09:15   │
└─────────┴──────────────────────┴─────────────────────┘

┌─────────┬──────────────────────┬─────────────────────┐
│ Version │ Version Name         │ Created             │
├─────────┼──────────────────────┼─────────────────────┤
│ v1.0.0  │ MVP Release          │ 2024-01-15 10:30   │
│ v0.9.0  │ Beta Release         │ 2024-01-10 14:20   │
│ v0.8.0  │ Alpha Release        │ 2024-01-05 09:15   │
└─────────┴──────────────────────┴─────────────────────┘
```

### 示例3：版本回滚 / Example 3: Rollback Version

```bash
vc rollback v0.9.0
```

**输出 / Output**:
```
⚠️  警告：即将回滚到版本 v0.9.0
✅ 已自动创建当前状态快照: v1.0.0-backup
✅ 成功回滚到版本 v0.9.0

⚠️  Warning: Rolling back to version v0.9.0
✅ Auto-created snapshot: v1.0.0-backup
✅ Successfully rolled back to v0.9.0
```

### 示例4：查看变更记录 / Example 4: View Change Log

```bash
vc changelog -f v0.9.0 -t v1.0.0
```

**输出 / Output**:
```
变更记录: v0.9.0 → v1.0.0
┌────────────┬─────────────────────────────────┐
│ 类型       │ 内容                           │
├────────────┼─────────────────────────────────┤
│ 新增功能   │ 用户注册功能                   │
│ 新增功能   │ 产品列表展示                   │
│ 新增功能   │ 订单管理系统                   │
│ 改进       │ 数据库查询优化20%              │
│ 已知问题   │ 暂无                          │
└────────────┴─────────────────────────────────┘

Change Log: v0.9.0 → v1.0.0
┌────────────┬─────────────────────────────────┐
│ Type       │ Description                    │
├────────────┼─────────────────────────────────┤
│ Feature    │ User registration              │
│ Feature    │ Product list display           │
│ Feature    │ Order management system       │
│ Improvement│ Database query optimization   │
│ Known Issue│ None                          │
└────────────┴─────────────────────────────────┘
```

---

## 🔧 故障排除 / Troubleshooting

### 常见错误及解决方法 / Common Errors & Solutions

| 错误代码 / Error Code | 错误信息 / Error Message | 原因 / Cause | 解决方法 / Solution |
|----------------------|-------------------------|-------------|-------------------|
| VC001 | 版本号格式无效 / Invalid version format | 版本号不符合语义化规范 | 检查版本号格式，如 `v1.0.0` |
| VC002 | 版本已存在 / Version exists | 相同版本号已存在 | 使用其他版本号 / Use another version |
| VC003 | 版本不存在 / Version not found | 指定的版本号不存在 | 确认版本号正确 / Verify version number |
| VC004 | 无法回滚到当前版本 / Cannot rollback to current version | 尝试回滚到当前版本 | 选择其他版本 / Select another version |
| VC005 | 缺少必填字段 / Missing required fields | 未提供必需的版本信息 | 补充 `--features` 和 `--compatibility` |
| VC006 | 权限不足 / Insufficient permissions | 无权限执行操作 | 联系管理员 / Contact administrator |

### 日志查看 / Log Inspection

```bash
# 查看变更日志文件 / View change log file
cat .version-control/changelog.json
```

---

## 📊 版本历史 / Version History

| 版本 / Version | 日期 / Date | 更新内容 / Changes |
|---------------|------------|-------------------|
| v1.0.0 | 2024-01-15 | 初始版本发布 / Initial release |
| v1.1.0 | 2024-02-01 | 新增自动版本创建功能 / Added auto version creation |
| v1.1.1 | 2024-02-10 | 修复版本回滚bug / Fixed rollback bug |
| v1.2.0 | 2024-03-01 | 新增CI/CD集成支持 / Added CI/CD integration |

---

## 🤝 贡献指南 / Contributing

### 如何贡献 / How to Contribute

1. **Fork 仓库 / Fork Repository**
```bash
git fork https://github.com/jeanmycn/skills.git
```

2. **创建功能分支 / Create Feature Branch**
```bash
git checkout -b feature/your-feature
```

3. **提交代码 / Commit Changes**
```bash
git add .
git commit -m "feat: 添加新功能"
git commit -m "feat: Add new feature"
```

4. **推送分支 / Push Branch**
```bash
git push origin feature/your-feature
```

5. **创建 Pull Request / Create Pull Request**

### 代码规范 / Code Standards

- 使用 Python 3.8+ 语法 / Use Python 3.8+ syntax
- 遵循 PEP 8 代码风格 / Follow PEP 8 style guide
- 提交信息格式 / Commit message format: `type: description`
  - `feat`: 新增功能 / New feature
  - `fix`: 修复bug / Bug fix
  - `docs`: 文档更新 / Documentation update
  - `refactor`: 代码重构 / Code refactor

---

## 📄 许可证 / License

MIT License - 详见 LICENSE 文件  
MIT License - See LICENSE file for details

---

## 📞 联系方式 / Contact

如有问题或建议，请通过以下方式联系 / For questions or suggestions, please contact:

- GitHub Issues: [提交问题](https://github.com/jeanmycn/skills/issues)
- GitHub Issues: [Submit Issue](https://github.com/jeanmycn/skills/issues)
- 邮箱 / Email: jeanmycn@example.com

---

**最后更新 / Last Updated**: 2024年1月15日 / January 15, 2024