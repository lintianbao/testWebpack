
#babelѧϰ�ʼ�
	babel����
		��ES6���߸��߼��ĵ�js�﷨��׼ת����ES5
		
	babel���� https://www.cnblogs.com/mjian/p/9427687.html
		����babel 7.X
		�Ȱ�װ��ز�� npm install babel-loader @babel/core @babel-preset -D
		����babel�Ĳ�������ַ���
		��һ�֣���webpack������optionsѡ��
		rules:[
            {
                test:/\.js$/,
                use:{
                    loader: 'babel-loader',
                    options:{
                        presets:['@babel/preset-env']
                    }
                }
            }
        ]
		�ڶ��֣�����.babelrc �����ļ������������е�babelת�붼������ȡ�������
		{
		  "presets":[
			"@babel/preset-env"
		  ]
		}
	babel������ز��
		babel-polyfill
		babelĬ��ֻת���µ�JavaScript�﷨��syntax�������ͷ�����ȣ�����ת���µ�API������Iterator��Generator��Set��Maps��Proxy��Reflect��Symbol��Promise��ȫ�ֶ����Լ�һЩ������ȫ�ֶ����ϵķ���������Object.assign��������ת�룻���������Ҫpolyfill��
		��Ϊ����һ�� polyfill ������Ҫ��Դ����֮ǰ���У���������Ҫ������Ϊһ�� dependency������ʱ��������,������һ�� devDependency������ʱ����������
		
		@babel/palugin-transform-runtime -D
		@babel/runtime --save (��������)
	
		