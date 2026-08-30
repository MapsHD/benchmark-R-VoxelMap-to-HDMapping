# R-VoxelMap to HDMapping simplified instruction

## Step 1 (prepare data)
Download the dataset `reg-1.bag` by clicking [link](https://cloud.cylab.be/public.php/dav/files/7PgyjbM2CBcakN5/reg-1.bag) (it is part of [Bunker DVI Dataset](https://charleshamesse.github.io/bunker-dvi-dataset)).

File 'reg-1.bag' is an input for further calculations.
It should be located in '~/hdmapping-benchmark/data'.


## Step 2 (prepare docker)
```shell
mkdir -p ~/hdmapping-benchmark
cd ~/hdmapping-benchmark
git clone https://github.com/marcinmatecki/benchmark-R-VoxelMap-to-HDMapping --recursive
cd benchmark-R-VoxelMap-to-HDMapping
git checkout Bunker-DVI-Dataset-reg-1
docker build -t r-voxelmap_noetic .
```

## Step 3 (run docker, file 'reg-1.bag' should be in '~/hdmapping-benchmark/data')
```shell
cd ~/hdmapping-benchmark/benchmark-R-VoxelMap-to-HDMapping
chmod +x docker_session_run-ros1-fast-lio.sh 
cd ~/hdmapping-benchmark/data
~/hdmapping-benchmark/benchmark-R-VoxelMap-to-HDMapping/docker_session_run-ros1-r-voxelmap.sh reg-1.bag .
```

## Step 4 (Open and visualize data)
Expected data should appear in ~/hdmapping-benchmark/data/output_hdmapping-r-voxelmap
Use tool [multi_view_tls_registration_step_2](https://github.com/marcinmatecki/HDMapping) to open session.json from ~/hdmapping-benchmark/data/output_hdmapping-r-voxelmap.

You should see following data in folder '~/hdmapping-benchmark/data/output_hdmapping-r-voxelmap'

lio_initial_poses.reg

poses.reg

scan_lio_*.laz

session.json

trajectory_lio_*.csv

Result(terminated approximately halfway through the sequence due to significant map drift.):

<img width="1428" height="736" alt="Screenshot from 2026-08-30 14-19-21" src="https://github.com/user-attachments/assets/3097200e-0267-4596-9bce-1ed17d1ff1d5" />

## Contact email
januszbedkowski@gmail.com
