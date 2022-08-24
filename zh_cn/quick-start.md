# 快速部署

!> 目前项目仍处于开发阶段，请勿部署到正式环境。

## 初始化

请务必在**全新的 Debian 11** 中以 **root** 运行下列命令初始化环境

```bash
cd /tmp
wget https://raw.githubusercontent.com/UISSH/install-script/main/install.sh
bash install.sh
```

## 安装

数据库以及面板用户名默认为： **root**

<!-- tabs:start -->

#### **绑定域名**

> 域名需要提前设置，否则将会回退到  **直接安装**  进行安装。

```bash
cd /tmp/install-script 
python3 main.py --login_email=* --db_root_password=* --login_password=* --domain=your.domain.com
```

?> 强烈建议绑定域名方式安装，这样将会自动开启 SSL 加密敏感数据传输。(http 将升级为 https, ws 将升级为 wss，phpMyAdmin 也将使用
SSL)

#### **直接安装**

!> 除非您在本机上安装以及承担明文传输将会泄露敏感数据的风险之外，强烈不建议使用这种方式部署。

```bash
cd /tmp/install-script 
python3 main.py --login_email=* --db_root_password=* --login_password=* 
```

#### **参数说明**

- --login_email
    - 登录邮箱地址，此外还用于证书到期通知以及其他需要邮箱地址的默认值

- --db_root_password
    - 面板登录密码

- --domain
    - 绑定面板域名

<!-- tabs:end -->

## 会安装哪些软件？

脚本会默认安装以下软件以及相关依赖，默认均从系统源或官网下载。

| 软件名 | 版本 |
|------------|--|
| Nginx | 系统默认 |
| PHP | 系统默认 |
| MariaDB | 系统默认 |
| phpMyAdmin | [v5.2.0](https://github.com/UISSH/install-script/blob/main/src/phpMyAdmin/phpMyAdmin.py#L29) |
| Python3 | 系统默认 |
| snapd | 系统默认 |
| certbot | 系统默认 |
| Osquery | [v5.0.3](https://github.com/UISSH/install-script/blob/main/src/osquery/osquery.py#L41) |
| 其他以上必须依赖的组件 | 系统默认 |

## 项目位置

```bash
# 程序默认位置
/usr/local/uissh
# systemd
/lib/systemd/system/ui-ssh.service
```
