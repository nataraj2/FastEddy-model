# Compilation and running on Perlmutter GPUs

To compile on Perlmutter (NERSC) follow the steps below
1. Add these modules and options in `~/.bash_profile`
```
module load PrgEnv-gnu/8.5.0
module load cudatoolkit/12.2
export MPICH_GPU_SUPPORT_ENABLED=0
```
2. `source ~/.bash_profile`

3. `make`

4. `mkdir initial`

5. `mkdir output`

6. Download `Moist_BOMEX.tar.gz` from [Zenodo](https://zenodo.org/records/10982246)

7. ```
	tar xvf Moist_BOMEX.tar.gz
	cp Moist_BOMEX/BOMEX_IC/FE_BOMEX.0 initial
   ```
8. `salloc --nodes 1 --qos interactive --time 01:00:00 --constraint gpu --gpus 4 --account=xxxx`
    Replace `xxxx` with the account code. 

9. `srun -n 1 -G 4 FastEddy Example04_BOMEX.in`

