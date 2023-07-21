## XX记账本 
### 基于React /React Router /自定义 Hooks / Webpack 实现的极简主义记账应用

### 1.是创建一个React项目

```javascript
  //在终端汇中
  运行 yarn config set registry https://registry.npm.taobao.org/ 设置淘宝源
  create-react-app morney --template typescript（项目名可以自定）
  cd morney 进入项目
  yarn start（会自动打开浏览器）
  不喜欢自动，就运行 echo 'BROWSER=none' > .env 再 yarn start
  我使用的WebStorm，就在 .gitignore 添加 /.idea
```
### 2.CSS-in-JS
<p>在这个项目中，我使用了一种CSS-in-JS中的方案。其中，我想让React支持sass，但是node-sass有两个缺点，下载速度慢且本地编译慢，于是我就想用dart-sass代替node-sass，但是React不支持dart-sass，进过我的研究，我发现了 npm6.9支持一个package alias的功能，使用命令 yarn add node-sass@npm:dart-sass即可偷梁换柱，最终达成在React中使用dart-sass。 </p>

```javascript
在 index.css 添加 @import-normalize; 即可

yarn add --dev node-sass@npm:dart-sass@1.25.0 安装依赖

yarn add react-router-dom

yarn add --dev @types/react-router-dom
```
### 3.React router 之 hash router
<p>在项目中我使用了React router 中的hash router，表现形式是：http://example.com/#/home

 它的优点是：不需要对服务器进行额外配置，可以直接在静态服务器上运行。

缺点是：哈希值不会被发送到服务器，因此在服务器端无法通过哈希值获取到路由信息。</p>

### 5.封装了自定义hooks 

<p>在项目中，我创建了一个名为 useTags 的自定义 Hook。这个 Hook 用于管理标签的数据，包括标签的增删改查等操作。

在 useTags Hook 中，使用了 useState 来声明标签的状态 tags 和更新函数 setTags，并使用 useEffect 来在组件挂载时从 localStorage 中获取已保存的标签数据。

useTags Hook 中提供了一系列函数来实现标签的增删改查功能，包括 findTag、findTagIndex、updateTag、deleteTag 和 addTag。这些函数可以直接在组件中使用，非常方便。
 </p>