# react_vagrant_setup
This is repo with React default create-react-app running on Vagrant for dev/test purposes.

## Setup

Setup info:
- Windows 10 Home
- Oracle VM VirtualBox: 5.2.8 r121009 (Qt5.6.2)
- Vagrant: 2.2.4

## How to install? Easy step-by-step guide

1. **(Optional) Setup up vagrant**

Setup vagrant enviroment using Vagrantfile from repository. You can modify it according to needs. 
It contains basic node packages and nginx config.


2. **(Optional) Start a new project**

**Repo contains default create-react-app, but you may want to set up new project in it.**

Since I encountered various problem with symlinks while trying to setup projects by npm or yarn inside a vagrant, I advice 
to setup project with npm from Win10.

First delete current project by removing `app` directory.

Next install nodeJS from official website:
https://nodejs.org/en/

When it's done restart computer and test if it is installed properly:

```
$ node --version
v10.15.3

$ npm --version
6.4.1
```

Now install create-react-app package:

```
npm install -g create-react-app
```

Navigate into correct folder (I prefer the folder which will mount into `/vagrant` ) and use:

```
create-react-app app
```

Now `app` is a folder where app will be located (so now in Vagrant enviroment it will be `/vagrant/app` )



3. **Start development server**

Into the image navigate to app folder

```
cd /vagrant/app
```

and run

```
npm start
```


4. **Make build and run build server**

First you have to make a build. In the main app folder run'

```
npm run build
```

Now serve the build using pm2

```
pm2 serve build
```

Your server is running on `44.44.44.4:8080`, but nginx forward it to 80, which is default port for http access. 
Type `44.44.44.4` in browser window to connect to it.
