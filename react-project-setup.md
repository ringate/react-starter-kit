#### Step 1: Manual Setup Project
* Create project directory
```sh
mkdir yourproject && cd yourproject
```
* npm package init
```sh
npm init -y
```
* Define node version for this project (if using with nvm, e.g. `node version 12.18.1`)
```sh
echo "12.18.1" > .nvmrc
```
* Prepare control files
```sh
touch .gitignore
touch webpack.config.js
```

#### Step 2: Installing Packages
##### React packages
```sh
npm install react react-dom
```

##### Babel packages
```sh
npm install --save-dev @babel/core @babel/preset-env @babel/preset-react
```

##### Webpack packages
```sh
npm install --save-dev webpack webpack-cli webpack-dev-server babel-loader css-loader style-loader html-webpack-plugin
```

##### Redux packages (if need)
```sh
npm install redux react-redux
```

#### Step 3: Updating Config Files
##### `webpack.config.js` file
```
var path = require('path');
var HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname , 'dist'),
    filename: 'index_bundle.js'
  },
  module : {
    rules : [
      { test: /\.(js)$/, use: 'babel-loader' },
      { test: /\.css$/, use: ['style-loader', 'css-loader'] }
    ]
  },
  mode: 'development',
  devServer: {
    port: 9000
  },
  plugins: [
    new HtmlWebpackPlugin ({
      template: 'src/index.html'
    })
  ]
}
```

##### `package.json` file
* Append babel settings into `package.json` file.
```
  "main": "index.js",
  "babel": {
    "presets": [
      "@babel/preset-env",
      "@babel/preset-react"
    ]
  },
  "scripts": {
    "start": "webpack-dev-server --open",
    "build": "webpack"
  },
```
* Sample file
```
{
  "name": "yourproject",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "babel": {
    "presets": [
      "@babel/preset-env",
      "@babel/preset-react"
    ]
  },
  "scripts": {
    "start": "webpack-dev-server --open",
    "build": "webpack"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "react": "^16.13.1",
    "react-dom": "^16.13.1"
  },
  "devDependencies": {
    "@babel/core": "^7.10.3",
    "@babel/preset-env": "^7.10.3",
    "@babel/preset-react": "^7.10.1",
    "babel-loader": "^8.1.0",
    "css-loader": "^3.6.0",
    "html-webpack-plugin": "^4.3.0",
    "style-loader": "^1.2.1",
    "webpack": "^4.43.0",
    "webpack-cli": "^3.3.12",
    "webpack-dev-server": "^3.11.0"
  }
}
```

##### `.gitignore` file
```
# Logs
logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# Runtime data
pids
*.pid
*.seed
*.pid.lock

# Dependency directories
node_modules/
bower_components/

# Output of 'npm pack'
*.tgz

# Yarn Integrity file
.yarn-integrity

# dotenv environment variables file
.env

# next.js build output
.next

# VS Code configurations
.vscode/

# MacOS
.DS_Store

# Ignore production directory
dist/
```

#### Step 4: Setting Up React App
##### Files and directory setup
```sh
mkdir src && cd src
touch index.html index.js index.css
```

##### `index.html` file
```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>React</title>
  </head>
  <body>
    <div id="app"></div>
  </body>
</html>
```

##### `index.js` file
```
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';

class App extends React.Component {
  render() {
    return (
      <div>Hello World</div>
    )
  }
}

ReactDOM.render(<App />, document.getElementById('app'));
```

#### Step 5: Commands for Run/Build Project
* Run project
```sh
npm run start
```
* Build project. Generate output to `dist` directory.
```sh
npm run build
```

#### References
* https://dev.to/vish448/create-react-project-without-create-react-app-3goh
* https://wing324.github.io/2019/07/27/How-to-set-up-a-React-Project-without-create-react-app/
* https://medium.com/@dan_abramov/you-might-not-need-redux-be46360cf367
