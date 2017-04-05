# Dockerize Rails application

This repository is aimed at providing a docker based starter approach for setting up the development environment of rails application. 

The code related to docker (Dockerfile and docker-compose.yml) is complete and in place but this will require a lot of documentation to explain how things work. 

I have referred to docker hub pages of phpmyadmin, mysql and ruby as well docker-compose documentation to get things in place and working. 

Documentation coming soon. Hopefully :) 

# Docker Installation 

If you don't have docker installed already then :

```sh
curl -sSL https://get.docker.com/ | sh

# Replace <your_user> with your username 
sudo usermod -aG docker <your_user>
```
NOTE: Docker installation is done. You have to log out and in log to start using docker. 

After logging back in check if the following command is running successfully or not
```sh
docker run hello-world
```
If it does then your docker installation is done. 

# Starting your rails app. 

Please note that this is very basic documentation and it might not work for you.
```
git clone https://github.com/vik-y/dockerize_rails.git
cd dockerize_rails
touch Gemfile.lock
sudo apt-get install python-pip
sudo pip install docker-compose
docker-compose build
docker-compose run web bundle install
# This will take a while
```

Now your ruby on rails installation is done. 

TO initialize a new app do this: 
```sh
docker-compose run web rails new . --force --database=mysql
# This will init the rails app and install required gems.
```
You can run all the rake and rails command by just prepending 'docker-compose run web' to your command.
```sh
#Example:
# Create db: 
docker-compose run web rake db:create
# migrate
docker-compose run web rake db:migrate
```
Please note that you don't have to use 'rails s' command to run the server. Once your db create and migrate is done just do
```sh
docker-compose up 
```
to run your development web server. GO to localhost:3000 and you are done. 


More documentation to come later :)     
