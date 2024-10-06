# trss-yunzai-guide

草履虫都能看懂的 Linux 下使用 Trss 脚本部署 [云崽](https://github.com/yoimiya-kokomi/Miao-Yunzai) 的教程

## 材料准备

- 一台 Linux 服务器（本地、云服务器或挂机宝均可）

- SSH 工具，推荐 Xterminal [官网下载](https://www.xterminal.cn/) [官方蓝奏云](https://xterminal.lanzouq.com/s/xterminal) 

  > (Windows 用户请下载 `XTerminal-win-x64-installer.exe`)

- 一个没用的 QQ 小号

## 详细步骤

### 连接上服务器

1. 打开 Xterminal ，点击右上角 + 号添加服务器
2. 名称云崽，地址填自己服务器的地址，登录用户 root，密码自己填自己密码
3. 点击测试连接，并且确保通过，没通过就是你账号密码错了，或者服务器不允许 root 登录，那你需要自己去服务器设置一下
4. 点击创建
5. 点击连接

### 安装 1panel 管理面板

> 可能有人好奇为什么装云崽一定要装个服务器管理面板，这里主要是方便一键安装 docker 和 配置 docker 镜像源，后面 trss 要用 docker

1. 打开 https://1panel.cn/docs/installation/online_installation/#2 查看安装命令，我是 Ubuntu 系统，所以找到
   ```shell
   curl -sSL https://resource.fit2cloud.com/1panel/package/quick_start.sh -o quick_start.sh && sudo bash quick_start.sh
   ```

2. 在终端里输入上面的命令

3. 按照下面的步骤进行配置

   >  设置 1Panel 安装目录（默认为/opt）： 

   直接回车

   >  是否配置镜像加速？(y/n):

   输入y

   > 设置 1Panel 端口（默认为13738）：

   输入10000

   > 设置 1Panel 安全入口（默认为7e24b502af）：

   直接回车

   > 设置 1Panel 面板用户（默认为d26b224209）：

   输入admin

   > 设置 1Panel 面板密码，设置完成后直接回车以继续（默认为bf7896ac79）：

   这里自己取一个密码就好了

4. 根据终端里的信息，打开浏览器，进入上面的网址。网址有两个，本地 Linux 就用内网地址，云服务器就用外网地址 (没法访问请检查云服务器安全组是否放行 10000 端口)

   ![](https://cdn.jsdelivr.net/gh/bling-yshs/ys-image-host@main/img/202410051226566.png)

5. 大功告成

   ![](https://cdn.jsdelivr.net/gh/bling-yshs/ys-image-host@main/img/202410051230245.png)

### 通过 Trss 脚本安装云崽

1. 下载 trss 需要的 docker 镜像，在终端执行以下命令

   ```shell
   docker pull ogarcia/archlinux
   ```

2. 执行以下命令

   ```shell
   bash <(curl -L gitee.com/TimeRainStarSky/TRSS_AllBot/raw/main/Install-Docker.sh)
   ```

3. 终端内执行命令 `tsab`，到这个界面

   ![](https://cdn.jsdelivr.net/gh/bling-yshs/ys-image-host@main/img/202410051234473.png)

4. 选择 `Miao-Yunzai`，开始下载

5. 选择打开 `Miao-Yunzai`

6. 输入QQ小号的账号密码，登录设备选 `aPad`，主人QQ号填自己QQ，签名API地址留空

7. 会提示登录失败，别急，ctrl+c 退出，选 `启动 fish`，输入以下命令

   ```shell
   curl -L Gitee.com/haanxuan/QSign/raw/main/X | bash
   ```

8. 没出现红色字，就输入

   ```shell
   curl https://gitee.com/bling_yshs/res-repo/raw/master/yunzai/script/trss-redis-fix.sh | bash
   ```

9. 没出现红色字，就输入

   ```shell
   curl https://gitee.com/bling_yshs/res-repo/raw/master/yunzai/script/qq-pic-read-fix.sh | bash
   ```

10. 没出现红色字，就输入

   ```shell
   exit
   ```

11. 有可能触发滑动验证码，按住 shift 不松开，用鼠标选择网址，复制，然后在本机浏览器打开，自己过一下验证码就好

12. 大功告成

### 安装云崽插件

1. 先 ctrl+c ，选择返回菜单
2. 停止 Miao-Yunzai
3. `插件管理` -> `Git 插件管理` -> `安装插件` -> 想装啥装啥
4. 启动  Miao-Yunzai

### 附录

1. 云崽插件库 https://gitee.com/yhArcadia/Yunzai-Bot-plugins-index

2. tsab 界面操作快捷键 https://trss.me/Guide/Command.html

3. trss 容器内文件已映射到 `/root/TRSS_AllBot`，可以直接在容器外进行修改

### 鸣谢

[Trss](https://github.com/TimeRainStarSky/TRSS_Script)

[喵云崽](https://github.com/yoimiya-kokomi/Miao-Yunzai)
