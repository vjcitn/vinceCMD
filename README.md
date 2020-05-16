# vinceCMD
VJC work on curatedMetagenomicData, following a link on "current approach", we'll assume XSEDE Jetstream TACC volume /vol_b is our basic write area -- 'RUN_PATH_IN_CONTAINER' should be given by Levi's group?

```
# vjc: from Usage at https://github.com/waldronlab/curatedMetagenomicDataHighLoad/tree/master/docker/curatedMetagenomics
docker run -v /vol_b/CMD:/RUN_PATH_IN_CONTAINER -ti waldronlab/curatedmetagenomics curatedMetagenomicData_pipeline.sh SAMPLENAME SRA_ACCESSION
# a runnable example, where big databases are stored on the host in `${HOME}/biobakery.db`, output goes to `/tmp/output`, and a small demo is run.
export DB_PATH="${HOME}/biobakery.db"; docker run -ti -e ncores=2 -e OUTPUT_PATH=/tmp/containeroutput -v "/tmp/output:/tmp/containeroutput" -v ${DB_PATH}/metaphlan:/usr/local/miniconda3/lib/python3.7/site-packages/metaphlan/metaphlan_databases -v ${DB_PATH}/humann:/usr/local/humann_databases waldronlab/curatedmetagenomics curatedMetagenomicData_pipeline.sh TEST_SAMPLE ERR262957 DEMO
```

running `/usr/local/bin/curatedMetagenomicData_pipeline.sh TEST_SAMPLE ERR262957` within the container includes a "building Bowtie2 indexes" step that takes a long time.  Can't this be factored out?

----
earlier comments

This didn't work:  retrieved following from https://github.com/waldronlab/curatedMetagenomicDataHighLoad

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
