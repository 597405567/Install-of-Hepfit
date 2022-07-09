# Install-of-Hepfit
###################################################
配置环境的安装：  

BAT:
软件可以通过命令自动安装  

root:
要求版本大于5  

GSL:
要求GSL版本大于1.16  

`wget https://mirrors.sjtug.sjtu.edu.cn/gnu/gsl/gsl-2.7.1.tar.gz`  
`tar -zxvf gsl-2.7.1.tar.gz`  
`cd gsl-2.7.1`  
`./configure`  
`make`  
`make install`  

boost:  
不需要安装，只需要下载并解压  
`https://www.boost.org/users/download/`  

MPI:  
`wget http://www.mpich.org/static/downloads/3.3.2/mpich-3.3.2.tar.gz`   
`tar -zxvf mpich-3.3.2.tar.gz`  
`cd mpich-3.3.2`   
`./configure  --prefix=/usr/local/mpich-3.3.2`   
`make`   
`make install`   
`vim ~/.bashrc`  
`export PATH="/usr/local/mpich-3.3.2/bin:$PATH"`  
`source ~/.bashrc`   
`which mpicc`   
`which mpif90`  
`mpicc -o hellow hellow.c`  
`mpirun -np 4 ./hellow`  
####################################################

安装命令:  
`cmake .. <option>`  
`option:`  
`-DLOCAL_INSTALL_ALL=ON`   
`-DMPIBAT=ON`   
`-DBOOST_INCLUDE_DIR=/home/wsy/programs/HEPFIT/boost/boost`   
`-DDEBUG_MODE=ON （不是必须的）`  
`-DGSL_CONFIG_DIR=/home/wsy/programs/HEPFIT/gsl-latest/gsl-2.7.1 （如果程序提示错误，那么就加上这一行）`  
`-DMPI_CXX_COMPILER=/home/shl/wsy/hepfit/openmpi-4.1.4(错误)`  
`-DCMAKE_INSTALL_PREFIX=/home/wsy/programs/HEPFIT/HEPfit-1.0/build （错误）`  
`-DBAT_INSTALL_DIR=/home/wsy/programs/HEPFIT/bat-1.0.0 （错误）`  
`-DBAT_INSTALL=OFF （不推荐，因为这个命令的作用被整合到了第一个里边）`  
`-DNOMCMC_MODE=ON （暂时用不到）`  
`make`  
`make install`  

############################（这一部分内容还在解读）  
Found MPI_C: /usr/local/mpich-3.3.2/lib/libmpi.so (found version "3.1")   
Found MPI_CXX: /usr/local/mpich-3.3.2/lib/libmpicxx.so (found version "3.1")   
-- Downloading... done  
-- extracting...  
     src='/home/wsy/programs/HEPFIT/HEPfit-1.0-RC2/build/BAT-0.9.4.1.tar.gz'  
     dst='/home/wsy/programs/HEPFIT/HEPfit-1.0-RC2/build/BATBUILD/src'  
-- extracting... [tar xfz]  
-- extracting... [analysis]  
-- extracting... [rename]  
-- extracting... [clean up]  
-- extracting... done  
############################
