
#babel学习笔记
	babel作用
		将ES6或者更高级的的js语法标准转换成ES5
		
	babel配置 https://www.cnblogs.com/mjian/p/9427687.html
		基于babel 7.X
		先安装相关插件 npm install babel-loader @babel/core @babel-preset -D
		配置babel的插件有两种方法
		第一种：在webpack中配置options选项
		rules:[
            {
                test:/\.js$/,
                use:{
                    loader: 'babel-loader',
                    options:{
                        presets:['@babel/preset-env']，
						plugins:['@babel/palugin-transform-runtim']
                    }
                }
            }
        ]
		第二种：新增.babelrc 配置文件，基本上所有的babel转译都会来读取这个配置
		{
		  "presets":[
			"@babel/preset-env"
		  ]
		}
	babel常用相关插件
		@babel/polyfill --save
		main文件引入
		require ('@babel/polyfill')
		babel默认只转换新的JavaScript语法（syntax），如箭头函数等，而不转换新的API，比如Iterator、Generator、Set、Maps、Proxy、Reflect、Symbol、Promise等全局对象，以及一些定义在全局对象上的方法（比如Object.assign）都不会转码；因此我们需要polyfill；
		因为这是一个 polyfill （它需要在源代码之前运行），我们需要让它成为一个 dependency（上线时的依赖）,而不是一个 devDependency（开发时的依赖）；
		
		之前babel6.x里的stage-2已经包含了各种新的标准预案，现在需要单独引入
		把之前的es2015换成env，stage-x(标准预案)换成各种proposal-xxx
		
		@babel/palugin-transform-runtime -D
		
		@babel/runtime --save (上线依赖)
	
		