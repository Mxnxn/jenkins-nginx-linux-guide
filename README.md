# Jenkins Guide for pre-existing react projects
I've faced a lot of errors and utilized a significant amount of time to deploy successfully.

<img src="https://github.com/Mxnxn/jenkins-reactjs-guide/blob/master/logos/jenkins.png" alt="drawing" width="300"/> <img src="https://github.com/Mxnxn/jenkins-reactjs-guide/blob/master/logos/reactjs.png" alt="drawing" width="200"/>

## Techs
1. Nodejs/NVM/npm
2. Reactjs
3. bun package manager (faster than node/yarn)
4. Jenkins
5. Digital Ocean Droplet (25 GB)
6. Github Actions
> **Note:** I have not used **Docker** in this process.

# Installation
## Jenkins
I've run through this command to install Jenkins.
```
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt install jenkins
```
to run 
```
sudo systemctl start jenkins
```
if you get error while starting you may check for java and jvm
```
sudo update-alternatives --config java
```
you'll see output like this \
\
<img src="https://github.com/Mxnxn/jenkins-reactjs-guide/blob/master/assets/Termius_4SyzqUzGWf.png" alt="drawing" width="600"/>

## Nodejs and Npm
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash
source ~/.bashrc # your bash/shell
nvm --version
nvm install node #default
npm install -g npm
node -v
npm -v
```
## Bun 
```
npm install -g bun #can run as sudo as  well.
```
other way
```
curl -fsSL https://bun.sh/install | bash
```
