# Compilation and running on Perlmutter GPUs

1. Get FastEddy code from GitHub by
```git clone https://github.com/nataraj2/FastEddy-model.git
   cd FastEddy-model
   git checkout FE_perlmutter
```

2. `cd SRC/FEMAIN`

To compile on Perlmutter (NERSC) follow the steps below
3. Add these modules and options in `~/.bash_profile`
```
module load PrgEnv-gnu/8.5.0
module load cudatoolkit/12.2
export MPICH_GPU_SUPPORT_ENABLED=0
```
4. `source ~/.bash_profile`

5. `make`

6. `mkdir initial`

7. `mkdir output`

8. Download `Moist_BOMEX.tar.gz` from [Zenodo](https://zenodo.org/records/10982246)

9. ```
	tar xvf Moist_BOMEX.tar.gz
	cp Moist_BOMEX/BOMEX_IC/FE_BOMEX.0 initial
   ```
10. `salloc --nodes 1 --qos interactive --time 01:00:00 --constraint gpu --gpus 4 --account=xxxx`
    Replace `xxxx` with the account code. 

11. `srun -n 1 -G 4 FastEddy Example04_BOMEX.in`

