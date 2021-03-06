# Copyright (C) 2016, 2017 by Maciej Serylak
# Copyright (C) 2019 by Maciej Serylak and Vivek Venkatraman Krishnan
# Copyright (C) 2020 by MS, VVK and Aditya Parthasarathy

# Licensed under the Academic Free License version 3.0
# This program comes with ABSOLUTELY NO WARRANTY.
# You are free to modify and redistribute this code as long
# as you do not remove the above attribution and reasonably
# inform receipients that you have modified the original work.


FROM ubuntu:bionic-20200112

MAINTAINER Aditya Parthasarathy "adityapartha3112@gmail.com"

# Suppress debconf warnings
ENV DEBIAN_FRONTEND noninteractive

# Switch account to root and adding user accounts and password
USER root
RUN echo "root:meerdock" | chpasswd

# Create psr user which will be used to run commands with reduced privileges.
RUN adduser --disabled-password --gecos 'unprivileged user' psr && \
    echo "psr:psr" | chpasswd && \
    mkdir -p /home/psr/.ssh && \
    chown -R psr:psr /home/psr/.ssh

# Create space for ssh deamozshn and update the system
RUN echo 'deb http://us.archive.ubuntu.com/ubuntu bionic main multiverse' >> /etc/apt/sources.list && \
echo 'deb http://mirrors.kernel.org/ubuntu/ bionic main multiverse' >> /etc/apt/sources.list && \
    mkdir /var/run/sshd && \
    apt-get -y check && \
    apt-get -y update && \
    apt-get install -y apt-utils apt-transport-https software-properties-common &&\
    apt-get -y update --fix-missing && \
    apt-get -y upgrade

RUN apt-get -y install \
    apt-utils \
    autoconf \
    automake \
    autotools-dev \
    binutils-dev \
    bison \
    build-essential \
    cmake \
    cmake-curses-gui \
    cmake-data \
    cpp \
    csh \
    curl \
    cvs \
    cython \
    dkms \
    dvipng \
    emacs\
    exuberant-ctags \
    f2c \
    fftw-dev \
    fftw2 \
    flex \
    fort77 \
    g++ \
    gawk \
    gcc \
    gfortran \
    ghostscript \
    ghostscript-x \
    git \
    git-core \
    gnuplot \
    gnuplot-x11 \
    gsl-bin \
    gv \
    h5utils \
    hdf5-helpers \
    hdf5-tools \
    hdfview \
    htop \
    hwloc \
    ipython \
    python3-notebook python-notebook jupyter jupyter-core python-ipykernel\
    libatlas-base-dev \
    libbison-dev \
    libblas-dev \
    liblapack-dev \
    libboost-all-dev \
    libc-dev-bin \
    libc6-dev \
    libcfitsio-bin \
    libcfitsio-dev \
    libcfitsio-doc \
    libcloog-isl4 \
    libcppunit-dev \
    libcppunit-subunit-dev \
    libcppunit-subunit0 \
    libfftw3-3 \
    libfftw3-bin \
    libfftw3-dbg \
    libfftw3-dev \
    libfftw3-double3 \
    libfftw3-long3 \
    libfftw3-quad3 \
    libfftw3-single3 \
    libfreetype6 \
    libfreetype6-dev \
    libgd-dev \
    libgd3 \
    libglib2.0-0 \
    libglib2.0-dev \
    libgmp3-dev \
    libgsl-dev \
    libgtksourceview-3.0-dev \
    libgtksourceview2.0-dev \
    libhdf5-dev \
    libhdf5-serial-dev \
    libhwloc-dev \
    liblapack-dev \
    liblapack-pic \
    liblapack-test \
    liblapack3 \
    liblapacke \
    liblapacke-dev \
    libltdl-dev \
    libltdl7 \
    liblua5.1-0 \
    liblua5.1-0-dev \
    liblua5.2-0 \
    liblua5.2-dev \
    liblua5.3-0 \
    liblua5.3-dev \
    libncurses5-dev \
    libntrack-qt4-1 \
    libopenblas-base \
    libopenblas-dev \
    libpng++-dev \
    libpng-sixlegs-java \
    libpng-sixlegs-java-doc \
    libpng-dev \
    libpnglite-dev \
    libpth-dev \
    libqt4-dbus \
    libqt4-declarative \
    libqt4-designer \
    libqt4-dev \
    libqt4-dev-bin \
    libqt4-help \
    libqt4-network \
    libqt4-opengl \
    libqt4-opengl-dev \
    libqt4-qt3support \
    libqt4-script \
    libqt4-scripttools \
    libqt4-sql \
    libqt4-sql-mysql \
    libqt4-svg \
    libqt4-test \
    libqt4-xml \
    libqt4-xmlpatterns \
    libreadline-dev \
    libsocket++-dev \
    libsocket++1 \
    libssl-dev \
    libtool \
    libx11-dev \
    llvm-4.0 \
    llvm-4.0-dev \
    llvm-4.0-doc \
    llvm-4.0-examples \
    llvm-4.0-runtime \
    locate \
    lsof \
    m4 \
    make \
    man \
    mc \
    nano \
    nfs-common \
    numactl \
    openssh-server \
    pbzip2 \
    pgplot5 \
    pkg-config \
    pyqt4-dev-tools \
    python \
    python-dev \
    python-pip \
    python-qt4 \
    python-qt4-dbus \
    python-qt4-dev \
    python-tk \
    qt4-default \
    qt4-linguist-tools \
    qt4-qmake \
    qt4-qtconfig \
    screen \
    source-highlight \
    subversion \
    swig \
    tcsh \
    tk \
    tk-dev \
    tmux \
    vim \
    wcslib-dev \
    wcslib-tools \
    wget \
    zlib1g-dev\
    zsh \
    libfontconfig1 \
    libfontconfig1-dev \
    htop \
    latex2html \
    libpng-dev \
    zlib1g-dev \
    software-properties-common \
    openjdk-8-jdk \
    python3

