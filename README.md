# EasyTier Android (aarch64) 自动编译

本仓库通过 GitHub Actions 自动交叉编译 [EasyTier](https://github.com/EasyTier/EasyTier) 的 Android aarch64 静态版本。

## 功能

- ✅ **自动跟踪新版本**：每天 UTC 02:00 自动检查 EasyTier 最新 Release，有新版本则自动编译
- ✅ **手动触发**：支持指定 Tag 手动触发编译（`workflow_dispatch`）
- ✅ **去重跳过**：已编译的版本不会重复构建
- ✅ **静态链接**：产物无需依赖任何系统库，可直接在 Android 上运行
- ✅ **Release 发布**：编译完成后自动发布到本仓库的 Releases

## 使用方式

### 下载预编译版本

前往 [Releases](../../releases) 页面下载最新的 `easytier-core-aarch64-android`。

### 在 Android 上运行（Termux）

```bash
# 下载二进制
wget https://github.com/qzrsa/easytier-android-build/releases/latest/download/easytier-core-aarch64-android

# 赋予执行权限
chmod +x easytier-core-aarch64-android

# 运行
./easytier-core-aarch64-android --help
```

### 通过 ADB 部署

```bash
adb push easytier-core-aarch64-android /data/local/tmp/easytier-core
adb shell chmod +x /data/local/tmp/easytier-core
adb shell /data/local/tmp/easytier-core --help
```

## 手动触发编译

1. 进入 **Actions** → **Build EasyTier for Android (aarch64)**
2. 点击 **Run workflow**
3. 可选填写 Tag（如 `v2.1.0`），留空则自动使用最新版本

## 编译环境

| 项目 | 版本 |
|------|------|
| Rust | stable |
| Android NDK | r26d |
| Target | `aarch64-linux-android` API 21+ |
| Features | `static` |

## 注意事项

- 需要 Android 5.0 (API 21) 或更高版本
- 仅支持 `aarch64`（ARM64）架构，不支持 x86/armv7
- 如需其他架构，可 Fork 本仓库修改 workflow 中的 target
