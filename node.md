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
	全局变量引入问题（jquery）
		a.expose-loader 暴露到window全局属性$
		b.providePlugin  给每个文件提供$
		c.引入cdn不打包
		
	图片处理
		a.在js中创建图片来引入(需要用require) 
		b.在css中引入图片background:url('url')
		c.<img src=''>
	配置source-map
		devtool:'source-map'
		大而全，产生单独文件，显示错误行和列
		devtool:'eval-source-map'
		不会产生单独文件，但会显示行和列
		devtool:'cheap-module-eval-source-map'
		不会产生单独文件，但会显示行
		devtool:'cheap-module-source-map'
		产生单独文件，但不会显示行和列，可以保留起来
		
	watch监控实时打包
		watch：true
		watchOptions：{
			poll:1000, //每秒监控次数
			aggregateTimeout:500, //防抖 输入间隔
			ignored：/node_module //排除监控
		}
		
	webpack小插件
		a.clean-webpack-plugin
		作用：每次打包前清除之前的打包文件
		npm install clean-webpack-plugin -D
		new CleanwebpackPlugin('./dist')
		
		b.copy-webpack-plugin
		作用：一般用于拷贝静态文件到打包目录
		npm install copy-webpack-plugin -D
		new CopywebpackPlugin({
		  from: path.resolve(__dirname, './static'),
          to: './static',
          ignore: ['.*']
		})
		
		c.new webpack.BannerPlugin('make by 2020 lintianbao')
		作用：版权声明插件，在每个打包文件的开头显示
		
	webpack处理跨域
		原理：先请求到webServer本地服务，再由本地服务代理出去
		dev-server:{
			proxy:{
				'/api':{
					target:'http://localhost:3000', //配置代理
					pathRewrite:{'/api':'/api'} //重写路径
				}
			}
		}
		
		前端模拟请求mock数据
		dev-server:{
			before(app){ //参数app就是express的实例
				app.get('/api/user',(req.res)=>{
					res.json({name:'zhangsan'})
				})
			}
		}
		
		