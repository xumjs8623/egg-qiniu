# egg-qiniu-upload

[![NPM version][npm-image]][npm-url]
[![build status][travis-image]][travis-url]
[![Test coverage][codecov-image]][codecov-url]
[![David deps][david-image]][david-url]
[![Known Vulnerabilities][snyk-image]][snyk-url]
[![npm download][download-image]][download-url]

[npm-image]: https://img.shields.io/npm/v/mj-egg-qiniu.svg?style=flat-square
[npm-url]: https://npmjs.org/package/mj-egg-qiniu
[travis-image]: https://img.shields.io/travis/eggjs/mj-egg-qiniu.svg?style=flat-square
[travis-url]: https://travis-ci.org/eggjs/mj-egg-qiniu
[codecov-image]: https://img.shields.io/codecov/c/github/eggjs/mj-egg-qiniu.svg?style=flat-square
[codecov-url]: https://codecov.io/github/eggjs/mj-egg-qiniu?branch=master
[david-image]: https://img.shields.io/david/eggjs/mj-egg-qiniu.svg?style=flat-square
[david-url]: https://david-dm.org/eggjs/mj-egg-qiniu
[snyk-image]: https://snyk.io/test/npm/mj-egg-qiniu/badge.svg?style=flat-square
[snyk-url]: https://snyk.io/test/npm/mj-egg-qiniu
[download-image]: https://img.shields.io/npm/dm/mj-egg-qiniu.svg?style=flat-square
[download-url]: https://npmjs.org/package/mj-egg-qiniu

<!--
Description here.
-->
## 说明
取自egg-qiniu-upload，因无法自定义上传文件名称，所以自己微调以后传了一个
## 依赖说明

### 依赖的 egg 版本

egg-qiniu-upload 版本 | egg 1.x
--- | ---
1.x | 😁
0.x | ❌

### 依赖的插件
<!--

如果有依赖其它插件，请在这里特别说明。如

- security
- multipart

-->

## 开启插件

```js
// config/plugin.js
exports.qiniuUpload = {
  enable: true,
  package: 'egg-qiniu-upload',
};
```
## 例子
```js
// {app_root}/config/config.default.js
exports.qiniu = {
  // I ussually set the key into `~/.zshrc`, and I can get the value via `process.env.key`, It's very safe~
  ak: 'your access key',
  sk: 'your secret key',
  bucket: 'yout bucket',
  baseUrl: 'your base url',
  zone: 'your zone',
  app: true, // default value
  agent: false, //default value
};
```
### 根据文件路径上传
```js
// {app_root}/app/service/file.js
async upload2Qiniu(path,realname) {
  const {app} = this
 
  // do someting what you want to do........
 
  return await app.qiniu.upload(path, realname)
}
/* return a Objet:
{key:'your key',url:'your public url'}
*/
```
### 根据数据流上传
```js
// {app_root}/app/service/file.js
async upload2Qiniu(path,realname) {
  const {app} = this
 
  // do someting what you want to do........
 
  return await app.qiniu.upBuffer(buffer, realname)
}
/* return a Objet:
{key:'your key',url:'your public url'}
*/
```
### 根据key获取信息
```js
// {app_root}/app/servcie/file.js
async info(key) {
  // your should auth the user's passport.
  return await this.app.qiniu.info(key);
}
```

[MIT](LICENSE)
