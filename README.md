# vinceCMD
VJC work on curatedMetagenomicData, retrieved following from https://github.com/waldronlab/curatedMetagenomicDataHighLoad

5/16/2020 -- on TACC M1.large

```
#sudo apt-get install -y docker.io #install Docker if needed
docker pull stevetsa/curatedmetagenomicdatahighload
docker run -it stevetsa/curatedmetagenomicdatahighload

## mount the current directory in the container for debugging
#docker run -v `pwd`:`pwd` -w `pwd` -i -t stevetsa/curatedmetagenomicdatahighload

## Inside container - 
git clone https://github.com/stevetsa/curatedMetagenomicDataHighLoad.git
cd curatedMetagenomicDataHighLoad
bash setup.sh
bash curatedMetagenomicData_pipeline.sh MV_FEI4_t1Q14 "SRR4052038" 
```
