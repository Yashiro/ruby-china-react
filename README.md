# ruby-china-react
A frontend project for RubyChina use Reactjs

1、初始化

    npm init

2、安装

    npm install webpack webpack-dev-server -g
    npm install webpack css-loader style-loader --save-dev
    npm install babel-core babel-loader --save-dev
    npm install babel-preset-es2015 babel-preset-react --save-dev
    npm install react react-dom react-router --save
    npm install antd --save
    npm install babel-plugin-import --save-dev   // 配个antd或其他，使用方法 https://github.com/ant-design/babel-plugin-import
    npm install html-webpack-plugin --save-dev   // 使用模版
    npm install extract-text-webpack-plugin --save-dev  // css单独打包
    npm install react-blocks --save // Flex块显示
    npm install url-loader --save-dev

3、配置 webpack


配置1

    var path = require("path");
    var webpack = require("webpack");
    module.exports = {
        entry: {
            app: ["./src/main.js"]
        },
        output: {
            path: path.resolve(__dirname, "build"),
            // publicPath: "/assets/",
            filename: "bundle.js"
        },
        module: {
            loaders: [{
                test: /\.css$/,
                loader: 'style!css'
            }]
        }
    };

配置2

    var path = require("path");
    var webpack = require("webpack");
    module.exports = {
        entry: {
            app: ["./src/main.js"]
        },
        output: {
            path: path.resolve(__dirname, "build"),
            // publicPath: "/assets/",
            filename: "bundle.js"
        },
        module: {
            loaders: [{
                test: /\.css$/,
                loader: 'style!css'
            }]
        },
        plugins: [
            new webpack.HotModuleReplacementPlugin()
        ],
        devServer: {
            contentBase: 'build',
            inline: true,
            hot: true
        }
    };


4、运行

    webpack-dev-server --content-base build/ --hot --inline  // 与配置1 对应

    webpack-dev-server  // 与配置2 对应

5、访问

    http://localhost:8080/





========================= Less 使用 ============================

    npm install --save-dev less-loader less

    module: {
        loaders: [{
            test: /\.js$/,
            exclude: /node_modules/,
            loader: 'babel',
            query: {
                presets: ['es2015', 'react']        // babel 配置项中
            }
        },{
            test: /\.css$/,
            loader: 'style!css'
        },{
            test: /\.less$/,
            loader: 'style!css!less'
        }]
    }

