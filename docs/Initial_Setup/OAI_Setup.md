The general guideline for this documentation process can be found [here](https://gitlab.eurecom.fr/oai/openairinterface5g/-/tree/develop/doc)

# Setting up OAI CN5G
Install following pre-requisites

```
sudo apt install -y git net-tools putty

# https://docs.docker.com/engine/install/ubuntu/
sudo apt update
sudo apt install -y ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Add your username to the docker group, otherwise you will have to run in sudo mode.
sudo usermod -a -G docker $(whoami)
reboot
```

Download and copy configuration files
```
wget -O ~/oai-cn5g.zip https://gitlab.eurecom.fr/oai/openairinterface5g/-/archive/develop/openairinterface5g-develop.zip?path=doc/tutorial_resources/oai-cn5g
unzip ~/oai-cn5g.zip
mv ~/openairinterface5g-develop-doc-tutorial_resources-oai-cn5g/doc/tutorial_resources/oai-cn5g ~/oai-cn5g
rm -r ~/openairinterface5g-develop-doc-tutorial_resources-oai-cn5g ~/oai-cn5g.zip
```

Pull docker images
```
cd ~/oai-cn5g
docker compose pull
```

## Several Debugging Notes
For every docker command, the official documentation uses the modern command for pulling with the docker, ```dokcer compose```. If said format doesn't work, try the legacy command syntax instead, ```docker-compose```

There is also a possibiity that the ```docker-compose pull``` command doesn't work, as there could be permission issues. This issue might persist even after adding permission to the user. If such issues persist, use the sudo command for access.

Following the documentation, installing the UHD is a necessary process to allow wireless communication. However, building it is also necessary :
```
git clone --recursive https://github.com/EttusResearch/uhd.git
cd uhd
mkdir build
cd build
cmake ..
make -j$(nproc)
sudo make install
sudo ldconfig
```
