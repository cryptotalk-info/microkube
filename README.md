# microkube

Server request Ubuntu 18.10 x64
Minimum for test 8G of RAM, SSD 120G, 4 CPUs

su - root

sudo apt update
sudo apt upgrade
sudo adduser app
sudo usermod -a -G sudo app

sudo apt install apt-transport-https ca-certificates curl software-properties-common
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu  $(lsb_release -cs)  stable"

sudo apt update

sudo apt install docker-ce
systemctl status docker

usermod -aG docker app

curl -L "https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose

su - app

sudo apt update
sudo apt upgrade

sudo apt-get install git curl zlib1g-dev build-essential \
   libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 \
   libxml2-dev libxslt1-dev libcurl4-openssl-dev libffi-dev

gpg --keyserver hkp://keys.gnupg.net \
    --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 \
    7D2BAF1CF37B13E2069D6956105BD0E739499BDB
    
\curl -sSL https://get.rvm.io | bash -s stable --ruby=2.6.0 --gems=rails
source /home/deploy/.rvm/scripts/rvm
rvm use 2.6.0

cd $HOME

git clone https://github.com/rubykube/microkube.git
cd microkube
bundle

cd config
sudo nano app.yml

Change images:
rubukube/peatio: 2.2.3 
rubukube/barong: 2.2.2	  
rubukube/mikroapp: 0.1.5  
rubukube/tower: 0.1.17
rubukube/arke: 0.1.10

rake -T
rake service:all

rake -T
rake vendor:clone

rake -T
rake render:config

cd
Folder microkube:
bundle
rake -T
rake render:config

You can login on www.app.local with the following default users from seeds.yaml

Seeded users:
Email: admin@barong.io, password: 0lDHd9ufs9t@
Email: john@barong.io, password: Am8icnzEI3d!
