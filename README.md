# This page is still under development


# CouchMovies

This is a sample project shows how to build a search feature using Bleve/Couchbase FTS

# Demo
TBD

## Pull and run a docker image
pull docker couchbase
docker run -d --name couchmovies -p 8000:8000 -p 8080:8080 -p 8091-8096:8091-8096 -p 11210-11211:11210-11211 couchbase
docker exec -it couchmovies bash

## Configure environment inside Docker
```
apt-get update
apt-get -y  install git sudo

useradd -m -p $(openssl passwd -1 demo) demo
usermod -aG sudo demo
echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
echo "PATH=/opt/couchbase/bin:\$PATH" >> /home/demo/.profile
su -l demo
git clone https://github.com/escapedcanadian/couchmovies

cd couchmovies/build
. .env
./installToolsDebian
./createCluster
./loadData
./createRBAC

cd /home/demo/couchmovies
mvn clean install

mvn spring-boot:run &

./front/runWebServer &su 

```  


9) Copy the content of the "front" folder in a web server (Ex: NGINX) and access the couchflix.html

10) OPTIONAL: If you want to enable the image cover (the image that appears when you click over a movie) you will need to install a chrome driver:
```
brew cask install chromedriver //on mac
```

And then update the path to your chrome driver in the class "ImageService.java"
