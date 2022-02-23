# Angular踩坑记录

> version Angular12

### Angular12脚手架安装Angular+scss成功后出现错误 
```
// 错误信息
UnhandledPromiseRejectionWarning: TypeError: MessagePort was found in message but not listed in transferList

```
> 出现原因： NodeJS版本 v12至少需要节点12.20。  
> 解决办法：使用nvm切换更新更高等级的Node版本

### 引用框架ng-zorro出现问题
```
Can't bind to 'nzVisible' since it isn't a known property of 'nz-drawer'.
```
> 出现原因：本地的angular/cli脚手架工具版本和项目的版本不一样出现警告，但运行是可以的  
> 解决办法：npm uninstall  @angular/cli --卸载脚手架  --安装一样的版本号