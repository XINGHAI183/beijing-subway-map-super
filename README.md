# 北京轨道地图 Super (BSMS)

> 增强版的北京地铁可视化地图，带有更多交互功能与自定义扩展点，适合展示线路、站点信息、换乘路径及自定义覆盖物。

> 本文由 AI 生成，仓库维护者不对内容的准确性做任何担保。

目录
- 项目简介
- 主要功能
- 安装与快速开始
- 使用示例
- 数据格式说明
- 自定义与扩展
- 贡献指南
- 常见问题
- 许可证

## 项目简介
本项目基于 Web（HTML/CSS/JS）实现北京地铁网络的可视化，目标是提供轻量、易扩展、便于嵌入的地铁地图组件/页面。适合用于展示线路信息、提供换乘建议、导出图片或结合业务数据做高亮标注。

## 主要功能
- 显示北京地铁线路的可视化地图
- 支持用户在地图上点击站点，显示详细信息
- 提供站点之间的路径规划
- 站点搜索与定位
- 线路高亮显示
- 鼠标/触摸交互（地图支持缩放和平移）

## 安装与快速开始

GitHub Pages：https://xinghai183.github.io/BSMS/

克隆仓库：
```bash
git clone https://github.com/XINGHAI183/BSMS
cd beijing-subway-map-super
```

直接用浏览器打开：
```bash
# 打开 beijing-subway-map-super.html
open beijing-subway-map-super.html
```

把构建产物部署到任意静态主机：GitHub Pages、Netlify、Vercel 等。

## 使用示例

本项目页面为单文件集成，推荐直接以浏览器打开 `beijing-subway-map-super.html` 查看效果。如需嵌入到其他页面，可以采用 iframe 的方式：

```html
<iframe src="beijing-subway-map-super.html" width="100%" height="700"></iframe>
```

主要功能包括地图交互、站点信息弹窗、站点搜索、路径规划等，均已集成在页面中。无需额外 JS/模块初始化步骤。

## 数据格式说明

所有线路及站点数据在 HTML 文件中以 JavaScript 变量直接维护，无需请求外部 JSON 文件。核心数据结构如下：

### 站点数据（`allStations`）

```js
const allStations = {
  "古城": { lat: 39.9072, lng: 116.1902 },
  // ... 其它站点
};
```

### 线路与走向（`lineConnections`）

```js
const lineConnections = {
  "1号线": ["古城","八宝山","玉泉路", ...],
  "2号线": [...],
  // 更多线路
};
```

每条线路的数组成员为经停站点名称，顺序代表线路走向。

## 自定义与扩展

1. **自定义线路颜色：**
   编辑 `lineColors` 对象即可调整线路显示色。

   ```js
   const lineColors = {
     "1号线": "#C03A2E",
     "2号线": "#005F98",
     // ... 其它线路颜色
   };
   ```

2. **增删线路或站点：**
   直接补充/修改 `allStations` 和 `lineConnections` 变量内容。

3. **交互与功能扩展：**
   如需增加弹窗内容、修改路径规划规则、样式主题等，可在 HTML 文件对应 JavaScript 部分进行编辑。功能与 UI 全部内嵌于 `beijing-subway-map-super.html`，适合本地或静态服务环境。

4. **更高级集成：**
   如需对接外部数据或实现动态加载，可参考源码结构，在`beijing-subway-map-super.html`基础上扩展相应逻辑。

---

如需进一步自定义开发建议请直接阅读源码或 Discussion 讨论。

## 贡献指南
欢迎贡献！建议流程：
1. Fork 本仓库并创建分支：`feature/xxx` 或 `fix/xxx`
2. 提交代码并打开 PR，附上说明与截图/演示
3. 遵循现有代码风格，添加必要的测试（若适用）

请在 PR 描述中说明变更目的、改动范围以及如何复现或验证。

## 常见问题 (FAQ)
Q: 数据如何与真实线路保持一致？  
A: 项目不会自动同步官方数据，建议使用权威公开数据源或维护专门的 data/ 文件夹并在发布前校验。

Q: 是否支持移动端？  
A: 是的，图层与交互事件针对触摸做了优化，但复杂交互建议在移动端做适配测试。

## 许可证
本项目采用 AGPL-3.0 许可证，详见 LICENSE 文件。

## 联系方式
仓库维护者: XINGHAI183  
如果发现问题或有功能请求，请打开 Issue 或提交 PR。
