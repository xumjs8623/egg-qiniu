# egg-qiniu-upload


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
### 获取token
```js
// {app_root}/app/service/file.js
async upload2Qiniu(path,realname) {
  const {app} = this
 
  // do someting what you want to do........
 
  return await app.qiniu.getToken()
}
/* return a Objet:
{key:'your key',url:'your public url'}
*/
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
