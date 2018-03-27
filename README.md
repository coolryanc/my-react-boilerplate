# My react boilerplate

1. eject the project
```
yarn eject
```

2. install needed package
```
yarn add sass-loader node-sass
yarn add react-css-modules
```
3. Webpack dev config
```
{
  test: /\.sass$/,
  use: [
    {
      loader: 'style-loader',
      options: { sourceMap: true },
    },
    {
      loader: 'css-loader',
      options: {
        modules: true,
        importLoaders: 1,
        localIdentName: '[name]_[local]__[hash:base64:3]',
        sourceMap: true,
      },
    },
    {
      loader: 'sass-loader',
      options: { sourceMap: true },
    },
    {
      loader: require.resolve('postcss-loader'),
      options: {
        ident: 'postcss',
        plugins: () => [
          require('postcss-flexbugs-fixes'),
          autoprefixer({
            browsers: [
              '>1%',
              'last 4 versions',
              'Firefox ESR',
              'not ie < 9',
            ],
            flexbox: 'no-2009',
          }),
        ],
      },
    },
  ],
},
```
4. Webpack prod config
```
{
  test: /\.sass$/,
  use: ExtractTextPlugin.extract({
  fallback: 'style-loader',
    use: [
      {
        loader: 'css-loader',
        options: {
          modules: true,
          sourceMap: true,
          importLoaders: 2,
          localIdentName: '[name]__[local]___[hash:base64:3]'
        }
      },
    'sass-loader'
    ]
  })
},
```
5. path.js
```
line 44: appBuild: resolveApp('yourFolderName'), // build folder name
```
