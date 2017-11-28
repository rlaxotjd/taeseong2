const { resolve } = require('path'); 
 const webpack = require('webpack'); 
 
 
 const HOST = 'localhost'; 
 const PORT = 8080; 
 const _PATH = resolve(__dirname, 'src'); 
 
 
 module.exports = { 
     entry: [ 
         `webpack-dev-server/client?http://${HOST}:${PORT}`, 
         './main.js' 
     ], 
     output: { 
         filename: 'bundle.js', 
        path: _PATH, 16         publicPath: '/', 
     }, 
18     context: _PATH, 
19     devtool: 'cheap-module-eval-source-map', 
20     devServer: { 
21         contentBase: _PATH, 
22         publicPath: '/', 
23         compress: true, 
24         port: PORT 
25     }, 
26     module: { 
27         rules: [ 
28             { 
29                 test: /\.jsx?$/, 
30                 exclude: /node_modules/, 
31                 loader: 'babel-loader' 
32             } 
33         ] 
34     }, 
35     resolve: { 
36         modules: [ _PATH, 'node_modules' ], 
37         extensions: [ '.js' ] 
38     }, 
39     plugins: [ 
40         new webpack.NamedModulesPlugin(), 
41         new webpack.EvalSourceMapDevToolPlugin(), 
42         new webpack.NoEmitOnErrorsPlugin() 
43     ] 
44 }; 