# Install python modules
RUN pip install pip -U && \
    pip install setuptools -U && \
    pip install datetime -U && \
    pip install bitstring -U && \
    pip install ipython -U && \
    pip install --ignore-installed jupyter -U && \
    pip install six -U && \
    pip install numpy -U && \
    pip install scipy -U && \
    pip install pandas -U && \
    pip install h5py -U && \
    pip install astropy -U && \
    pip install astroplan -U && \
    pip install astropy_helpers -U && \
    pip install astroquery -U && \
    pip install pytz -U && \
    pip install paramz -U && \
    pip install APLpy -U && \
    pip install pyfits -U && \
    pip install cycler -U && \
    pip install peakutils -U && \
    pip install matplotlib -U && \
    pip install seaborn -U && \
    pip install lmfit -U && \
    pip install pyephem -U && \
    pip install h5py -U && \
    pip install statsmodels -U && \
    pip install schwimmbad -U && \
    pip install ChainConsumer -U && \
    pip install setuptools_scm pep517 -U && \
    pip install emcee -U && \
    pip install scikit-learn -U && \
    pip install corner -U && \
    pip install bokeh -U && \ 
    pip install psrqpy -U \
    pip install webscreenshot -U
    

# Switch account to psr
USER psr

# Define home, psrhome, OSTYPE and create the directory
ENV HOME /home/psr
ENV PSRHOME /home/psr/software
ENV OSTYPE linux
RUN mkdir -p /home/psr/software

