Custom Main Menu Reload
================

This is a fork of [lumien231/Custom-Main-Menu](https://github.com/lumien231/Custom-Main-Menu) that adds new features on top of the original mod.

**Minecraft 版本**：1.12.2
**Mod 版本**：3.0.0

## 相比原版新增的功能

### 按钮大小与位置自适应（百分比单位）

原版 `CustomMainMenu` 的按钮 `posX`/`posY`/`width`/`height` 只支持绝对像素值，在不同 GUI 缩放或不同窗口分辨率下，按钮的尺寸与间距无法随屏幕尺寸等比缩放。

`Reload` 版本为按钮新增了 `unit` 字段，允许以百分比（相对屏幕宽/高）方式指定位置与尺寸，使按钮布局可以"自适应"屏幕分辨率。

#### 用法示例

```json
"myButton": {
    "text": "menu.singleplayer",
    "posX": -15,
    "posY": 0,
    "width": 30,
    "height": 8,
    "unit": "percent",
    "alignment": "center",
    "action": { "type": "openGui", "gui": "singleplayer" }
}
```

- `unit`：可选，取值 `"px"`（默认，绝对像素）或 `"percent"`（相对屏幕宽/高的百分比，0–100 表示 0%–100%，可为小数）
- `posXUnit` / `posYUnit` / `widthUnit` / `heightUnit`：可选，逐字段覆盖 `unit`，允许位置用百分比而尺寸用像素（或反之）

详细字段说明请参见 [Wiki - Buttons](https://github.com/54895y/Custom-Main-Menu-Reload/wiki/Buttons#adaptive-sizing--positioning)。

### Bug 修复

- 修复首次进入主菜单时按钮位置/尺寸可能基于陈旧屏幕尺寸的问题（`initGui` 现在会清空按钮列表再重建）
- 修复带纹理按钮在百分比尺寸下渲染比预期小、与点击区域错位的问题

## 构建

本项目依赖 [japng](https://github.com/aellerton/japng) 库（用于 APNG 纹理支持）。GitHub Actions CI 会自动从源码构建 japng 并放入 `libs/` 目录，本地构建需手动执行同样的步骤。

```bash
git clone https://github.com/aellerton/japng.git ../japng
cd ../japng && ./gradlew :api:jar && cd -
mkdir -p libs && cp ../japng/api/build/libs/*.jar libs/
./gradlew build
```

构建产物位于 `build/libs/CustomMainMenuReload-MC1.12.2-3.0.0.jar`。

## Wiki

完整的配置文档位于 [Wiki](https://github.com/54895y/Custom-Main-Menu-Reload/wiki)。

## 致谢

- 原作者 [lumien231](https://github.com/lumien231)
- [japng](https://github.com/aellerton/japng) 库作者
