
# Go 微服务网关前端代码使用说明

### 运行后端代码

- 首先git clone 本项目

`git clone git@github.com:James2333/go_gateway_view.git`

- 确保本地环境安装了nodejs

```
node -v
v11.9.0
```

- 安装运行

```
cd go_gateway_view
npm install -g cnpm --registry=https://registry.npm.taobao.org
cnpm install &&npm run build:prod
```
#### 部署
- 前端项目一个端口
- 接口项目一个端口
- 使用nginx将后端接口设置到跟前端同域下访问
```
    server {
        listen       8882;
        server_name  localhost;
        root /opt/go_gateway_view/dist;
        index  index.html index.htm index.php;

        location / {
            try_files $uri $uri/ /index.html?$args;
        }

        location /prod-api/ {
            proxy_pass http://127.0.0.1:8880/;
        }
    }

```
##之后访问ip:8882
即可看到前端页面