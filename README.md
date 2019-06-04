# LAMMPS

## Building the container images
_Note: this requires access to a machine with the Docker CLI available_

Clone this repo:
```
git clone https://github.com/alahiff/lammps.git
cd lammps
```
Build an image for `lmp_serial` with OpenMP support:
```
docker build -f Dockerfile-serial -t alahiff/lammps-serial-omp:latest .
```
Build an image for `lmp_mpi` with OpenMP support:
```
docker build -f Dockerfile-mpi -t alahiff/lammps-openmpi-omp:latest .
```
In the above of you should use your own Docker Hub user name of course. Then push to Docker Hub:
```
docker push alahiff/lammps-serial-omp:latest
docker push alahiff/lammps-openmpi-omp:latest
```

## Basic tests using Docker
_Note: this requires access to a machine with the Docker CLI available_

Running the benchmarks using Docker as a quick test:
```
wget https://github.com/lammps/lammps/archive/stable_12Dec2018.tar.gz
tar xzf stable_12Dec2018.tar.gz
cd lammps-stable_12Dec2018/bench
```
Any of the benchmark problems can now be run, for example LJ:
```
docker run -it --rm -v `pwd`:/work --workdir /work -e OMP_NUM_THREADS=2 alahiff/lammps-openmpi-omp:latest lmp_mpi -sf omp -in in.lj
```
or EAM:
```
docker run -it --rm -v `pwd`:/work --workdir /work -e OMP_NUM_THREADS=2 alahiff/lammps-openmpi-omp:latest lmp_mpi -sf omp -in in.eam
```

## Running using PROMINENCE


