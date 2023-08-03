### Home11

Все затолкал в роль с распределением по папкам

структура папок
```
ltemans@Home01:~/otus/home11$ tree ./
./
├── ansible
│   ├── ansible.cfg
│   ├── group_vars
│   │   └── all.yml
│   ├── hosts
│   ├── nginx.yml
│   ├── roles
│   │   └── nginx
│   │       ├── handlers
│   │       │   └── main.yml
│   │       ├── tasks
│   │       │   └── main.yml
│   │       └── templates
│   │           └── nginx.conf.j2
│   └── Vagrantfile
└── readme.md
```

результат запуска

```
ltemans@Home01:~/otus/home11/ansible$ ansible-playbook nginx.yml

PLAY [NGINX | Install and configure NGINX] ******************************************************************************************************************************

TASK [Gathering Facts] **************************************************************************************************************************************************
ok: [nginx]

TASK [include_role : nginx] *********************************************************************************************************************************************

TASK [nginx : NGINX | Install EPEL Repo package from standart repo] *****************************************************************************************************
changed: [nginx]

TASK [nginx : NGINX | Install NGINX package from EPEL Repo] *************************************************************************************************************
changed: [nginx]

TASK [nginx : NGINX | Create NGINX config file from template] ***********************************************************************************************************
changed: [nginx]

RUNNING HANDLER [nginx : restart nginx] *********************************************************************************************************************************
changed: [nginx]

RUNNING HANDLER [nginx : reload nginx] **********************************************************************************************************************************
changed: [nginx]

PLAY RECAP **************************************************************************************************************************************************************
nginx                      : ok=6    changed=5    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0  
```

результат curl

```
altemans@Home01:~/otus/home11/ansible$ curl http://192.168.56.150:8080
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
  <title>Welcome to CentOS</title>
  <style rel="stylesheet" type="text/css"> 

        html {
        background-image:url(img/html-background.png);
        background-color: white;
        font-family: "DejaVu Sans", "Liberation Sans", sans-serif;
        font-size: 0.85em;
        line-height: 1.25em;
        margin: 0 4% 0 4%;
        }

        body {
        border: 10px solid #fff;
        margin:0;
        padding:0;
        background: #fff;
        }

        /* Links */

```