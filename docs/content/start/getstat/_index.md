# 调试项目

目前项目的前端页面可以下发指令：
![homepage3](images/homepage3.png)
可以利用该页面进行调试，但是缺点是不能增加别的指标字段，所以推荐使用postman来进行调试

项目最终实现的逻辑应该是前端首先获取目前的所有插件信息，然后显示在页面上，之后再由用户下发指令，所有插件的更新、删除都是自动进行，目前后端尚不完善，所以前端页面还并不支持这些功能。

### 采用 Postman 调试

Postman的设置如下：

- POST请求
- 访问URL为 `127.0.0.1:8080/collectdata`
- Headers设置如下：

  ![postman-headers](images/postman-headers.png)
- Body设置如下：

  ![postman-body](images/postman-body.png)
  
  Body部分需要采用如下的json格式:
  ```json
    {
    "plugins":{
    "irq":"bcc"
    },
    "pluginsruntime":1
    }
  ```
  plugins传输一个map，key是指标名，value是指标类型，可以自己增加需要测试的插件，注意指标类型必须是bcc；pluginsruntime是提取数据的时长，以分钟为单位。

之后编译、启动项目，就可以进行调试，注意MySQL数据库中需要有 `lmp` 的database，之后 `make db`，`make`，`sudo ./lmp`。
