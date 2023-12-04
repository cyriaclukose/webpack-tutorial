# Webpack basics
Webpack is a static javascript module bundler. Its also help in transpiling 
the code with help of babel. It help to include assests to the bundle as well
Also provide development derver  which can update the modules and styles on the fly

## Setting up the environment

First we need create a node project by running the following command

npm init -y

This will create a node project with default configuration(-y). you will see that
package.json is created. package.json id contains meta data about project like name,version, dependencies,dev dependencies ,scripts etc.

## Install webpack packages

we can intall the following packeges webpack webpack-cli and
webpack-dev-server

let us run the following command to install the above package as dev dependencies

npm install webpack webpack-cli webpack-dev-server

webpack: module and asset bundler
webpack-cli: command line inteface for webpack

let us create a folder called src and create a file called index.js
## web pack configuration
create a file call webpack.config.js in the root folder of the project to define
the webpack configuration
### Entry
The first thing we need to set is the entry. Entry is the file the webpack will look for compilation. Usually the entry is set as /src/index.js

webpack.config.ja

const path=require('path')

module.exports={

entry:{

main: path.resolve(__dirname,./src/index.js')

}


}

### output

output is where the bundled file will appear. Here we also mention 
the name of the output file.
here the name  has the value main since its defined in the entry

the name of the output file wil be main.bundle.js. And it will be present
in dist folder


module.exports={
--------------

output:{

path: path.resolve(__dirname,"./dist")
file:'[name].bundle.js'
}

}

### scripts

in the package.json under the scripts let us one entry as beloow

package.json

"scripts":{

    "dev": "webpack -mode development"
}


now we can run the webpack in development mode with following command

npm run dev

the following text will appear in the console/terminal

asset main.bundle.js 1.21 KiB [emitted] (name: main)
./src/index.js 29 bytes [built] [code generated]

you can see that dist folder has created with a file main.bundle.js

## Plugins

### html-webpack-plugin

This will let you careate an HTML template that will automatically use the generated script from web apck

npm i -D html-webpack-plugin

we have to import the html-webapack-plugin in the webpack.config.js file

HtmlWebpackPlugin=require('html-webpack-plugin')

now we have to add the plugins in module.expoers as below

module.exports{

    ...................

    plugins:[

         new HtmlWebpackPlugin({
          title: 'webpack Boilerplate',
          template: path.resolve(__dirname, './src/template.html'), // template file
          filename: 'index.html', // output file
        }),
    ]
}

### clean-webpack-plugin 

This can be used for cleaning the build folder . In our case 'dist' folder

npm install clean-webpack-plugin --save-dev

add the followinh entry in webpack.config.js

const {CleanWebpackPlugin} = require('clean-webpack-plugin')


module.exports={


pugins:[

new CleanWebpackplugin()

]

}

