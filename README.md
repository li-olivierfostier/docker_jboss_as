[![logo](https://raw.githubusercontent.com/li-olivierfostier/docker-jboss-as/master/as7_logo.png)]
(http://jbossas.jboss.org/)

[![Circle CI](https://circleci.com/gh/li-olivierfostier/docker-jboss-as.svg?style=shield)]
(https://circleci.com/gh/li-olivierfostier/docker-jboss-as)


# Information

The base docker image :

  * [ofostier/ubuntu](https://registry.hub.docker.com/u/ofostier/ubuntu/)

The GitHub project :

  * [ofostier/docker-jboss-as](https://github.com/li-olivierfostier/docker-jboss-as/)



# Installation

You can clone this project and build with docker command :

```
git clone https://github.com/li-olivierfostier/docker-jboss-as.git \
&& cd docker-jboss-as \
&& docker build -t ofostier/jboss-as-711 .
```

You can build directly from the [GitHub project](https://github.com/li-olivierfostier/docker-jboss-as/) :

```
docker build -t ofostier/jboss-as-711 \
github.com/li-olivierfostier/docker-jboss-as.git
```



# Help

To display usage :

```
docker run --rm ofostier/jboss-as-711 /help
```



# Usage

Quick start with binding to port 8080, 9990 and random password :

```
docker run -d -p 8080:8080 -p 9990:9990 ofostier/jboss-as-711
```

To get the password :

```
docker logs <container id>
```

Start and set a specific password for JBoss admin user :

```
docker run -d -p 8080:8080 -p 9990:9990 -e JBOSS_PASS="pass" \
ofostier/jboss-as-711
```

If you forget the admin password, delete the file .password and restart the container :

```
docker exec -it <container id> rm /.password
```


# Deploy a war

To deploy a specific file.war, you need to make another container.
Create a new directory and put your file.war.
Then, create a new Dockerfile :

```
FROM ofostier/jboss-as-711
ADD file.war /opt/jboss-as-7.1.1.Final/standalone/deployments/file.war
```
