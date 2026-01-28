# 北京轨道地图 Super

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
本项目基于 Web（HTML/CSS/JavaScript）实现北京地铁网络的可视化，目标是提供轻量、易扩展、便于嵌入的地铁地图组件/页面。适合用于展示线路信息、提供换乘建议、导出图片或结合业务数据做高亮标注。

## 主要功能
- 地铁线路与站点完整渲染（支持多条线路）
- 站点搜索与定位（待实现）
- 路线/换乘高亮显示（待实现）
- 鼠标/触摸交互（缩放、平移、点击查看站点详情）
- 夜间模式与多配色主题（待实现）
- 导出当前视图为 PNG/SVG（待实现）
- 支持自定义覆盖物（标注、热力、POI）
- 可配置的站点数据源（JSON、GeoJSON 等）

## 安装与快速开始

克隆仓库：
```bash
git clone https://github.com/XINGHAI183/beijing-subway-map-super
cd beijing-subway-map-super
```

直接用浏览器打开：
```bash
# 打开 beijing-subway-map-super.html
open beijing-subway-map-super.html
```

把构建产物部署到任意静态主机：GitHub Pages、Netlify、Vercel 等。

## 使用示例

在页面中引入（示例）：
```html
<link rel="stylesheet" href="dist/styles.css">
<script src="dist/bundle.js"></script>

<div id="map" style="width:100%;height:600px;"></div>

<script>
  // 全局或模块化 API 示例
  const map = new SubwayMap('#map', {
    theme: 'light',
    center: [116.4074, 39.9042], // 北京经纬度
    zoom: 12,
    dataUrl: '/data/beijing-subway.json'
  });

  map.on('stationClick', (station) => {
    console.log('点击站点：', station);
  });

  // 高亮一条路线
  map.highlightRoute(['四惠', '国贸', '呼家楼', '东单']);
</script>
```

导出视图为图片（示例）：
```js
map.exportPNG().then(blob => {
  // 下载或上传 blob
});
```

## 数据格式说明
项目支持多种数据格式。下面为推荐的简化 JSON 格式示例：

```json
{
  "lines": [
    {
      "id": "1",
      "name": "1号线",
      "color": "#C03A2E",
      "stations": ["古城", "八宝山", "玉泉路", "..."],
      "path": [[116.1902475357,39.9072014648],[116.2358236313,39.9072673042], "..."]
    }
  ],
  "stations": [
    {
      "id": "st-101",
      "name": "古城",
      "lng": 116.1902475357,
      "lat": 39.9072014648,
      "lines": ["1"]
    }
  ]
}
```

也支持 GeoJSON 结构，或从第三方数据源转换后加载。

## 自定义与扩展
- 主题：可以通过配置 theme、CSS 变量或 SCSS 变量改变配色与字体。
- 覆盖物：提供 addMarker、addLayer 接口，支持自定义 DOM/Canvas 渲染。
- 插件机制：可以注册插件（例如实时客流、事件标注），示例：
```js
map.use(MyHeatmapPlugin, { intensityField: 'count' });
```
- 国际化：支持将 UI 文案抽离为语言包，便于切换中/英文。

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
本项目采用 GPL-2.0 许可证，详见 LICENSE 文件。

## 联系方式
仓库维护者: XINGHAI183  
如果发现问题或有功能请求，请打开 Issue 或提交 PR。
