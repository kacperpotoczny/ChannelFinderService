# Installation

ChannelFinder is a Java EE5 REST-style web service. The directory data is held in a ElasticSearch index.

## Docker Compose

For using docker containers there is a barebones [docker compose file](./compose.yml).

## Manual Installation

* Prerequisites

    * JDK 25
    * Elastic version 8.18.x
    * **For authN/authZ using LDAP:** LDAP server, e.g. OpenLDAP

### Setup Elasticsearch

Options:

- Download and install elasticsearch (version 8.18.0)
  from [elastic.com](https://www.elastic.co) following the instructions for
  your platform.
- Install the elastic server from your distribution using a package manager.
- Run Elasticsearch in a [docker container](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html)

### Running

```bash
sudo apt-get install openjdk-25-jre git curl wget
sudo systemctl start elasticsearch # Or other command to run elastic search

# Replace verison with the release you want
wget https://github.com/ChannelFinder/ChannelFinderService/releases/download/ChannelFinder-{version}/ChannelFinder-{version}.jar 
java -jar target/ChannelFinder-*.jar
``` 

Other installation recipes can be found
on [the wiki pages](https://github.com/ChannelFinder/ChannelFinder-SpringBoot/wiki).

## Configuration

By default, the channelfinder service will start on port 8080 with the default settings. To start with a
different `application.properties` file:

```bash
java -Dspring.config.location=file:./application.properties -jar ChannelFinder-*.jar
```

The default authentication includes an embedded ldap server with users and roles defined in
the [`cf.ldif`](src/main/resources/cf.ldif) file.
Note that `cf.ldif` contains **default credentials** and should only be used during testing and evaluation.

## Verification

To check that the server is running correctly, visit [the default homepage](http://localhost:8080/). For more
information on the api see the [swagger docs endpoint](http://localhost:8080/swagger-ui/index.html).

## Demo account

By default there are configured two demo accounts (admin and user), to test and show system capabilites. You can find more in config file in src/main/resources/application.properties:

```java
demo_auth.enabled = true
demo_auth.delimiter.roles = :
demo_auth.users = admin,user
demo_auth.pwds = adminPass,userPass
demo_auth.roles = ADMIN,USER 
```
