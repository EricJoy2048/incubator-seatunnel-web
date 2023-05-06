# Apache SeaTunnel (Incubating)

<img src="https://seatunnel.apache.org/image/logo.png" alt="seatunnel logo" height="200px" align="right" />

[![Backend Workflow](https://github.com/apache/incubator-seatunnel/actions/workflows/backend.yml/badge.svg?branch=dev)](https://github.com/apache/incubator-seatunnel/actions/workflows/backend.yml)
[![Slack](https://img.shields.io/badge/slack-%23seatunnel-4f8eba?logo=slack)](https://join.slack.com/t/apacheseatunnel/shared_invite/zt-123jmewxe-RjB_DW3M3gV~xL91pZ0oVQ)
[![Twitter Follow](https://img.shields.io/twitter/follow/ASFSeaTunnel.svg?label=Follow&logo=twitter)](https://twitter.com/ASFSeaTunnel)

---
[![EN doc](https://img.shields.io/badge/document-English-blue.svg)](README.md)

SeaTunnel was formerly named Waterdrop , and renamed SeaTunnel since October 12, 2021.

---

So, What we are?

An open-source web console to manage your seatunnel-script, and would push them to any scheduling-system easily.
Click it if your want to know more about our design. 👉🏻[Design](https://github.com/apache/incubator-seatunnel/issues/1947)


## How to start

### Preparing the Apache DolphinScheduler environment

#### Install Apache DolphinScheduler

If you already have Apache DolphinScheduler environment, you can skip this step and go to `Create Tenant and User for SeaTunnel Web`

Because running SeaTunnel Web must rely on the DolphinScheduler, if you do not have a DS environment, you need to first install and deploy a DolphinScheduler (hereinafter referred to as DS). Taking DS version 3.1.5 as an example.

Reference https://dolphinscheduler.apache.org/zh-cn/docs/3.1.5/guide/installation/standalone to install a standalone DS.

#### Create Tenant and User for SeaTunnel Web

If you already have a DS environment and decide to use existing users and tenants for SeaTunnel Web, you can skip this step and go to `Create Project for SeaTunnel Web`.

Because SeaTunnel Web needs to call the interface of DS to create workflows and tasks, it is necessary to submit the projects, users, and tenants created in DS for SeaTunnel to use.

1. Create Tenant

"Security" -> "Tenant Manage" -> "Create Tenant"

![image](docs/images/ds_create_tenant.png)

2. For simplicity, use the default user admin of DS directly here

#### Create Project for SeaTunnel Web

![image](docs/images/ds_create_project.png)

#### Create Token for SeaTunnel Web

![image](docs/images/ds_create_token.png)

### Run SeaTunnel Web in IDEA

#### Init database 

1. Edit `whaletunnel-server/whaletunnel-app/src/main/resources/script/seatunnel_server_env.sh` file, Complete the installed database address, port, username, and password. Here is an example:

    ```
    export HOSTNAME="localhost"
    export PORT="3306"
    export USERNAME="root"
    export PASSWORD="123456"
    ```
2. Run init shell `sh seatunnel-server/seatunnel-app/src/main/resources/script/init_sql.sh` If there are no errors during operation, it indicates successful initialization.

#### Config application and Run SeaTunnel Web Backend Server

1. Edit `seatunnel-server/seatunnel-app/src/main/resources/application.yml` Fill in the database connection information and DS interface related information in the file.

![image](docs/images/application_config.png)

2. Run `seatunnel-server/seatunnel-app/src/main/java/org/apache/seatunnel/app/SeatunnelApplication.java` If there are no errors reported, the seatunnel web backend service is successfully started.

#### Run SeaTunnel Web Front End

```
cd seatunnel-ui
npm install
npm run dev

```

If there are no issues with the operation, the following information will be displayed:

```
  ➜  Local:   http://127.0.0.1:5173/
  ➜  Network: use --host to expose
  ➜  press h to show help

```

Accessing in a browser http://127.0.0.1:5173/login Okay, the default username and password are admin/admin.

### How to use it

After all the pre-work is done, we can open the following URL: 127.0.0.1:7890(please replace it according to your configuration) to use it.

Now ,let me show you how to use it.

#### User manage

![img.png](docs/images/user.png)

#### Datapipeline manage

![img.png](docs/images/datapipeline.png)

#### Job manage
![img.png](docs/images/job.png)

#### Task manage
![img.png](task.png)