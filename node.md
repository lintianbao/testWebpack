webpack4笔记
安装
 需要安装webpack webpack-cli
 npm install webpack webpackcli -D
0配置打包
 没有配置文件时，运行webpack命令行，默认打包src/index.js
 输出为dist/main.js

配置文件打包
    webpack.config.js
    运行webpack命令默认调用webpack.config.js文件

    自定义打包文件名执行命令： webpack --config 自定义文件名
    命令行参数过多
        可以到package.json文件的script定义命令行

webpack-dev-server
    实际上是一个本地起一个node express服务
    打包的文件不会显示在文件上，而是存在缓存中

HTML文件处理
    插件 npm install html-webpack-plugin -D
    new htmlWebpackPlugin({
            tempalte:path.resolve('./src/index.html'),
            filename:'index.html',
            minify:{
                removeAttributeQuotes:true,//刪除html双引号
                collapseWhitespace:true//压缩成一行
            },
            hash:true,//js引用加hash戳
        })