# Downloading all source codes
WORKDIR $PSRHOME
RUN wget --no-check-certificate https://www.imcce.fr/content/medias/recherche/equipes/asd/calceph/calceph-2.3.2.tar.gz && \
    tar -xvvf calceph-2.3.2.tar.gz -C $PSRHOME && \
    wget http://ds9.si.edu/download/ubuntu18/ds9.ubuntu18.8.0.1.tar.gz && \
    mkdir $PSRHOME/ds9-7.5 && \
    tar -xvvf ds9.ubuntu18.8.0.1.tar.gz -C $PSRHOME/ds9-7.5 && \
    wget http://heasarc.gsfc.nasa.gov/FTP/software/lheasoft/fv/fv5.4_pc_linux64.tar.gz && \
    tar -xvvf fv5.4_pc_linux64.tar.gz -C $PSRHOME && \
    wget http://www.atnf.csiro.au/people/pulsar/psrcat/downloads/psrcat_pkg.tar.gz && \
    tar -xvf psrcat_pkg.tar.gz -C $PSRHOME && \
    wget http://www.iausofa.org/2017_0420_C/sofa_c-20170420.tar.gz && \
    tar -xvvf sofa_c-20170420.tar.gz && \
    wget http://www.iausofa.org/2017_0420_F/sofa_f-20170420.tar.gz && \
    tar -xvvf sofa_f-20170420.tar.gz && \
    wget http://www.hdfgroup.org/ftp/lib-external/szip/2.1.1/src/szip-2.1.1.tar.gz && \
    tar -xvvf szip-2.1.1.tar.gz && \
    wget https://www.hdfgroup.org/ftp/HDF5/tools/h5check/src/h5check-2.0.1.tar.gz && \
    tar -xvvf h5check-2.0.1.tar.gz && \
    wget -U 'Linux' https://bsdforge.com/projects/devel/clig/src/clig-1.9.11.2.tar.xz && \
    tar -xvvf clig-1.9.11.2.tar.xz && \
    wget http://www.bastoul.net/cloog/pages/download/cloog-0.18.4.tar.gz && \
    tar -xvvf cloog-0.18.4.tar.gz && \
    wget http://prdownloads.sourceforge.net/ctags/ctags-5.8.tar.gz && \
    tar -xvvf ctags-5.8.tar.gz && \
    wget http://downloads.sourceforge.net/project/geographiclib/distrib/GeographicLib-1.48.tar.gz && \
    tar -xvvf GeographicLib-1.48.tar.gz && \
    wget http://www.hdfgroup.org/ftp/HDF5/projects/jpss/h5edit/h5edit-1.3.1.tar.gz && \
    tar -xvvf h5edit-1.3.1.tar.gz && \
    wget http://www.leptonica.org/source/leptonica-1.79.0.tar.gz && \
    tar -xvvf leptonica-1.79.0.tar.gz && \
    wget http://downloads.sourceforge.net/project/tvmet/Tar.Gz_Bz2%20Archive/1.7.2/tvmet-1.7.2.tar.bz2 && \
    tar -xvvf tvmet-1.7.2.tar.bz2 && \
    wget http://www.fftw.org/fftw-2.1.5.tar.gz && \
    tar -xvvf fftw-2.1.5.tar.gz && \
    wget http://heasarc.gsfc.nasa.gov/docs/software/ftools/fitsverify/fitsverify-4.18.tar.gz && \
    tar -xvvf fitsverify-4.18.tar.gz && \
    wget http://bitbucket.org/eigen/eigen/get/3.3.4.tar.bz2 && \
    tar -xvvf 3.3.4.tar.bz2 && \
    wget http://downloads.sourceforge.net/project/healpix/Healpix_3.31/Healpix_3.31_2016Aug26.tar.gz && \
    tar -xvvf Healpix_3.31_2016Aug26.tar.gz && \
    git clone https://github.com/SixByNine/psrxml.git && \
    git clone https://bitbucket.org/psrsoft/tempo2.git && \
    git clone https://git.code.sf.net/p/tempo/tempo && \
    git clone https://git.code.sf.net/p/psrchive/code psrchive && \
    git clone https://github.com/SixByNine/sigproc.git && \
    git clone https://github.com/ewanbarr/sigpyproc.git && \
    git clone https://github.com/nextgen-astrodata/DAL.git && \
    git clone https://git.code.sf.net/p/dspsr/code dspsr && \
    git clone https://github.com/weltevrede/psrsalsa.git && \
    git clone https://github.com/scottransom/presto.git && \
    git clone https://github.com/scottransom/psrfits2psrfits.git && \
    git clone https://github.com/scottransom/psrfits_utils.git && \
    git clone https://github.com/scottransom/pyslalib.git && \
    git clone https://github.com/mserylak/coast_guard.git && \
    git clone https://github.com/ajameson/pfits.git && \
    git clone git://git.code.sf.net/p/psrdada/code && \
    git clone https://github.com/straten/epsic.git && \
    git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto" && \
    wget https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-1.9.8-linux-x86_64.tar.bz2 && \
    tar -xvvf phantomjs-1.9.8-linux-x86_64.tar.bz2    


# PGPLOT
ENV PGPLOT_DIR="/usr/lib/pgplot5" \
    PGPLOT_FONT="/usr/lib/pgplot5/grfont.dat" \
    PGPLOT_INCLUDES="/usr/include" \
    PGPLOT_BACKGROUND="white" \
    PGPLOT_FOREGROUND="black" \
    PGPLOT_DEV="/xs"

# calceph
ENV CALCEPH=$PSRHOME"/calceph-2.3.2" \
    PATH=$PATH:$PSRHOME"/calceph-2.3.2/install/bin" \
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PSRHOME"/calceph-2.3.2/install/lib" \
    C_INCLUDE_PATH=$C_INCLUDE_PATH:$PSRHOME"/calceph-2.3.2/install/include"
WORKDIR $CALCEPH
RUN ./configure --prefix=$CALCEPH/install --with-pic --enable-shared --enable-static --enable-fortran --enable-thread && \
    make && \
    make check && \
    make install

# ds9
ENV PATH $PATH:$PSRHOME/ds9-7.5

# fv
ENV PATH $PATH:$PSRHOME/fv5.4

# psrcat
ENV PSRCAT_FILE=$PSRHOME"/psrcat_tar/psrcat.db" \
    PATH=$PATH:$PSRHOME"/psrcat_tar"
WORKDIR $PSRHOME/psrcat_tar
RUN /bin/bash makeit

# psrXML
ENV PSRXML=$PSRHOME"/psrxml" \
    PATH=$PATH:$PSRHOME"/psrxml/install/bin" \
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PSRHOME"/psrxml/install/lib" \
    C_INCLUDE_PATH=$C_INCLUDE_PATH:$PSRHOME"/psrxml/install/include"
WORKDIR $PSRXML
RUN autoreconf --install --warnings=none
RUN ./configure --prefix=$PSRXML/install && \
    make && \
    make install

# tempo
ENV TEMPO=$PSRHOME"/tempo" \
    PATH=$PATH:$PSRHOME"/tempo/bin"
WORKDIR $PSRHOME/tempo
RUN ./prepare && \
    ./configure --prefix=$PSRHOME/tempo && \
    make && \
    make install

