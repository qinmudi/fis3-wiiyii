## fis3-wiiyii

基于 FIS3 的针对yii框架和smarty模板的前端工程解决方案

### 文档

- 构建工具文档参见 https://github.com/fex-team/fis3

### 使用方法

**产生原因**
>1、历史框架原因不能将模板部署到同一个template下。  
>2、替换yii本身的layout，这种成本最小。  

**安装**

```
npm install -g fis3
npm install -g fis3-wiiyii
```

**fis-conf配置**
```
fis.require('wiiyii')(fis);
fis.set('namespace', ' 模块名称');
```

**远程部署**
RECEIVER 为服务接收地址  
DEPLOY_PATH 为项目部署路径  
media 会开启默认yii模块化部署  
```
fis.media('remote').match('**', {
    deploy: fis.plugin('http-push', {
        receiver: RECEIVER,
        to: DEPLOY_PATH
    })
});
```

**部署逻辑**
>1、静态资源会自动部署到项目根目录/fe/static/模块名  
>2、layout和widget会部署到项目/protected/views/模块名/{layout,widget}  
>3、其它模块类模板会部署到对应模块，如：page/admin/act/index.tpl，会部署到protected/modules/views/act/index.tpl  
>ps:注意模板路径要和 yii 后端模块路径一致  