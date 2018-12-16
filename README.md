### 1，目的：规范前端代码
eslint是检验代码的工具，支持

	.eslintrc.json
	.eslintrc.js
等格式，使用.eslintrc.js，因为可以加注释。

### 2，实现方法，以目前最流行的webstrom和vscode为例，其他ide自行研发配置
-	全局安装依赖

```
npm install -g eslint-config-react-app babel-eslint@^7.2.3 eslint@^4.1.1 eslint-plugin-flowtype@^2.34.1 eslint-plugin-import@^2.6.0 eslint-plugin-jsx-a11y@^5.1.1 eslint-plugin-react@^7.1.0
```


-	eslint 配置文件位置
[eslint在git上的文件文件位置](http://git.lagou.com/yun/yun-web-fed/raw/Tom-eslint/.eslintrc.js)
包含了一些基本配置的方法和基本方法

```
/**
 * http://eslint.cn/docs/user-guide/configuring
 * "off" 或 0 - 关闭规则
 * "warn" 或 1 - 开启规则，使用警告级别的错误：warn (不会导致程序退出)
 * "error" 或 2 - 开启规则，使用错误级别的错误：error (当被触发的时候，程序会退出)
 */
```

```
'globals': {
	'jQuery': true,
	'$': true,
},
```
可能每个项目配置最多的，忽略全局变量

[eslint规则搜索地址](https://eslint.org/docs/4.0.0/rules/object-curly-newline)

- vscode配置方法

在商店库安装eslint插件

![图片描述](https://upload-images.jianshu.io/upload_images/7101063-ce012887215e3df1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
在用户配置中，配置eslint

![图片描述](https://upload-images.jianshu.io/upload_images/7101063-f0fe5acf85f30c2d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
附件，关键配置
```
"eslint.run": "onType",
	// 点击按键的时候出发
  	"eslint.autoFixOnSave": true,
	//  开启自动修复功能
	"eslint.options": {
        "configFile": "/Users/pcName/selfConfig/eslint/eslintrc.js"
	 },
	// eslint 全局配置文件位置
```
其他的配置，自行研究，做好这些配置，就可以自动修复不规范的代码了

- webstrom配置eslint方法
下载插件

![图片描述](https://upload-images.jianshu.io/upload_images/7101063-8cbfe9a747509c40.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

依图所示，打开eslint的配置位置
![图片描述](https://upload-images.jianshu.io/upload_images/7101063-29c51b5bc05e33ac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 注解，第7步是配置eslint的文件位置，为自己电脑的eslint的位置。

webstrom不支持自动实时修复功能
需要自己进行实现

1- 使用ide的自动提示修复

![图片描述](https://upload-images.jianshu.io/upload_images/7101063-ba577387cd167ee8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


> 注解：鼠标悬浮在1指示的红色波浪线，左测就会出现红色小灯泡，选择使用eslint修复文件即可


2-自己制作external tool


![图片描述](https://upload-images.jianshu.io/upload_images/7101063-e9934c10dd1dcdf6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![图片描述](https://upload-images.jianshu.io/upload_images/7101063-d52b9b6cf0591f60.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
关键信息


```
eslint
-c /Users/wangjinyang/selfConfig/eslint/eslintrc.js --fix $FilePathRelativeToProjectRoot$
$ProjectFileDir$
```
配置完成，在文件点击右击，就会出现external tool => ESLint Fix

3-使用webstrom 的code style进行格式化

![图片描述](https://upload-images.jianshu.io/upload_images/7101063-b2feb055b37bb0f0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
已经参配置eslint配置好了code style，附件直接导入即可
导入完成后，command + option + l 即可格式化当前文件。

ps：使用webstrom 的code style进行格式化为webstrom最为推荐的方法，速度最快。