# tempo2
ENV TEMPO2=$PSRHOME"/tempo2/T2runtime" \
    PATH=$PATH:$PSRHOME"/tempo2/T2runtime/bin" \
    C_INCLUDE_PATH=$C_INCLUDE_PATH:$PSRHOME"/tempo2/T2runtime/include" \
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PSRHOME"/tempo2/T2runtime/lib"
WORKDIR $PSRHOME/tempo2
# A fix to get rid of: returned a non-zero code: 126.
RUN sync && perl -pi -e 's/chmod \+x/#chmod +x/' bootstrap
RUN ./bootstrap && \
    ./configure --x-libraries=/usr/lib/x86_64-linux-gnu --with-calceph=$CALCEPH/install/lib --enable-shared --enable-static --with-pic F77=gfortran CPPFLAGS="$CPPFLAGS -I"$CALCEPH"/install/include" LDFLAGS="-L"$CALCEPH"/install/lib" && \
    make -j $(nproc) && \
    make install && \
    make plugins-install
WORKDIR $PSRHOME/tempo2/T2runtime/clock
RUN touch meerkat2gps.clk && \
    echo "# UTC(meerkat) UTC(GPS)" > meerkat2gps.clk && \
    echo "#" >> meerkat2gps.clk && \
    echo "50155.00000 0.0" >> meerkat2gps.clk && \
    echo "58000.00000 0.0" >> meerkat2gps.clk


ENV EPSIC=$PSRHOME"/epsic"
WORKDIR $EPSIC/src

RUN ./bootstrap && \
    ./configure --prefix=$PSRHOME"/epsic/install" && make -j $(nproc) && make &&  make install > test

ENV LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PSRHOME"/epsic/install/lib" \
    C_INCLUDE_PATH=$C_INCLUDE_PATH:$PSRHOME"/epsic/install/include/epsic" \
    PATH=$PATH:$PSRHOME"/epsic/install/bin" \
    CPPFLAGS="-I ${PSRHOME}/epsic/install/include/epsic"  \  
    CFLAGS="-I ${PSRHOME}/epsic/install/include/epsic" 

# PSRCHIVE
ENV PSRCHIVE=$PSRHOME"/psrchive/install" \
    PATH=$PATH:$PSRHOME"/psrchive/install/bin" \
    C_INCLUDE_PATH=$C_INCLUDE_PATH:$PSRHOME"/psrchive/install/include" \
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PSRHOME"/psrchive/install/lib" \
    PYTHONPATH=$PYTHONPATH:$PSRHOME"/psrchive/install/lib/python2.7/site-packages"

WORKDIR $PSRHOME/psrchive/

RUN ./bootstrap && \
    ./configure --prefix=$PSRCHIVE --x-libraries=/usr/lib/x86_64-linux-gnu --with-psrxml-dir=$PSRXML/install --enable-shared --enable-static F77=gfortran LDFLAGS="-L"$PSRXML"/install/lib" LIBS="-lpsrxml -lxml2" && \
    make -j $(nproc) && \
    make install 

WORKDIR $HOME
RUN $PSRCHIVE/bin/psrchive_config >> .psrchive.cfg && \
    sed -i 's/# ArrivalTime::default_format = Parkes/ArrivalTime::default_format = Tempo2/g' .psrchive.cfg && \
    sed -i 's/# Predictor::default = polyco/Predictor::default = tempo2/g' .psrchive.cfg && \
    sed -i 's/# Predictor::policy = ephem/Predictor::policy = default/g' .psrchive.cfg && \
    sed -i 's/# WeightedFrequency::round_to_kHz = 1/WeightedFrequency::round_to_kHz = 0/g' .psrchive.cfg


# SIGPROC
ENV SIGPROC=$PSRHOME"/sigproc" \
    PATH=$PATH:$SIGPROC"/install/bin" \
    FC="gfortran" \
    F77="gfortran" \
    CC="gcc" \
    CXX="g++"
WORKDIR $SIGPROC
RUN ./bootstrap && \
    ./configure --prefix=$SIGPROC/install --x-libraries=/usr/lib/x86_64-linux-gnu --enable-shared LDFLAGS="-L"$TEMPO2"/lib" LIBS="-ltempo2" && \
    make && \
    make install

# sigpyproc
ENV SIGPYPROC=$PSRHOME"/sigpyproc" \
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PSRHOME"/sigpyproc/lib/c"
WORKDIR $PSRHOME/sigpyproc
RUN python setup.py install --record list.txt --user


ENV PSRDADA=$PSRHOME"/psrdada" \
    PATH=$PATH:$PSRHOME"/psrdada/install/bin" \
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PSRHOME"/psrdada/install/lib" \
    C_INCLUDE_PATH=$C_INCLUDE_PATH:$PSRHOME"/psrdada/install/include" \
    CPPFLAGS="$CPPFLAGS -I ${PSRHOME}/psrdada/install/include -I ${PSRHOME}/epsic/install/include/epsic"  \
    CFLAGS="$CFLAGS -I ${PSRHOME}/psrdada/install/include -I ${PSRHOME}/epsic/install/include/epsic" 

