---
title: '管理员手册'
publishDate: 2022-10-31
date: 2022-10-31
---

## RWR 存档后台管理

### 前端

管理界面: 仓库地址: [https://github.com/Kreedzt/rwr-profile-web](https://github.com/Kreedzt/rwr-profile-web)
查询页面: 仓库地址: [https://github.com/Kreedzt/rwr-profile-stats](https://github.com/Kreedzt/rwr-profile-stats)
数据可视化页面: 仓库地址: [https://github.com/Kreedzt/rwr-profile-visualization](https://github.com/Kreedzt/rwr-profile-visualization)

### 后端

仓库地址: [https://github.com/Kreedzt/rwr-profile-server](https://github.com/Kreedzt/rwr-profile-server)

### 部署方式

#### nginx 部署

nginx 托管 前端页面, API 反向代理至后端
反向代理如下配置:

```nginx
 server {
        listen 9090;
        server_name localhost;

        # 管理: 前端页面
        location / {
            # 注意: win server 2016 与 2012 的路径分隔符可能不同, 此处适用于 2016
            root C://Users//Administrator//Documents//rwr-web//dist;
            try_files $uri $uri/ /index.html;
            index index.html;
        }

        # API 转发
        location /api/ {
         	proxy_set_header HOST $host;
        	proxy_set_header X-Forwarded-Proto $scheme;
       	 	proxy_set_header X-Real-IP $remote_addr;
        	proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_pass http://127.0.0.1:8080/;
        }
}

server {
      listen 9091;
      server_name localhost;

      # 数据可视化: 前端页面
      location / {
          root C://Users//Administrator//Documents//rwr-web//visualization;
          try_files $uri $uri/ /index.html;
          index index.html;
      }

      # API 转发
      location /api/ {
          proxy_set_header HOST $host;
          proxy_set_header X-Forwarded-Proto $scheme;
          proxy_set_header X-Real-IP $remote_addr;
          proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
          proxy_pass http://127.0.0.1:8080/;
      }
}

server {
      listen 9292;
      server_name localhost;

      # 数据查询: 前端页面
      location / {
          root C://Users//Administrator//Documents//rwr-web//stats;
          try_files $uri $uri/ /index.html;
          index index.html;
      }

      # API 转发
      location /api/profile/query_all_cache {
          proxy_set_header HOST $host;
          proxy_set_header X-Forwarded-Proto $scheme;
          proxy_set_header X-Real-IP $remote_addr;
          proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
          proxy_pass http://127.0.0.1:8080/profile/query_all_cache;
    }
}
```

## Mod 内数据提取

> 每次 mod 更新时重新提取

武器数据提取: 仓库地址: [https://github.com/Kreedzt/rwr-gfl-weapon-parser](https://github.com/Kreedzt/rwr-gfl-weapon-parser)
护甲数据提取: 仓库地址: [https://github.com/Kreedzt/rwr-gfl-armor-parser](https://github.com/Kreedzt/rwr-gfl-armor-parser)

# 服务器维护操作

步骤

1. 根据维护类型，提前群内通知玩家
2. 先停止 rwr 游戏服务
3. 等待存档同步完成, 否则存档冲突
4. 备份一次所有玩家的存档
5. 根据维护类型，进行操作
6. 进入存档管理后台，发放福利
7. 第二次备份所有玩家存档
8. 等待存档同步完成, 否则存档冲突
9. 启动 rwr 游戏服务
10. 管理员测试游戏能否正常进入
11. 维护完成
