# WBO 协作白板 懒猫微服包

自托管在线协作白板，支持多人实时绘制。

- 上游：<https://github.com/lovasoa/whitebophir>
- 镜像：`lovasoa/wbo`
- 许可：AGPL-3.0（全文见 content/licenses/LICENSE，已核对无子目录覆盖条款）

## 组成

单容器，容器内监听 80 端口；白板数据放在持久化目录里。

## 关键配置说明

- **`WBO_IP_SOURCE=X-Forwarded-For`**：上游 README 明确指出，容器跑在可信反代后面时
  必须显式设置，否则应用只看到代理自己的地址（影响限流与审计）。
- 数据目录 `/opt/app/server-data`（上游要求 uid 1000 可写），挂到 `/lzcapp/var/server-data`。
- **没有账号体系**：谁能访问入口谁就能协作，因此不加 `public_path`，由懒猫入口鉴权。
- 白板名即链接末段，换名字就是新白板。

## 未验证部分

未在真机上实测：多人实时绘制、便签与图片、导出、重启后数据留存。
