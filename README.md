# Docker Compose App for VMware Cluster Rules Manager Fling

Docker Compose App consisted of Tomcat and MySQL Docker Container ready to run VMware Cluster Rules Manager Fling. 

## Requirements

* Docker Host (PhotonOS or any other system that can run docker and docker-compose
* Git (included in PhotonOS)
* Docker Compose (have a look [here](https://docs.docker.com/compose/install/) on how to install)
* Access to vCenter Server

## Usage

Step 1 - Download the [Cluster Rules Manager Fling zip](https://download3.vmware.com/software/vmw-tools/crm/crm downloads-v1.0.zip).

Step 2 - Extract **crm.war** and **crminstallationkeystore.jks** from the zip file.

Step 3 - Clone this Github repository by running the following command:

```console
git clone https://github.com/lamw/crm-fling-docker-compose-app
```
You should end up with a directory called **crm-fling-docker-compose-app** which contains the following structure:

```
├── app
│   ├── Dockerfile
│   └── server.xml
├── db
│   ├── Dockerfile
│   └── data.sql
└── docker-compose.ym
```

Step 4 - Copy both **crm.war** and **crminstallationkeystore.jks* into the **app** directory

Step 5 - Change into the **crm-fling-docker-compose-app** directory and build our Docker application by running the following:

```
docker-compose up
```

If everything was successful, you should now be able to launch the CRM application by going to the IP Address of the Docker Host (this could also be localhost if you are running on your local desktop):

```
https://[DOCKER-HOST]:8443/crm
```

Note: If you wish to change the default password of the MySQL, edit the docker-compose.yml and update **MYSQL_ROOT_PASSWORD** which is for the root account which will be provided to the CRM application when asked for database connection. 