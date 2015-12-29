Development environment deployment
==================================

###Full new environment
Which don't install package vagrant, virtualbox and don't check out code.   
**For linux** execute the following command:

```
sudo apt-get update
sudo apt-get -y install virtualbox vagrant git
vagrant box add -f sms http://192.168.1.247/dev/vagrant/sms.box
git clone http://121.42.165.131:8080/tfs/MarketPlace/_git/Code sms
cd sms
vagrant up
```

**For Windows**   
Download Software & Install & Restart System:   
<http://192.168.1.247/dev/soft/win/Git-1.9.5-preview20150319.exe>  
<http://192.168.1.247/dev/soft/win/VirtualBox-4.3.26-98988-Win.exe>   
<http://192.168.1.247/dev/soft/win/vagrant_1.7.2.msi>  

On D:\ Open the git bash shell via a right-click context menu (Git Bash Here).

```
git clone http://121.42.165.131:8080/tfs/MarketPlace/_git/Code sms
cd sms
vagrant up
```

###Exist environment
```
cd sms
git pull
vagrant box add -f sms http://192.168.1.247/dev/vagrant/sms.box
vagrant destroy -f
vagrant up
```

###Only run provision for small change
```
cd sms
vagrant reload --provision
```

###Request uri
<http://127.0.0.1:8080/>  
<http://127.0.0.1:8080/docs/>  
<http://127.0.0.1:8080/frontend/web/>   
<http://127.0.0.1:8080/backend/web/> 
<http://127.0.0.1:8080/rest/>     

###References
[Vagrant manual](https://docs.vagrantup.com/v2/)

SMS Restful
===========

###App get token
```
Url: http://127.0.0.1:8080/rest/oauth2/token
Method: POST
Payload:
{
    "client_id": "testclient",
    "client_secret": "testpass",
    "grant_type": "client_credentials"
}

```

###App get resource
Send token using query params

```
Url: http://127.0.0.1:8080/rest/v1/user?access_token=TOKEN
Method: GET
```
Send token using headers

```
Url: http://127.0.0.1:8080/rest/v1/user
Method: GET
Header: Authorization => Bearer TOKEN
```

#References
https://github.com/Filsh/yii2-oauth2-server   
https://github.com/bshaffer/oauth2-server-php   
http://bshaffer.github.io/oauth2-server-php-docs/   
http://www.ruanyifeng.com/blog/2014/05/oauth_2_0.html     


Resource
========
[Awesome PHP](https://github.com/ziadoz/awesome-php)   
[Guzzle HTTP](http://guzzle.readthedocs.org/en/5.3/clients.html)

tricks
======
#####1. Store git password
```
git config --global credential.helper store
``` 