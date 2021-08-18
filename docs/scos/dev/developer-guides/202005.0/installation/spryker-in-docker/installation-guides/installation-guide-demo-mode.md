---
title: Installation Guide - Demo Mode
originalLink: https://documentation.spryker.com/v5/docs/installation-guide-demo-mode
originalArticleId: fca332e7-6016-41e7-bd22-e380b8949de6
redirect_from:
  - /v5/docs/installation-guide-demo-mode
  - /v5/docs/en/installation-guide-demo-mode
---

This document describes the procedure of installing Spryker in [Demo Mode](/docs/scos/dev/developer-guides/202005.0/installation/spryker-in-docker/installation-guides/modes-overview.html#demo-mode).

{% info_block warningBox %}

Before you start, make sure to fulfill the [prerequisites](/docs/scos/dev/developer-guides/202005.0/installation/spryker-in-docker/docker-installation-prerequisites/docker-installation-prerequisites.html).

{% endinfo_block %}

## Installation 

Follow the steps to install Spryker in Demo Mode:
1. Open a terminal.
{% info_block infoBox %}
In case you are going to run the script on Windows, open Ubuntu (For more details, see the *Install Docker Desktop* section in [Docker Installation Prerequisites - Windows](/docs/scos/dev/developer-guides/202005.0/installation/spryker-in-docker/docker-installation-prerequisites/docker-installation-prerequisites.html-windows
{% endinfo_block %}.))
2. Create a new folder and navigate into this folder.
3. Depending on the desired [Demo Shop](https://documentation.spryker.com/v5/docs/en/en/about-spryker#spryker-b2b-b2c-demo-shops):

    a. Clone the B2C repository:

    ```shell
    git clone https://github.com/spryker-shop/b2c-demo-shop.git -b 202001.0 --single-branch ./
    ```

    b. Clone the B2B repository:

    ```shell
    git clone https://github.com/spryker-shop/b2b-demo-shop.git -b 202001.0 --single-branch ./
    ```
4. Depending on the cloned repository, navigate into the cloned folder:
    * B2C repository:
    ```bash
    cd b2c-demo-shop
    ```
    * B2B repository:
    ```bash
    cd b2b-demo-shop
    ```
{% info_block warningBox "Verification" %}

Make sure that you are in the correct folder by running the `pwd` command.

{% endinfo_block %}

5. In `deploy.yml`, define `image:` with the PHP image compatible with the current release of the demo shop:

```yaml
image: spryker/php:7.2-alpine3.10
```

6. Clone the Docker repository into the same folder:
```shell
git clone git@github.com:spryker/docker-sdk.git -b 1.6.3 --single-branch docker
```
{% info_block warningBox "Verification" %}

Make sure `docker 18.09.1+` and `docker-compose 1.23+` are installed:

```bash
$ docker version
$ docker-compose --version
```

{% endinfo_block %}
7. Bootstrap the local Docker setup for demo:
```shell
docker/sdk bootstrap
```

 
{% info_block warningBox "Bootstrap" %}

Once you finish the setup, you don't need to run `bootstrap` to start the instance. You only need to run it after:
* Docker SDK version update;
* Deploy file update.

{% endinfo_block %}
8. Once the job finishes, build and start the instance:
```shell
docker/sdk up
```
9. Update the `hosts` file:

  - Linux/MacOS:
```shell
echo "127.0.0.1 zed.de.spryker.local yves.de.spryker.local glue.de.spryker.local zed.at.spryker.local yves.at.spryker.local glue.at.spryker.local zed.us.spryker.local yves.us.spryker.local glue.us.spryker.local mail.spryker.local scheduler.spryker.local queue.spryker.local" | sudo tee -a /etc/hosts
```

{% info_block infoBox %}
If needed, add corresponding entries for other stores. For example, if you are going to have a US store, add the following entries: `zed.us.spryker.local glue.us.spryker.local yves.us.demo-spryker`
{% endinfo_block %}
  - Windows:
    1. Click **Start** → **Search** and type "Notepad".
    2. Right-click **Notepad** and select the **Run as administrator option**.
    3. In the **User Account Control** window click **Yes** to confirm the action.
    4. In the upper navigation panel, select **File** → **Open**.
    5. Put the following path into the address line: `C:\Windows\System32\drivers\etc`
    6. In the **File name** line, enter "hosts" and click **Open**.
    The hosts file is opened in the drop-down.
    7. Add the following line into the file:
`127.0.0.1   zed.de.spryker.local glue.de.spryker.local yves.de.spryker.local scheduler.spryker.local mail.spryker.local queue.spryker.local`
    {% info_block infoBox %}
If needed, add corresponding entries for other stores. For example, if you are going to have a US store, add the following entries: `zed.us.spryker.local glue.us.spryker.local yves.us.spryker.local`
{% endinfo_block %}
    9. Click **File** → **Save**.
    10. Close the file.


{% info_block warningBox %}
Depending on the hardware performance, the first project launch can take up to 20 minutes.
{% endinfo_block %}

## Endpoints

To ensure that the installation is successful, make sure you can open the following endpoints:

* yves.de.spryker.local, yves.at.spryker.local, yves.us.spryker.local - Shop UI (*Storefront*)
* zed.de.spryker.local, zed.at.spryker.local, zed.us.spryker.local - Back-office UI (*the Back Office*)
* glue.de.spryker.local, glue.at.spryker.local, glue.us.spryker.local - API endpoints
* scheduler.spryker.local - Jenkins (*scheduler*)
* queue.spryker.local - RabbitMQ UI (*queue*).
{% info_block infoBox %}
Use "spryker" as a username and "secret" as a password. These credentials are defined and can be changed in `deploy.yml`.
{% endinfo_block %}
* mail.spryker.local - Mailhog UI (*email catcher*)

## Useful Commands

Run the `docker/sdk help` command to get the full and up-to-date list of commands.

**What's next?**
* [Troubleshooting](https://documentation.spryker.com/v5/docs/en/peer-authentication-failed-for-user-postgres)
* [Debugging Setup in Docker](/docs/scos/dev/developer-guides/202005.0/installation/spryker-in-docker/debugger-setup-in-docker.html)
* [Deploy File Reference - 1.0](/docs/scos/dev/developer-guides/202005.0/installation/spryker-in-docker/docker-sdk/deploy-file-reference-1.0.html) 
* [Services](/docs/scos/dev/developer-guides/202005.0/installation/spryker-in-docker/configuration/services.html)
* [Self-signed SSL Certificate Setup](/docs/scos/dev/developer-guides/202005.0/installation/spryker-in-docker/configuration/self-signed-ssl-certificate-setup.html) 
* [Additional DevOPS Guidelines](/docs/scos/dev/developer-guides/202005.0/installation/spryker-in-docker/configuration/additional-devops-guidelines.html)
