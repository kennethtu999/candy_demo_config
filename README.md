## Using DevOps environment

### available login admin ID
- devops / password

### Service location


| Application | URL(IP should be changed)   | Specified Account |
|-------------|-----------------------------|-------------------|
| Nexus       | http://192.168.99.102:10083 | admin / admin123  |
| SonarQube   | http://192.168.99.102:10082 | admin / admin     |
| Jenkins     | http://192.168.99.102:10081 | root / password   |
| Gitlab      | http://192.168.99.102:10080 | root / password   |

## Setup DevOps environment
1. install CentOS
1. [install Docker](https://store.docker.com/editions/community/docker-ce-server-centos)
1. install docker-compose
```
sudo yum -y install epel-release
sudo yum -y install python-pip
sudo pip install docker-compose
```

1. install other tools
```
yum -y install wget git
```

1. auto start docker service on boot
```
sudo systemctl enable docker
```


## Install DevOps software
### Gitlab (Version Control)
```
mkdir gitlab
cd gitlab
wget https://raw.githubusercontent.com/sameersbn/docker-gitlab/master/docker-compose.yml
docker-compose up
```

#### other command
- run docker-compose background `docker-compose up -d`

#### reference
- https://github.com/sameersbn/docker-gitlab

#### config and add testing projects
1. browser to http://192.168.99.102:10080
  - set a password for the root user accoun
1. add following projects using **Repo by URL** and set access permission as public
  - https://github.com/kennethtu999/candy_demo_config.git
  - https://github.com/kennethtu999/candy_demo_java_war.git

### Jenkins (CI SERVER)
```
mkdir jenkins
cd jenkins
docker-compose up
```

#### other command
- run docker-compose background `docker-compose up -d`

#### reference
1. https://hub.docker.com/_/jenkins/
1. https://twasink.net/2016/08/01/setting-up-a-jenkins-server-with-docker/

#### config
1. browser to http://192.168.99.102:10081


### SonarQube (Code Quality)
```
mkdir nexus
cd nexus
docker-compose up
```

#### config
1. browser to http://192.168.99.102:10082


#### reference
- https://github.com/SonarSource/docker-sonarqube/blob/master/recipes.md


### nexus (artifact repository)
```
mkdir nexus
cd nexus
docker-compose up
```

#### config
1. browser to http://192.168.99.102:10083
  - Default credentials are: admin / admin123

#### reference
- https://hub.docker.com/r/sonatype/nexus3/
