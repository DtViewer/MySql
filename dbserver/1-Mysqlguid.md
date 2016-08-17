# Mysql 概述

这里描述mysql的一些易混淆概念

    readahead
    single page flush
    group commit
    purge lag 
    change buffer 
    adaptive flush 
    history list 
    

### Read ahead
Mysql 根据用户具体的请求方式，根据其内部算法来判定是否一次读取一个extent 比读取单个page 更有意义，有两种方式：

    linear readahead: 
      主要是用来判定是否需要对临近的extent进行预读；判定的条件包括当前区的page在缓存池中出现
      的数量，以及其读取时的方式；当前区是指，用户线程正在读取的extent；当用户线程试图访问缓
      存池中的block时，就会触发线性预读，此时mysql会判定 用户读取的page 是否是 extent的边缘 
      块，以及其访问方式，如果 用户要访问 的位于缓存池block数量 超innodb_read_ahead_threshold 
      值，并且是顺序读，此时innodb 就会执行异步的 临近区的预读；
   
    random readahead:
       此种方式主要关注当前区，并且关注每个block的访问，当参数innodb_random_read_ahead ，mysql
       会关注当前区中有多少个page 位于缓存池中，如果特定数量的block位于缓存池，并且最近被访问过，
       此时mysql会异步读取整个区；
       
       
### single page flush 

    
    

   
   
    
    
    

 