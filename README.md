# LAMMPS

## Building the container images
Clone this repo:
```
git clone https://github.com/alahiff/lammps.git
cd lammps
```
Build an image containing `lmp_serial` with OpenMP support:
```
docker build -f Dockerfile-serial -t alahiff/lammps-serial-omp:latest .
```
Build an image containing `lmp_mpi` with OpenMP support:
```
docker build -f Dockerfile-mpi -t alahiff/lammps-openmpi-omp:latest .
```
In the above of you should use your own Docker Hub user name of course. Then push to Docker Hub:
```
docker push alahiff/lammps-serial-omp:latest
docker push alahiff/lammps-openmpi-omp:latest
```

## Basic tests using Docker
Running the benchmarks using Docker as a quick test:
```
wget https://github.com/lammps/lammps/archive/stable_12Dec2018.tar.gz
tar xzf stable_12Dec2018.tar.gz
cd 
```
