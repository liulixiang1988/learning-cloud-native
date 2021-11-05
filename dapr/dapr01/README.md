# How to use

[toc]

## 直接执行

```bash
python main.py
```

## 安装Dapr

https://docs.dapr.io/getting-started/install-dapr-cli/

## 通过Dapr执行

需要有docker

**1.初始化**

```bash
>dapr init 
Making the jump to hyperspace...
Installing runtime version 1.4.3
Downloading binaries and setting up components...
Downloaded binaries and completed components set up.
daprd binary has been installed to C:\Users\刘理想\.dapr\bin.
dapr_placement container is running.
dapr_redis container is running.
dapr_zipkin container is running.
Use `docker ps` to check running containers.
Success! Dapr is up and running. To get started, go here: https://aka.ms/dapr-getting-started
```

**2.运行**

```bash
>dapr run --app-id api --app-port 8000 --dapr-http-port 3500 python main.py
```

- `app-port`：原有端口
- `dapr-http-port`：dapr端口

修改pyapi.http中的端口为3500，再次访问，发现增加了trace

```http
HTTP/1.1 200 OK
Server: uvicorn
Date: Fri, 05 Nov 2021 08:24:03 GMT
Content-Type: application/json
Content-Length: 29
Traceparent: 00-ed817a50ee323045568483ec56673a72-de3712e82963783a-01
Connection: close

{
  "message": "Helo liulixiang"
}
```

**3.dashboard**

```bash
dapr dashboard
```
