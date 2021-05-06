## Important points for optimising websites using webpack

Today I am jotting down few ways to optimise website loading times using webpack configuration along with few gotchas to keep in mind while writing a webpack confog file. This is work in progress and the article will be updated periodically as I learn more about this topic. Feel free add your own learnings in comments section.

**Order of loaders matters **.     
Loaders are loaded from right to left so last element in array would be loaded first followed by one's added before them.

```
{
   test: /\.css$/,
   use: ["style-loader", "css-loader"]
}
```
CSS loader is loaded before style loader

**In production mode instead, webpack applies few optimisations like**:- 
   - minification with  [TerserWebpackPlugin](https://webpack.js.org/plugins/terser-webpack-plugin/)  to reduce the bundle size.    
This plugin internally uses  [terser](https://github.com/terser/terser)  for code compression since uglify-js does not support es6.
   - scope hoisting with ModuleConcatenationPlugin.     
Tools like Closure Compiler and RollupJS ‘hoist’ or concatenate the scope of all your modules into one closure and allow for your code to have a faster execution time in the browser.
 [ModuleConcatenationPlugin](https://webpack.js.org/plugins/module-concatenation-plugin/)  plugin will enable the same concatenation behavior in webpack

**Code splitting with optimization.splitChunks**.     
With `optimization.splitChunks` we can move out external imports out from the main bundle.

```
module.exports = {
  optimization: {
    splitChunks: { chunks: "all" }
  },
};
``` 

**Code splitting with dynamic imports**.   
With a dynamic import, we can choose when to load our code based on a particular event. This feature is supported in webpack to reduce main bundle size and requesting JS code only when it is required.

**Caching**  
Caching can be used to prevent loading JS bundles in future once they are loaded during first load in browser. The only time JS bundles should be reloaded are when some changes are made in our JS code from developer's end and released on production. For this we can name our file using chunk hashes.  
Whenever a particular file's code changes the chunkhash changes accordingly signaling the browser to reload the code.  
For this we need to set output using chunkhash as shown below:-   

```
output: {
    filename: "[name].[contenthash].js",
    path: path.resolve(__dirname, "dist"),
    clean: true,
 }
``` 
Next we can send code from external node modules into a separate JS file using splitchunks option:-

```
optimization: {
    moduleIds: 'deterministic',
    splitChunks: {
      cacheGroups: {
        vendor: {
          test: /[\\/]node_modules[\\/]/,
          name: "vendors",
          chunks: "all",
        },
      },
    },
    runtimeChunk: "single",
  },
``` 
This will send node modules code in a separate vendors JS file.

**Tree shaking**.      
Tree shaking happens in webpack by default in production mode to reduce bundle size.
Check out official guide here for more information:-
https://webpack.js.org/guides/tree-shaking/

References:-
https://www.valentinog.com/blog/webpack/#code-splitting-with-optimizationsplitchunks