# DAL
ENV DAL=$PSRHOME"/DAL" \
    PATH=$PATH:$PSRHOME/DAL"/install/bin" \
    C_INCLUDE_PATH=$C_INCLUDE_PATH:$PSRHOME/DAL"/install/include" \
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PSRHOME/DAL"/install/lib"
WORKDIR $DAL
RUN mkdir build
WORKDIR $DAL/build
RUN cmake .. -DCMAKE_INSTALL_PREFIX=$DAL/install && \
    make -j $(nproc) && \
    make && \
    make install


ENV PSRDADA=$PSRHOME"/psrdada" \
    PATH=$PATH:$PSRHOME"/psrdada/install/bin" \
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PSRHOME"/psrdada/install/lib" \
    C_INCLUDE_PATH=$C_INCLUDE_PATH:$PSRHOME"/psrdada/install/include" \
    CPPFLAGS="$CPPFLAGS -I ${PSRHOME}/psrdada/install/include -I ${PSRHOME}/epsic/install/include/epsic"  \
    CFLAGS="$CFLAGS -I ${PSRHOME}/psrdada/install/include -I ${PSRHOME}/epsic/install/include/epsic"

#psrdada
RUN     mv $PSRHOME/code $PSRDADA
WORKDIR $PSRDADA
RUN ./bootstrap && ./configure --prefix=$PSRDADA/install --enable-shared && \
        make -j $(nproc) &&\
        make &&\
        make install

ENV PATH=$PATH:"$PSRDADA/install/bin"

# DSPSR
ENV DSPSR=$PSRHOME"/dspsr" \
    PATH=$PATH:$PSRHOME"/dspsr/install/bin" \
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PSRHOME"/dspsr/install/lib" \
    C_INCLUDE_PATH=$C_INCLUDE_PATH:$PSRHOME"/dspsr/install/include"

WORKDIR $DSPSR
RUN ./bootstrap && \
    echo "apsr asp bcpm bpsr caspsr cpsr cpsr2 dada dummy fits kat lbadr lbadr64 lofar_dal lump lwa puma2 sigproc ska1" > backends.list && \
    ./configure --prefix=$DSPSR/install --x-libraries=/usr/lib/x86_64-linux-gnu CPPFLAGS="$CPPFLAGS -I"$DAL"/install/include -I/usr/include/hdf5/serial -I/usr/local/cuda/include -I"$PSRXML"/install/include" LDFLAGS="-L"$DAL"/install/lib -L/usr/lib/x86_64-linux-gnu/hdf5/serial -L"$PSRXML"/install/lib -L/usr/local/cuda/lib64" LIBS="-lpgplot -lcpgplot -lpsrxml -lxml2" && \
    make -j $(nproc) && \
    make && \
    make install

# FFTW2
ENV FFTW2=$PSRHOME"/fftw-2.1.5" \
    C_INCLUDE_PATH=$C_INCLUDE_PATH:$PSRHOME"/fftw-2.1.5/install/include" \
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PSRHOME"/fftw-2.1.5/install/lib"
WORKDIR $FFTW2
RUN ./configure --prefix=$FFTW2/install --enable-threads --enable-float && \
    make -j $(nproc) && \
    make && \
    make install

# fitsverify
ENV FITSVERIFY=$PSRHOME"/fitsverify" \
    PATH=$PATH:$PSRHOME"/fitsverify"
WORKDIR $FITSVERIFY
RUN gcc -o fitsverify ftverify.c fvrf_data.c fvrf_file.c fvrf_head.c fvrf_key.c fvrf_misc.c -DSTANDALONE -I/usr/include -L/usr/lib/x86_64-linux-gnu -lcfitsio -lm -lnsl

# PSRSALSA
ENV PSRSALSA=$PSRHOME"/psrsalsa" \
    PATH=$PATH:$PSRHOME"/psrsalsa/bin" \
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PSRHOME"/psrsalsa/src/lib"
WORKDIR $PSRSALSA
RUN sed -i.backup -e's/GSLFLAGS =.*/GSLFLAGS = -DGSL_VERSION_NUMBER=203/' Makefile && \
    make -j $(nproc) && \
    make

# PRESTO
ENV PRESTO=$PSRHOME"/presto" \
    PATH=$PATH:$PSRHOME"/presto/bin" \
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PSRHOME"/presto/lib" \
    PYTHONPATH=$PYTHONPATH:$PSRHOME"/presto/lib/python"
WORKDIR $PRESTO/src
#RUN make makewisdom
RUN make prep && \
    make -j $(nproc) && \
    make && \
    make mpi
WORKDIR $PRESTO
RUN pip install .

# psrfits2psrfits
ENV PSRFITS2PSRFITS=$PSRHOME"/psrfits2psrfits" \
    PATH=$PATH:$PSRHOME"/psrfits2psrfits"
