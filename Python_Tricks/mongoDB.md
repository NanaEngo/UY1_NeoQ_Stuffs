# MongoDB

## Installation on Linux

A complete documentataion can be found in [How to Install MongoDB on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-16-04)

## Installing MongoDB

Import the GPG signed keys to the official MongoDB repository:
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
```

Create a list file for MongoDB and update the packages list:
```
sudo echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
sudo apt-get update
```

Install MongoDB package:
```
sudo apt-get install -y --allow-unauthenticated mongodb-org
```

Create a configuration file named mongodb.service in the /etc/systemd/system directory using nano:
```
sudo nano /etc/systemd/system/mongodb.service
```
and paste the following:
```
[Unit]
Description=High-performance, schema-free document-oriented database
After=network.target

[Service]
User=mongodb
ExecStart=/usr/bin/mongod --quiet --config /etc/mongod.conf

[Install]
WantedBy=multi-user.target
```

Set MongoDB to start automatically as system starts:
```
sudo systemctl enable mongodb
```

## Starting MongoDB

To start MongoDB service:
```
sudo systemctl start mongodb
```

To view the status of MongoDB service:
```
sudo systemctl status mongodb
```
