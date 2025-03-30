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
