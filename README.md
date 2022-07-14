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
`-DBOOST_INCLUDE_DIR=/home/name/programs/HEPFIT/boost/boost`   
`-DDEBUG_MODE=ON （不是必须的）`  
`-DGSL_CONFIG_DIR=/home/wsy/programs/HEPFIT/gsl-latest/gsl-2.7.1 （如果程序提示错误，那么就加上这一行）`  
`-DMPI_CXX_COMPILER=/home/shl/name/hepfit/openmpi-4.1.4(错误)`  
`-DCMAKE_INSTALL_PREFIX=/home/name/programs/HEPFIT/HEPfit-1.0/build （错误）`  
`-DBAT_INSTALL_DIR=/home/name/programs/HEPFIT/bat-1.0.0 （错误）`  
`-DBAT_INSTALL=OFF （不推荐，因为这个命令的作用被整合到了第一个里边）`  
`-DNOMCMC_MODE=ON （暂时用不到）`  
`make`  
`make install`  

############################(关于BAT的环境变量设置)
export PATH="/home/name/programs/HEPFIT/HEPfit-1.0-RC1/build/BAT/bin:$PATH"
export LD_LIBRARY_PATH="/home/name/programs/HEPFIT/HEPfit-1.0-RC1/build/BAT/lib:$LD_LIBRARY_PATH"
export CPATH="/home/name/programs/HEPFIT/HEPfit-1.0-RC1/build/BAT/include:$CPATH"
export PKG_CONFIG_PATH="/home/name/programs/HEPFIT/HEPfit-1.0-RC1/build/BAT/lib/pkgconfig:$PKG_CONFIG_PATH"
############################

程序可能存在的bug

1.编译例子中的文件时，最好使用CXX=/usr/local/mpich-3.3.2/bin/mpicxx进行编译。这个命令一般在makefile中。

2.如果提示找不到mpi.h这个头文件，那么建议手动找到配置环境时安装的mpich文件，在这个文件的路径下找到include/mpi.h，并在对应的.cpp文件中手动指明这个文件的路径。

