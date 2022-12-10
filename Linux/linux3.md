1. Ctrl + c 强制停止（跟MATLAB一样）
2. Ctrl + d退出当前用户
3.  history 查看历史指令
4. Ctrl + r ‘关键词’ 匹配command
5. ![Pasted image 20221126175024](./linux3.assets/Pasted%20image%2020221126175024.png)
6. ![Pasted image 20221126175052](./linux3.assets/Pasted%20image%2020221126175052.png)
7. systemctl start/stop/status/enable/disable 软件名 **可以控制软件**
8.  ln -s 被链接的文件/文件夹 要链接去的目的地  类似【快捷方式】
9. ifconfig 查看IP地址
10. 10. ping -c [num] ip/主机名 (**实测百度可以，谷歌不行**)
11. wget -b url 下载网络环境，-b 是后台下载，不会显示进度
12. curl -O url 向网络发起请求，-O是下载的意思
13. 端口可以锁定电脑的程序
14. kill -9 进程ID -9表示强制关闭
15. ps -ef 查看进程信息   ps -ef | grep 过滤内容
16. top 类似Windows的任务管理器，可以查看CPU等信息
17. df 查看磁盘使用率
18. iostat 查看磁盘速率
19. sar -n DEV 查看网络情况，Ubuntu下terminal用不了
20. env 可以查看当前系统环境变量
21. $ 可以取出环境变量的值
