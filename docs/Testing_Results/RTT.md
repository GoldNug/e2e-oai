## To successfully perform an RTT, ensure that all the initial setup steps have been performed.

Run OAI CN5G. The expected output can be viewed [here](https://github.com/GoldNug/e2e-oai/blob/2025-TEEP-9-Jason/docs/Testing_Results/Run%20CN5G.png)
```
cd ~/oai-cn5g
sudo docker-compose up -d
```

Run the OAI gNB RFsimulator (on another terminal). The expected output can be viewed [here](https://github.com/GoldNug/e2e-oai/blob/2025-TEEP-9-Jason/docs/Testing_Results/Run%20gnB.png)
```
cd ~/openairinterface5g/cmake_targets/ran_build/build
sudo ./nr-softmodem -O ../../../targets/PROJECTS/GENERIC-NR-5GC/CONF/gnb.sa.band78.fr1.106PRB.usrpb210.conf --gNBs.[0].min_rxtxtime 6 --rfsim
```

Run the OAI nrUE RFsimulator (on another terminal). The expected output can be viewed [here](https://github.com/GoldNug/e2e-oai/blob/2025-TEEP-9-Jason/docs/Testing_Results/Run%20nrUE.png)
```
cd ~/openairinterface5g/cmake_targets/ran_build/build
sudo ./nr-uesoftmodem -r 106 --numerology 1 --band 78 -C 3619200000 --uicc0.imsi 001010000000001 --rfsim
```

Perform an end to end connectivity test to validate (on another terminal). This test pings from the UE host to CN5G. The expected output can be viewed [here]()
```
ping 192.168.70.135 -I oaitun_ue1
```
