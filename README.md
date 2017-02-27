# Docker Compose App for VMware Cluster Rules Manager Fling

Docker Compose App consisting of Tomcat and MySQL Docker Container ready to run VMware Cluster Rules Manager Fling. Docker Volume is also used to persist the MySQL db to your Docker Host which will be located in root folder of Docker Compose App called **crmdb**.

## Requirements

* Docker Host (PhotonOS or any other system that can run docker)
* Docker Compose (have a look [here](https://docs.docker.com/compose/install/) on how to install)
* Access to vCenter Server

## Usage

Step 1 - Download the [Cluster Rules Manager Fling zip](https://download3.vmware.com/software/vmw-tools/crm/crm%20downloads-v1.0.zip).

Step 2 - Extract **crm.war** and **crminstallationkeystore.jks** from the zip file.

Step 3 - Download the Docker Compose App zip from [here](https://github.com/lamw/crm-fling-docker-compose-app/archive/master.zip) and extract it to your desktop. 

You should end up with a directory called **crm-fling-docker-compose-app** which contains the following structure:

```
├── app
│   ├── Dockerfile
│   └── server.xml
├── db
│   ├── Dockerfile
│   └── data.sql
└── docker-compose.yml
```

Step 4 - Copy both **crm.war** and **crminstallationkeystore.jks** into the **app** directory.

Step 5 - Upload the **crm-fling-docker-compose-app** to your Docker Host. 

Step 6 - Change into the **crm-fling-docker-compose-app** directory and build our Docker application by running the following:

```
docker-compose up
```

If everything was successful, you should now be able to launch the CRM application by opening a browser to the following URL:

```
https://[DOCKER-HOST]:8443/crm
```

When prompted for the DB Server, use the same IP Address as the Docker Host with following credentials:

**Default MySQL Credentials**
* Username: root
* Password: VMware1!

Note: If you wish to change the default password of the MySQL, edit the docker-compose.yml and update the **MYSQL_ROOT_PASSWORD** variable with your new password.
