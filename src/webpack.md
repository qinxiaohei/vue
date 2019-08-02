 一.webpack是一个模块打包器

二.全局安装webpack,才能使用webpack的命令

 三.全局安装webpack-cli

 四.新建webpack的配置文件，默认是webpack.config.js 

### 五.四个核心概念：


### 1.入口(entry)

entry:String |  Array | Object

前两种是单入口文件,后一种是多个入口文件

entry:{

    key1:value1,//value指的是入口文件
    
    key2:value2
    
}

### 2.出口(output)

默认的出口文件夹dist,编译之后的文件名main.js

output:{

    path:path.join(__dirname,"build"), //编译之后的出口路径,
    
    filename:"编译之后的文件的名字"
    
    （filename:"[name]-[hash].js"）//多入口
}

[hash]为了防止缓存

###  3.加载器(loader)

module:{

    rules:[
    
        {
          test:/\.(js | jsx)$/,  //匹配文件, 需要注意test后边不需要加引号
          
          loader:"babel-loader(加载器)",
          
          options:{
          
             presets:["@babel/preset-env"]
             
          },
          
          use:["style-loader","css-loader"]
          
          //执行顺序是从右到左的
          
        },{
            test:/\.(svg|eot|woff|ttf)$/,
            
            loader:"file-loader",
            
            options:{
            
                name:"./font/[name].[ext]"
                
            }
            
        }
        
    ]
}

###  4.插件(plugins)

- 下载插件
- 引入插件
- 使用插件
- 调用插件

#### 六. 当默认文件不是webpack.config.js时

- #### webpack --config webpack.dev.js

 //当配置文件名不是默认的时候执行

- #### mode:"development" 

//在入口文件前面写

development 开发环境

production 生产环境(线上开发)

- #### pageage.json配置命令

"scripts":{

    "build":webpack --config webpack.dev.js --mode development
    
}

执行命令为: npm run build

#### 七.

##### 1.抽离css

下载==extract-text-webpack-plugin==

下载的时候需要主要的是版本问题

==extract-text-webpack-plugin@next==

##### 2.引用插件

##### 3.使用插件

在module里面

use：
    
    ExtractTextWebpackPlugin.extract({
        
        fallback:"style-loader",//运行结束时加载的loader
        
        use:["css-loader","sass-loader"],//若是抽离单纯的css的话,直接css-loader
    
    })

#### 八.html

1.下载html-webpack-plugin

2.引入

3.调用

    plugins: [
    
        new ExtractTextPlugin("style.css"),
        
        new CleanWebpackPlugin(),
        
        new HtmlWebpackPlugin({
        
            template: "index.html", //模板
            
            filename: "app.html",//构建之后的文件名
            
            title: "首页",
            
            minify: {
            
                removeAttributeQuotes: true, //去除引号
                
                collapseWhitespace: true, //去除空格
                
                removeComments: true, //去除注释
                
                removeEmptyAttributes: true, //去除空属性
                
            }
       ]
       
#### 九.用于删除/清除构建文件夹的webpack插件

1.下载clean-webpack-plugin

2.引用

3.调用
    
    plugins:[
    
        new CleanWebpackPlugin()
        
    ]
    
#### 十.起服务

配置

==webpack-dev-server==（简写为：dev-server）
能够用于快速开发应用程序。

1.下载

==npm i webpack-dev-server -D || npm i webpack-dev-server -g==

2.执行

==webpack-dev-server --config webpack.dev.js==

在package.json中配置scripts：

"scripts": {

        "dev": "webpack-dev-server --config webpack.dev.js"
        
 },
 
需注意webpack-dev-server要和webpack一起使用，即两者要

一起在本地或者全局。

3.参数

devServer: {

        port: 9001,
        
        open: true,
        
        host:"localhost",
        
        inline:true,
        
        before(app){ //与middleware作用相似
        
            app.get('/api/list',(req,res,next) => {
            
                res.send({code:2,msh:"成功"})
                
            })
            
        },
        
        proxy:{//用户代理,相当于proxies
        
            "./classify/iconlist":"http://localhost:3000"
            
        }
        
 }
    



    





