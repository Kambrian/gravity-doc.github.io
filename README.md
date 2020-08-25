欢迎进入上海交通大学天文系高性能计算中心

高性能集群队列信息
A job scheduling system(pbs/torque),which configured with three queues: 
 1. normal(gr01-gr32)[default queue]
 2. small(gr33-gr36)
 3. fat(fat01)
 4. all(gr01-gr36)
高性能集群作业提交脚本
the sample submit script for torque:
  #PBS -N gr01-linpack
  #PBS -l nodes=gr01:ppn=72
  #PBS -q normal
  #PBS -V
  #PBS -S /bin/bash
  #PBS -W group_list=project2
  module load mpi/intel-2018 
  cd $PBS_O_WORKDIR
  NP=`cat $PBS_NODEFILE | wc -l`
  cat $PBS_NODEFILE > /tmp/nodefile.$$
  mpirun -machinefile /tmp/nodefile.$$ -n $NP  EXEC
  rm -rf /tmp/nodefile.$$
  rm -rf /tmp/nodes.$$
notes: the group_list argument is your project name
高性能集群module的使用
module can be used to manage the software in this cluster. Usage as follow:
 1. module avail  # list all software 
 2. module load modulefiles   # load moduelfiles for special software
 3. module unload modulefiles # unload modulefiles
 4. module list   # list modulefiles loaded now
 5. module switch modulefiles1 modulefiles2        # switch from modulefiles1 to modulefiles2
