
使用 Chrome sidePanel API 在侧边栏嵌入网页,加载 https://edgeservices.bing.com/edgesvc/shell 页面

背景脚本 background.js 中使用 chrome.declarativeNetRequest API 修改请求头,伪装成 Edge 浏览器

content-script.js 中检测当前页面是否是 PDF,如果是则使用 pdf.js 提取文本内容

侧边栏页面可以通过 postMessage 与页面内容脚本通信,获取当前页面数据

监听 Chrome tabs API,向侧边栏页面发送标签页激活和更新事件,提供当前页面标题和 URL

侧边栏页面加载后,主动发送消息展示聊天界面等,提供无缝的用户体验

没有任何用户数据收集,请求直接从浏览器发出,内容不被中间人查看

使用了一些技巧比如修改 User-Agent 伪装成 Edge 浏览器,移除 response header 等

代码组织合理,背景脚本、内容脚本、侧边栏页面脚本分离

打开源码,许可证为 MIT,接受贡献和建议


# Bing Chat sidebar for Chrome

[**Install from Chrome Web Store**](https://chrome.google.com/webstore/detail/bing-sidebar-for-chrome/ncjedehfkpnliaafimjhdjjeggmfmlgf)

AI-powered Bing sidebar ported from Microsoft Edge to Chrome, with the same features like accessing the current webpage or PDF.

![Screenshot](screenshot.png?raw=true)

[Demo video](https://youtu.be/dIZoB1gUbxE)

## How it works

You can learn how I reverse engineered the Edge sidebar in this [Twitter thread](https://threadreaderapp.com/thread/1676175646970740736.html)

## Supported browsers

This extension uses the [chrome.sidePanel](https://developer.chrome.com/docs/extensions/reference/sidePanel/) API, which is only available since Chrome 114. Therefore it only works with Google Chrome, version 114 or higher, and may not be compatible with other Chromium-based browsers, such as Brave, Arc, Opera, etc.

## Privacy

This extension does not collect any user data. Requests are sent directly from your browser to Bing's server using HTTPS. There is no middle server and no one else can see the requests, responses and their content.
