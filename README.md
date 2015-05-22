# npm-dev -- Develop Server for NPM

Run your node.js server and automatically restart if needed.


## Introduction

This project is inspired by gulp-develop-server, but with some important
differences:

	- Zero configuration in most use cases
	- Provide `npm-dev` cli
	- Your node.js process is spawned in separate process group so all child
		processes can be cleanly killed
	- Better APIs (in my opinion :)
	- Written in ES6+

## Usage as a global tool

### Install
```sh
npm install npm-dev --global
```

Just run `npm-dev` under your project directory.

### Local configuration

Edit `.npmdevrc`


## Usage as a local package

### Install
```sh
npm install npm-dev --save-dev
```

### APIs
```js
import {Server} from 'npm-dev'

const serv = new Server()

serv.watch('lib/**/*.js')
```

### Gulp Sample
```js
import {Server} from 'npm-dev'

const serv = new Server()

gulp.task('start', () => {
	serv.start()
})

gulp.task('dev', () => {
	gulp.watch('lib/**/*.js', () => {
		serv.restart()
	})
})
```
