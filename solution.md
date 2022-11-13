## Creation of EC2 Instances

Created an EC2 instances each for nexus, sonarqube and jenkins
* Nexus - centos, t2.medium(4gb ram)
* Sonarqube - ubuntu18, t2.medium
* Jenkins - ubuntu20, t2.small

![](./img/j1.png)

## Setting up Jenkins, Nexus and Sonarqube servers

1. Jenkins

* On the terminal, cd into jenkins server using the public-IP address
* check if ther server is up and running
```
systemctl status jenkins
```

* Open TCP port 8080 to allow incoming traffic from anywhere

![](./img/j2.png)

* Check the accessibility of the server on a browser, using public-IP address
`http://<Public-IP-Address>:8080`

![](./img/j3.png)

* After succesful accessibility, setup jenkins on the browser, On the server `cat` the password
```
cat /var/lib/jenkins/secrets/InitialPassword
```

![](./img/j4.png)

* Install recommended plugins and setup a profile

![](./img/j5.png)

2. Nexus

* On the terminal, ce into nexus to check if the server is up and running

* Open TCP port 8081 to allow inbound traffic from anywhere

![](./img/j6.png)

* Access the instance on a browser using public-IP

![](./img/j7.png)

* Sign in using `admin` as username and `cat /opt/nexus/sonatype-work/nexus3/admin.password ` for passwd

![](./img/j8.png)

* Set a new password and enable anonymous access

3. Sonarqube

* On the terminal, ce into nexus to check if the server is up and running

* Open TCP port 80 and 9000 to allow inbound traffic from anywhere

![](./img/j9.png)

* Sign in using `admin` as username and password
