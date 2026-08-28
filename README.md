# macOS 图标集

本仓库收集了 macOS 系统图标与各应用图标，含 `.icns` 原格式和 256×256 PNG 转换版，用于其他系统的个人美化。

## 目录结构

| 目录 | 数量 | 内容 |
| --- | --- | --- |
| `macOS-Icons/应用图标/` | 185 | 各应用主图标（Info.plist 声明的 CFBundleIconFile）+ App 包内其他特色图标 |
| `macOS-Icons/系统通用图标/` | 255 | CoreTypes.bundle 通用图标（文件夹、磁盘、文档类型等） |
| `macOS-Icons/系统资源图标/` | 698 | Dock、Finder 及系统框架（Frameworks/PrivateFrameworks）资源图标 |
| `macOS-Icons-PNG/` | 1138 | 以上全部图标的 256×256 PNG 版，目录结构一致 |

## 来源

全部图标提取自本机 macOS 系统的以下位置：

- `/System/Library/CoreServices/CoreTypes.bundle/Contents/Resources/*.icns` —— 系统通用图标
- `/Applications/*.app`、`/System/Applications/*.app`（含 `Utilities/` 及嵌套 App）—— 各应用图标，按每个 App 的 `Contents/Info.plist` 中 `CFBundleIconFile` 定位主图标，并收集 `Contents/Resources/` 下其余 `.icns`
- `/System/Library/CoreServices/` 下各 bundle（Dock.app、Finder.app 等）的资源图标
- `/System/Library/Frameworks/*.framework` 与 `/System/Library/PrivateFrameworks/*.framework` 的 `Resources/*.icns`

## 处理方法

1. **收集**：按上述路径复制全部 `.icns`，重名文件自动加序号。
2. **去重**：对所有图标计算 md5，全局去重（1681 → 1138，去除 543 个完全重复文件）。
3. **分类**：按 应用图标 / 系统通用图标 / 系统资源图标 三类归档。
4. **转 PNG**：使用 macOS 自带 `sips` 批量转换：
   ```bash
   sips -s format png -z 256 256 input.icns --out output.png
   ```

## 版权与使用限制

- 系统图标版权归 **Apple Inc.** 所有；第三方应用图标归各自开发商所有。
- 本仓库仅供**个人学习与个人设备美化**使用，禁止商用、禁止公开再分发。
- macOS 软件许可协议不允许将系统资源提取后用于其他操作系统，请自行评估使用风险。
