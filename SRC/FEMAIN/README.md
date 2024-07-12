# Compilation on Perlmutter

To compile on Perlmutter (NERSC) follow the steps below
1. Add these modules and options in `~/.bash_profile`
```
module load PrgEnv-gnu/8.5.0
module load cudatoolkit/12.2
export MPICH_GPU_SUPPORT_ENABLED=0
```
2. Do 
```
source ~/.bash_profile
```

2. Do
```
make
```


