FROM centos:7
RUN yum -y install wget \
                   gcc \
                   gcc-c++ \
                   make \
                   openmpi \
                   openmpi-devel \
                   openssh-clients \
                   bc

ENV PATH            /usr/lib64/openmpi/bin:${PATH}
ENV LD_LIBRARY_PATH /usr/lib64/openmpi/lib:${LD_LIBRARY_PATH}

WORKDIR /tmp
RUN wget https://github.com/lammps/lammps/archive/stable_12Dec2018.tar.gz && \
    tar xzvf stable_12Dec2018.tar.gz

WORKDIR /tmp/lammps-stable_12Dec2018/src
RUN make yes-standard no-lib no-ext yes-user-omp && \
    sed -i "/CCFLAGS =/c\CCFLAGS =       -g -O3 -fopenmp" /tmp/lammps-stable_12Dec2018/src/MAKE/Makefile.mpi && \ 
    sed -i "/LINKFLAGS =/c\LINKFLAGS =     -g -O -fopenmp" /tmp/lammps-stable_12Dec2018/src/MAKE/Makefile.mpi && \ 
    make mpi && \
    cp /tmp/lammps-stable_12Dec2018/src/lmp_mpi /usr/local/bin/ && \
    rm -f /tmp/stable_12Dec2018.tar.gz && \
    rm -rf /tmp/lammps-stable_12Dec2018