WORKDIR $PSRFITS2PSRFITS
RUN make -j $(nproc) && \
    make

# psrfits_utils
ENV PSRFITS_UTILS=$PSRHOME"/psrfits_utils" \
    PATH=$PATH:$PSRHOME"/psrfits_utils/install/bin" \
    C_INCLUDE_PATH=$C_INCLUDE_PATH:$PSRHOME"/psrfits_utils/install/include" \
    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$PSRHOME"/psrfits_utils/install/lib"
WORKDIR $PSRFITS_UTILS
RUN sed -i 's|-Werror foreign|-Werror foreign -Wno-extra-portability|g' configure.ac && \
    ./prepare && \
    ./configure --prefix=$PSRFITS_UTILS/install && \
    make -j $(nproc) && \
    make && \
    make install

# coast_guard
ENV COAST_GUARD=$PSRHOME"/coast_guard" \
    PATH=$PATH:$PSRHOME"/coast_guard":$PSRHOME"/coast_guard/coast_guard" \
    COASTGUARD_CFG=$PSRHOME"/coast_guard/configurations" \
    PYTHONPATH=$PYTHONPATH:$PSRHOME"/coast_guard":$PSRHOME"/coast_guard/coast_guard"

#pfits
ENV PFITS=$PSRHOME"/pfits"  
WORKDIR $PFITS
RUN ./bootstrap && ./configure --prefix="$PFITS/install" && \
    make  -j $(nproc) && \
    make && \
    make install

ENV PATH=$PATH:"$PFITS/install/bin"


#Zsh commands
#RUN zsh -c 'git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"' && \
#zsh -c 'setopt EXTENDED_GLOB && for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do \
#ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}" \
#done '

#RUN chsh -s /bin/zsh
#ADD ./.zpreztorc /home/psr/

RUN curl -L https://iterm2.com/shell_integration/zsh -o ~/.iterm2_shell_integration.zsh && \
curl -L https://iterm2.com/shell_integration/install_shell_integration_and_utilities.sh | bash

