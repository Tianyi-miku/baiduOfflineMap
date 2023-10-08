# baiduOfflineMap
百度离线地图

# 在项目中使用

将文件夹复制到项目中

```
  <script type="text/javascript" src="./map/webgl.js"></script>
  <link type="text/css" rel="stylesheet" href="./map/bmap.css">
```

将map中的webgl.js 与 bmap.css 引入项目html

# pvd

瓦片地址放置位置，这里是矢量地图，可以在网上下载所需要的地图，放入其中。


# custom 

mapstyle 地图样式自定义。


# 部署

一般使用nginx代理。将项目中的nginx目录下html文件夹中新建一个baidumap，将map文件夹放进去。

```
 proxy: { 
  "/map": {
        target: `http://weizhi`,
        changeOrigin: true,
        pathRewrite: { '^/map': 'map' },
        ws: false,
      },
    }
```
将map作为关键词，代理到nginx终端。

nginx配置

```
  server {
			listen       3000;   #端口号
			server_name  192.168.1.2;  #服务器地址
			charset utf-8;
			
			location /map {
                root   E:/nginx-1.23.1/html/baidumap;  #这里填map文件夹所在的文件目录
                index  index.html index.htm;
			}
			
		}
```