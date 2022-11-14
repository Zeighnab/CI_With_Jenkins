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

## Plugins for CI on Jenkins

1. Install additional plugins needed for integration

2. On Jenkins Dashboard, click on `Manage Jenkins`

![](./img/j10.png)

3. Do the following:

* Check `Enable proxy compatibility`, under `Configure Global Security`, and save

* Install these plugins; `Nexus Artifact Uploader`, `Sonarqube Scanner`, `Build Timestamp`, `Pipeline maven integration` and `pipeline utility steps`, under `Manage Plugins`

![](./img/j11.png)

* Add `OracleJDK8` and `Maven3`, under `Global Tool Configuration`

![](./img/j12.png)

![](./img/J13.png)

## Build and Test

1. Click on `Create Job` on the Dashboard, enter the build name and  choose `Pipeline`

![](./img/j14.png)

2. On the Configuration page, under pipeline, paste your pipeline script, and save

![](./img/j15.png)

3. Click on `Build Now`

![](./img/j16.png)

## Code Analysis

1. Integrate Sonarqube with Jenkins

* Under, `Global Tool Configuration`, Add `SonarQube Scanner`

![](./img/j17.png)

* On sonarqube dashboard, goto `My Account`, then `Security` to generate a token

![](./img/j18.png)

* In Jenkins,under `Configure System`, Add Sonar Servers and your generated token

![](./img/j19.png)

2. Build our script

![](./img/j20.png)

![](./img/j21.png)

## Quality Gate - Threshold for bugs

* Create a quality gate and set conditions needed to fail a build

![](./img/j22.png)

* Link the project to the quality gate. Goto the project setting, click on quality gate and choose the created quality gate

![](./img/j23.png)

* Use webhooks to send information back to jenkins

![](./img/j24.png)

* Build the script

![](./img/j25.png)

![](./img/j26.png)

## Upload Artifact To Nexus

1. Create Repository using maven(hosted) to store artifact

![](./img/j27.png)

2. Integrate Jenkins with Nexus by setting credentials

![](./img/j28.png)

3. Build the script. Access the nexus repository to validate its storage

![](./img/j29.png)

## Slack Notification