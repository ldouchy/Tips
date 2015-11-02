# Tips installation BXA on Docker


## start last version of multinest container with cli
sudo docker run -t -i multinest:latest /bin/bash

sudo docker run -i -t ubuntu:14.04 /bin/bash

# apt-get install -y aptitude
# aptitude install -y --without-recommends ubuntu-desktop
# apt-get install -y gnome-shell gnome-panel gnome-system-tools pm-utils


apt-get update

apt-get install vim
apt-get install -y libblas-dev liblapack-dev gfortran


apt-get install -y python-{scipy,numpy,matplotlib,progressbar} ipython libblas{3,-dev} liblapack{3,-dev} libatlas{3-base,-dev} cmake build-essential git gfortran r-base r-base-dev



apt-get install -y wget
wget https://gist.githubusercontent.com/JohannesBuchner/6579476/raw/2af7e0c6b719e768a0ef61cb3992f863f5fbb197/installMultiNest.sh

chmod u+x installMultiNest.sh 
./installMultiNest.sh 

### Not suported ! must export with every run...
# export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/MultiNest/lib
# echo -e "\nLD_LIBRARY_PATH=/opt/MultiNest/lib\nexport LD_LIBRARY_PATH" >> /etc/profile

export LD_LIBRARY_PATH=/opt/MultiNest/lib
export MULTINEST=/opt/MultiNest

# package install in R

R -e "install.packages('Rserve', repos='https://cran.rstudio.com/')"

apt-get update ; apt-get install -y libblas-dev liblapack-dev gfortran ; apt-get install -y python-{scipy,numpy,matplotlib,progressbar} ipython libblas{3,-dev} liblapack{3,-dev} libatlas{3-base,-dev} cmake build-essential git gfortran r-base r-base-dev ; apt-get install -y wget ; cd /opt ;  wget https://gist.githubusercontent.com/JohannesBuchner/6579476/raw/2af7e0c6b719e768a0ef61cb3992f863f5fbb197/installMultiNest.sh ; chmod u+x installMultiNest.sh


# Rserve hand compilation

cd /opt/RMultiNest/
wget http://www.rforge.net/Rserve/snapshot/Rserve_1.8-4.tar.gz
tar xzvf Rserve_1.8-4.tar.gz
./Rserve/configure
cd Rserve/clients/cxx/
./configure && make Rconnection.o
cd ../../../


