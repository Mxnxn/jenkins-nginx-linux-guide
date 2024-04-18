# Jenkins Guide for pre-existing react projects
I've faced a lot of errors and utilized a significant amount of time to deploy successfully.

<img src="https://github.com/Mxnxn/jenkins-reactjs-guide/blob/master/logos/jenkins.png" alt="drawing" width="300"/> <img src="https://github.com/Mxnxn/jenkins-reactjs-guide/blob/master/logos/reactjs.png" alt="drawing" width="200"/>

# Prequisites
1. Nginx installation
2. Java jre/jdk installation
3. reactjs repository (which is perfectly builds on server)
4. setup SSH through username and password
5. Certbot
6. Already added A entry on if you are going to run jenkins on subdomain.

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
if you get an error while starting you may check for Java and jvm
```
sudo update-alternatives --config java
```
you'll see output like this \
\
<img src="https://github.com/Mxnxn/jenkins-reactjs-guide/blob/master/assets/Termius_4SyzqUzGWf.png" alt="drawing" width="600"/> \
If you do not see something like this then you may require the jre, jdk as mentioned in the prerequisites
```
sudo apt-get install default-jre
sudo apt-get install java-1.8.0 -y
```

# SSL for Jenkins.
> Note: I've setup Jenkins on the subdomain of my website but you can do by adding a prefix and path like `example.com/jenkins`
## Setup for Jenkins for SSL
We need to change the domain and prefix in JENKINS_ARG
```
sudo nano /etc/default/jenkins
```
add this at the end  `--httpListenAddress=127.0.0.1` \
<img src="https://github.com/Mxnxn/jenkins-reactjs-guide/blob/master/assets/jenkins_args.png" alt="drawing" width="900"/> 

Now, add a default-copy from `/etc/nginx/sites-available` to `/etc/nginx/sites-enabled` and run
```
sudo nano default_copy # or whatever you named it
```
it's `server { } ` should look like this
<img src="https://github.com/Mxnxn/jenkins-reactjs-guide/blob/master/assets/nginx_jenkins.png" alt="drawing" width="800"/> \
Now, run this to rename
```sudo mv default_copy jenkins.example.com # change your domain name instead example.com```
for checking syntax run
```
sudo nginx -t
```
if successful, run 
```
sudo systemctl restart nginx
```
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
