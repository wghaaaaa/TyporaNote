想要把 IntelliJ IDEA 配置得“十分舒服”，关键在于两点：**视觉上的愉悦**（字体、主题）和 **操作上的顺滑**（全局配置、编码、插件）。

特别是你提到的“**不用每次创建项目都重新配置**”，这是很多新手的痛点。

下面这份 **《IDEA 极致舒适化配置指南》**，请按步骤操作（基于 IDEA 2023/2024 版本，老版本路径大同小异）。

---

### 第一部分：一劳永逸 —— 全局默认配置（最重要！）

**痛点解决**：以前你可能是在当前项目里改设置，关了项目再开一个新的，设置就没了。
**正确姿势**：我们要改“新项目的默认设置”。

1.  关闭当前所有项目，回到 IDEA 的**欢迎启动界面**。
2.  点击左侧的 **Customize** (自定义) -> **All settings...** (所有设置)。
    *   *注意：如果是老版本，路径是 File -> New Projects Setup -> Settings for New Projects。*
3.  **注意：** 接下来的所有“基础配置”步骤，都要在这个窗口里进行，这样以后新建项目就会自动生效！

---

### 第二部分：基础硬核配置（编码与Maven）

在刚才打开的全局设置窗口中操作：

#### 1. 统一编码格式为 UTF-8 (解决乱码的根源)
*   **路径**：`Editor` -> `File Encodings`
*   **操作**：
    *   `Global Encoding`: 选择 **UTF-8**
    *   `Project Encoding`: 选择 **UTF-8**
    *   `Default encoding for properties files`: 选择 **UTF-8**
    *   **关键一步**：勾选后面的 `Transparent native-to-ascii conversion`（这能解决 Properties 配置文件中文变乱码的问题）。

#### 2. 全局 Maven 配置 (接上文)
*   **路径**：`Build, Execution, Deployment` -> `Build Tools` -> `Maven`
*   **操作**：
    *   `Maven home path`: 选你安装的 Maven 路径。
    *   `User settings file`: 勾选 **Override**，选你修改好的 `settings.xml`。
    *   `Local repository`: 勾选 **Override**，选你的 `D:\maven-repo`。
*   **进阶**：点击 Maven 下面的 `Importing`，勾选 `Search for projects recursively`（自动递归搜索），JDK for importer 选你常用的版本（如 1.8 或 17）。

#### 3. 自动导包与优化 (解放双手)
*   **路径**：`Editor` -> `General` -> `Auto Import`
*   **操作**：
    *   勾选 `Add unambiguous imports on the fly` (自动导入明确的包)
    *   勾选 `Optimize imports on the fly` (自动清理无用的包)

#### 4. 忽略大小写提示 (敲代码更顺手)
*   **路径**：`Editor` -> `General` -> `Code Completion`
*   **操作**：取消勾选 `Match case`（或者在旧版本选 None）。
    *   *效果：你输入 `string` 也能提示 `String`，不用按 Shift 切换大小写。*

---

### 第三部分：视觉享受 —— 字体与主题

#### 1. 字体推荐 (程序员的第二张脸)
目前公认最舒服、专门为代码设计的字体是 **JetBrains Mono**（IDEA 自带）。

*   **路径**：`Editor` -> `Font`
*   **推荐设置**：
    *   **Font**: `JetBrains Mono`
    *   **Size**: `14` 或 `15` (13太小费眼，15看着很舒服)
    *   **Line height**: `1.2` 或 `1.3` (行间距大一点，代码不拥挤)
    *   **Enable ligatures**: **勾选** (这个功能很帅，它会把 `!=` 变成 `≠`，把 `>=` 变成 `≥`，看着很高级)。

#### 2. 主题推荐 (护眼与颜值)
IDEA 自带的 `Dark` 或 `New UI` 已经很不错了，但如果你想更极致：

*   **推荐插件主题** (去 Plugins 市场搜)：
    1.  **One Dark Theme** (强烈推荐)：源自 Atom 编辑器，色彩对比度完美，久看不累，是目前最受欢迎的主题之一。
    2.  **Material Theme UI**：颜值极高，颜色鲜艳，但有时会修改 UI 结构，比较“重”。
    3.  **Atom Material Icons**：这是一个**图标插件**，必须装！它会把你的文件夹、文件图标变得非常漂亮且易于识别。

---

### 第四部分：Java 工程师必备插件 (神兵利器)

打开 `Settings` -> `Plugins`，搜索并安装以下插件：

#### 1. 核心开发类
*   **Lombok**: (新版 IDEA 已内置，确认 Enabled 即可) 省去写 Get/Set/ToString 方法。
*   **Maven Helper**: **(必装)** 解决 Maven 依赖冲突的神器。安装后打开 pom 文件，底部会多一个 `Dependency Analyzer` 标签，哪里冲突红点哪里。
*   **MyBatisX**: (如果你用 MyBatis) 也就是小鸟图标插件，能让你在 Mapper 接口和 XML 配置文件之间只有跳转，还能自动生成代码。

#### 2. 代码质量与规范
*   **Alibaba Java Coding Guidelines**: 阿里巴巴代码规范插件。它会像老师一样检查你的代码，不规范的地方会标黄/红，帮你养成大厂编码习惯。
*   **Rainbow Brackets**: **(必装)** 彩虹括号。让你的多层圆括号 `((()))` 显示为不同颜色，一眼就能看出括号匹配关系，防眼瞎。

#### 3. 效率提升工具
*   **Translation**: **(必装)** 翻译插件。选中代码或者报错信息，按快捷键（通常是 Ctrl+Shift+Y）直接翻译，变量名想不出来英文也能用它翻译并替换。
*   **String Manipulation**: 字符串处理神器。驼峰转下划线、下划线转大写、去除空格等，选中文字按 Alt+M 呼出菜单。
*   **Restful Fast Request** (或者 RestfulTool): IDEA 里内置的 Postman。写完 Controller，直接在 IDEA 里就能发请求测试接口，不用切出去。

---

### 第五部分：最后的性能优化 (让 IDEA 不卡顿)

这一步不在设置里，在安装目录里。

1.  点击 IDEA 顶部菜单 `Help` -> `Edit Custom VM Options...`。
2.  这会打开一个文件，这是配置 IDEA 内存分配的。
3.  根据你的电脑内存调整（建议电脑 16G 内存以上的修改）：

```properties
-Xms1024m
-Xmx2048m  <-- 这一项最重要，默认可能只有1024，改成2048或4096(如果你有32G内存)
-XX:ReservedCodeCacheSize=512m
```
*解释：给 IDEA 分配更多的内存，防止项目大时卡顿。*

---

### 总结操作流

1.  **先做全局配置**（Welcome 界面 -> All Settings），搞定 UTF-8 和 Maven。
2.  **设置字体**为 JetBrains Mono (Size 15) + 开启连字。
3.  **安装插件**：`One Dark Theme` (皮肤), `Atom Material Icons` (图标), `Maven Helper`, `Rainbow Brackets`, `Translation`。
4.  **重启 IDEA**。

配置完这些，你的 IDEA 就会变成一把趁手、漂亮、快速的“屠龙刀”了！