# richppt
## 安装
`npm install -g nodeppt`

## shell使用
### 启动
```
# 获取帮助
nodeppt start -h
# 绑定端口
nodeppt start -p <port>
```

```
nodeppt start -p 8090 -d path/for/ppts
# 绑定host，默认绑定0.0.0.0
nodeppt start -p 8080 -d path/for/ppts -H 127.0.0.1
# 使用socket通信（按Q键显示/关闭二维码，手机扫描，即可控制）
# socket须知：1、注意手机和pc要可以相互访问，2、防火墙，3、ip
```
### 启用socket控制
#### 方法一：使用url参数
```
http://127.0.0.1:8080/md/demo.md?controller=socket
```
#### 方法二：使用`start`命令行
```
nodeppt start -c socket
```
在页面按键【Q】显示控制url的二维码和控制链接（需要隐身窗口打开），手机上可以使用左右touch滑动和摇一摇切换下一页

### 启用postMessage控制
默认使用postMessage多窗口控制，打开方法：
```
http://127.0.0.1:8080/md/demo.md?_multiscreen=1
```
