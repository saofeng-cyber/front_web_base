# 视图容器

> [!note]
只记录部分组件内容的使用及其注意点,如果想看全部的请到 [uniapp官网](https://uniapp.dcloud.net.cn/)

## scroll-view组件

- 可滚动视图区域。用于区域滚动。
- 需注意在webview渲染的页面中，区域滚动的性能不及页面滚动。

?> 使用竖向滚动时，需要给 `<scroll-view>` 一个固定高度，通过 css 设置 height；使用横向滚动时，需要给`<scroll-view>`添加`white-space: nowrap;`样式。

>[!tip]
Tips 注意事项

- APP-vue和小程序中，请勿在 scroll-view 中使用 map、video 等原生组件。小程序中 scroll-view 中也不要使用 canvas、textarea 原生组件。更新：微信基础库2.4.4起支持了原生组件在 scroll-view、swiper、movable-view 中的使用。app-nvue无此限制。
- APP-vue和小程序中，请勿在 scroll-view 中使用 map、video 等原生组件。小程序中 scroll-view 中也不要使用 canvas、textarea 原生组件。更新：微信基础库2.4.4起支持了原生组件在 scroll-view、swiper、movable-view 中的使用。app-nvue无此限制。
- scroll-into-view 的优先级高于 scroll-top。
- scroll-view是区域滚动，不会触发页面滚动，无法触发pages.json配置的下拉刷新、页面触底onReachBottomDistance、titleNView的transparent透明渐变。
- 若要使用下拉刷新，建议使用页面的滚动，而不是 scroll-view 。插件市场有前端模拟的基于scroll-view的下拉刷新，但性能不佳。如必需使用前端下拉刷新，推荐使用基于wxs的下拉刷新，性能会比基于js监听方式更高。
- 如果遇到scroll-top、scroll-left、refresher-triggered属性设置不生效的问题参考：[组件属性设置不生效解决办法](https://uniapp.dcloud.net.cn/tutorial/vue-api.html#componentsolutions)
- scroll-view的滚动条设置，可通过css的-webkit-scrollbar自定义，包括隐藏滚动条。（app-nvue无此css）
