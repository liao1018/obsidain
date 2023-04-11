#cs #web  #node 

---

# intrucduction
> NPM = node package manager.

it was installed with node js automatically.

### start
```
npm init
```
-> to manipulate package.json

### use script to simply development workflow
```json
{
  "name": "42.",
  "version": "1.0.0",
  "description": "",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node app.js",  // npm start, 因為start 是關鍵字，可省略run
    "start-server": "node app.js" // npm run start-server
  },
  "author": "",
  "license": "ISC"
}
```

### install & uninstall third party packages
regular packages:
```
npm install nodemon
npm uninstall nodemon
```
dev dependencies(package using during development):
```
npm install nodemon --save-dev
npm uninstall nodemon --save-dev
```
global packages: 
```
npm install nodemon -g
npm uninstall nodemon -g 
```
-> 使用ios, linux 的時候可能會權限不夠，前面會需要加上 sudo

# 一些 npm 
## [[Axios]]