# Clean downloaded source codes
WORKDIR $PSRHOME
RUN rm -rf ./*.bz2 ./*.gz ./*.xz ./*.ztar ./*.zip

# Installing a nice vimrc file
WORKDIR $PSRHOME
RUN git clone --depth=1 https://github.com/aparthas3112/vimrc.git ~/.vim_runtime
RUN sh ~/.vim_runtime/install_awesome_vimrc.sh 


#Installing bokeh sampledata
WORKDIR $PSRHOME
RUN bokeh sampledata

#Creating a directory for custom TPA installs
WORKDIR $HOME
RUN mkdir TPA
WORKDIR $HOME/TPA
RUN git clone https://github.com/aparthas3112/TPA_Classifier.git 

#Installing a few other packages
USER root
RUN apt-get -y install \
libopenblas-base \
libopenblas-dev \
pax-utils 

#Installing TempoNest and related dependencies
USER psr
WORKDIR $PSRHOME
RUN git clone https://github.com/JohannesBuchner/MultiNest
WORKDIR $PSRHOME/MultiNest/build
RUN cmake ..
RUN make
WORKDIR $PSRHOME/MultiNest/lib
RUN ln -s libmultinest_mpi.so libnest3.so

ENV LD_LIBRARY_PATH=$LD_LIBRARY_PATH:"$PSRHOME/MultiNest/lib" \
    CFLAGS="$CFLAGS -I$PSRHOME/MultiNest/include" \
    CPPFLAGS="$CPPFLAGS -I$PSRHOME/MultiNest/include" \ 
    MULTINEST_DIR="$PSRHOME/MultiNest/lib"
ENV LD_LIBRARY_PATH=$LD_LIBRARY_PATH:"/usr/lib/x86_64-linux-gnu/openmpi/lib/"

WORKDIR $PSRHOME
RUN git clone https://github.com/aparthas3112/TempoNest.git 
WORKDIR $PSRHOME/TempoNest/PolyChord
RUN make
RUN mv src/libchord.a $PSRHOME/MultiNest/lib/

WORKDIR $PSRHOME/TempoNest
RUN chmod +x autogen.sh
RUN ./autogen.sh
RUN ./configure --prefix=$PSRHOME/TempoNest 
RUN make temponest
RUN make temponest-install

#Cloning and installing libstempo
USER root
WORKDIR $PSRHOME
RUN git clone https://github.com/vallis/libstempo.git
WORKDIR $PSRHOME/libstempo
RUN python setup.py install

#Linking phantomjs to /usr/local/share
USER root
RUN mv $PSRHOME/phantomjs-1.9.8-linux-x86_64 /usr/local/share
RUN ln -sf /usr/local/share/phantomjs-1.9.8-linux-x86_64/bin/phantomjs /usr/local/bin

#Installing selenium and google-chrome-stable
RUN pip install selenium -U
WORKDIR $PSRHOME
RUN wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
RUN dpkg -i --force-depends google-chrome-stable_current_amd64.deb
RUN wget https://chromedriver.storage.googleapis.com/2.41/chromedriver_linux64.zip
RUN unzip chromedriver_linux64.zip
RUN mv chromedriver /usr/bin/chromedriver
RUN chown root:root /usr/bin/chromedriver
RUN chmod +x /usr/bin/chromedriver

# Put in file with all environmental variables
WORKDIR $HOME
RUN echo "" >> .bashrc && \
    echo "if [ -e \$HOME/.mysetenv.bash ]; then" >> .bashrc && \
    echo "   source \$HOME/.mysetenv.bash" >> .bashrc && \
    echo "fi" >> .bashrc && \
    echo "" >> .bashrc && \
    echo "alias rm='rm -i'" >> .bashrc && \
    echo "alias mv='mv -i'" >> .bashrc && \
    echo "# Set up PS1" >> .mysetenv.bash && \
    echo "export PS1=\"\u@\h [\$(date +%d\ %b\ %Y\ %H:%M)] \w> \"" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# Define home, psrhome, software, OSTYPE" >> .mysetenv.bash && \
    echo "export HOME=/home/psr" >> .mysetenv.bash && \
    echo "export PSRHOME=/home/psr/software" >> .mysetenv.bash && \
    echo "export OSTYPE=linux" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# Up arrow search" >> .mysetenv.bash && \
    echo "export HISTFILE=\$HOME/.bash_eternal_history" >> .mysetenv.bash && \
    echo "export HISTFILESIZE=" >> .mysetenv.bash && \
    echo "export HISTSIZE=" >> .mysetenv.bash && \
    echo "export HISTCONTROL=ignoreboth" >> .mysetenv.bash && \
    echo "export HISTIGNORE=\"l:ll:lt:ls:bg:fg:mc:history::ls -lah:..:ls -l;ls -lh;lt;la\"" >> .mysetenv.bash && \
    echo "export HISTTIMEFORMAT=\"%F %T \"" >> .mysetenv.bash && \
    echo "export PROMPT_COMMAND=\"history -a\"" >> .mysetenv.bash && \
    echo "bind '\"\e[A\":history-search-backward'" >> .mysetenv.bash && \
    echo "bind '\"\e[B\":history-search-forward'" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# PGPLOT" >> .mysetenv.bash && \
    echo "export PGPLOT_DIR=/usr/lib/pgplot5" >> .mysetenv.bash && \
    echo "export PGPLOT_FONT=/usr/lib/pgplot5/grfont.dat" >> .mysetenv.bash && \
    echo "export PGPLOT_INCLUDES=/usr/include" >> .mysetenv.bash && \
    echo "export PGPLOT_BACKGROUND=white" >> .mysetenv.bash && \
    echo "export PGPLOT_FOREGROUND=black" >> .mysetenv.bash && \
    echo "export PGPLOT_DEV=/xs" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# calceph" >> .mysetenv.bash && \
    echo "export CALCEPH=\$PSRHOME/calceph-2.3.2" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$CALCEPH/install/bin" >> .mysetenv.bash && \
    echo "export LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:\$CALCEPH/install/lib" >> .mysetenv.bash && \
    echo "export C_INCLUDE_PATH=\$C_INCLUDE_PATH:\$CALCEPH/install/include" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# ds9" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$PSRHOME/ds9-7.5" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# fv" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$PSRHOME/fv5.4" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# psrcat" >> .mysetenv.bash && \
    echo "export PSRCAT_FILE=\$PSRHOME/psrcat_tar/psrcat.db" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$PSRHOME/psrcat_tar" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# psrXML" >> .mysetenv.bash && \
    echo "export PSRXML=\$PSRHOME/psrxml" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$PSRXML/install/bin" >> .mysetenv.bash && \
    echo "export LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:\$PSRXML/install/lib" >> .mysetenv.bash && \
    echo "export C_INCLUDE_PATH=\$C_INCLUDE_PATH:\$PSRXML/install/include" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# tempo" >> .mysetenv.bash && \
    echo "export TEMPO=\$PSRHOME/tempo" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$TEMPO/bin" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# tempo2" >> .mysetenv.bash && \
    echo "export TEMPO2=\$PSRHOME/tempo2/T2runtime" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$TEMPO2/bin" >> .mysetenv.bash && \
    echo "export C_INCLUDE_PATH=\$C_INCLUDE_PATH:\$TEMPO2/include" >> .mysetenv.bash && \
    echo "export LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:\$TEMPO2/lib" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# PSRCHIVE" >> .mysetenv.bash && \
    echo "export PSRCHIVE=\$PSRHOME/psrchive/install" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$PSRCHIVE/bin" >> .mysetenv.bash && \
    echo "export C_INCLUDE_PATH=\$C_INCLUDE_PATH:\$PSRCHIVE/include" >> .mysetenv.bash && \
    echo "export LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:\$PSRCHIVE/lib" >> .mysetenv.bash && \
    echo "export PYTHONPATH=\$PYTHONPATH:\$PSRCHIVE/lib/python2.7/site-packages" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# SIGPROC" >> .mysetenv.bash && \
    echo "export SIGPROC=\$PSRHOME/sigproc" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$SIGPROC/install/bin" >> .mysetenv.bash && \
    echo "export FC=gfortran" >> .mysetenv.bash && \
    echo "export F77=gfortran" >> .mysetenv.bash && \
    echo "export CC=gcc" >> .mysetenv.bash && \
    echo "export CXX=g++" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# sigpyproc" >> .mysetenv.bash && \
    echo "export SIGPYPROC=\$PSRHOME/sigpyproc" >> .mysetenv.bash && \
    echo "export LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:\$SIGPYPROC/lib/c" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# DSPSR" >> .mysetenv.bash && \
    echo "export DSPSR=\$PSRHOME/dspsr" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$DSPSR/install/bin" >> .mysetenv.bash && \
    echo "export LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:\$DSPSR/install/lib" >> .mysetenv.bash && \
    echo "export C_INCLUDE_PATH=\$C_INCLUDE_PATH:\$DSPSR/install/include" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# FFTW2" >> .mysetenv.bash && \
    echo "export FFTW2=\$PSRHOME/fftw-2.1.5" >> .mysetenv.bash && \
    echo "export C_INCLUDE_PATH=\$C_INCLUDE_PATH:\$FFTW2/install/include" >> .mysetenv.bash && \
    echo "export LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:\$FFTW2/install/lib" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# fitsverify" >> .mysetenv.bash && \
    echo "export FITSVERIFY=\$PSRHOME/fitsverify" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$FITSVERIFY" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# PSRSALSA" >> .mysetenv.bash && \
    echo "export PSRSALSA=\$PSRHOME/psrsalsa" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$PSRSALSA/bin" >> .mysetenv.bash && \
    echo "export LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:\$PSRSALSA/src/lib" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# PRESTO" >> .mysetenv.bash && \
    echo "export PRESTO=\$PSRHOME/presto" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$PRESTO/bin" >> .mysetenv.bash && \
    echo "export LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:\$PRESTO/lib" >> .mysetenv.bash && \
    echo "export PYTHONPATH=\$PYTHONPATH:\$PRESTO/lib/python" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# psrfits2psrfits" >> .mysetenv.bash && \
    echo "export PSRFITS2PSRFITS=\$PSRHOME/psrfits2psrfits" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$PSRFITS2PSRFITS" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# psrfits_utils" >> .mysetenv.bash && \
    echo "export PSRFITS_UTILS=\$PSRHOME/psrfits_utils" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$PSRFITS_UTILS/install/bin" >> .mysetenv.bash && \
    echo "export C_INCLUDE_PATH=\$C_INCLUDE_PATH:\$PSRFITS_UTILS/install/include" >> .mysetenv.bash && \
    echo "export LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:\$PSRFITS_UTILS/install/lib" >> .mysetenv.bash && \
    echo "" >> .mysetenv.bash && \
    echo "# coast_guard" >> .mysetenv.bash && \
    echo "export COAST_GUARD=\$PSRHOME/coast_guard" >> .mysetenv.bash && \
    echo "export PATH=\$PATH:\$COAST_GUARD:\$COAST_GUARD/coast_guard" >> .mysetenv.bash && \
    echo "export COASTGUARD_CFG=\$COAST_GUARD/configurations" >> .mysetenv.bash && \
    echo "export PYTHONPATH=\$PYTHONPATH:\$COAST_GUARD:\$COAST_GUARD/coast_guard" >> .mysetenv.bash && \
    echo "# TempoNest" >> .mysetenv.bash && \
    echo "export LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:/home/psr/software/MultiNest/lib" >> .mysetenv.bash && \ 
    echo "export CFLAGS=\$CFLAGS:\$PSRHOME/MultiNest/include" >> .mysetenv.bash && \
    echo "export CPPFLAGS=\$CPPFLAGS:\$PSRHOME/MultiNest/include" >> .mysetenv.bash && \
    echo "export MULTINEST_DIR=\$PSRHOME/MultiNest/lib" >> .mysetenv.bash && \
    echo "export LD_LIBRARY_PATH=\$LD_LIBRARY_PATH:/usr/lib/x86_64-linux-gnu/openmpi/lib/" >> .mysetenv.bash && \
    /bin/bash -c "source $HOME/.bashrc"

# Update database for locate and run sshd server and expose port 22
USER root
RUN sed 's/X11Forwarding yes/X11Forwarding yes\nX11UseLocalhost no/' -i /etc/ssh/sshd_config
RUN updatedb
EXPOSE 22
EXPOSE 5006
EXPOSE 5007
EXPOSE 5008
EXPOSE 5009
CMD ["/usr/sbin/sshd", "-D"]
