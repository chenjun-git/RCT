
<div align="right">Language: :us:
<a title="Chinese" href="./README_zh.md">:cn:</a>
</div>

# RCT(Redis Computed Tomography)

![](https://img.shields.io/badge/redis-%3E%3D2.6.0-green.svg) ![](https://img.shields.io/badge/SpringCloud--lightgrey.svg) ![](https://img.shields.io/badge/build-passing-yellow.svg)

RCT is a one-stop platform for Redis memory structure analysis by parsing RDB files. Support for non-clustered/clustered RDB file analysis, Slowlog query, and monitoring, ClientList query and monitoring.

## Functions
- Memory analysis
  >Through the RDB file analysis, Redis memory uses analysis, support multi-dimensional, multi-report. Support manual, automatic multiple ways! Provide report generation, Redis key export, and other functions!

- Slowlog

  >Slowlog module can regularly collect slowlog information, multidimensional report summary, convenient to view the current slowlog details of the cluster
  
- ClientList

  >ClientList module can easily and efficiently analyze and view the client connection!
   

## Product preview
Screenshot section mainly introduces the main functions of RCT, a series of processes, you can understand the main functions of our platform and application scenarios.

![](./doc/screenshots/rct.jpg)
 
 ## Quick start

 ### jre（linux and windows）
 Before you begin, make sure you install jre1.8+ and download the release package in the release.
 
For example, click rct-dashboard -2.0.0-release.tar.gz to download and extract it (WinRAR software can be used to extract it under Windows, and commands can be used under Linux ``` tar xvf RCT-Dashboard-2.0.0-release.tar.gz ```)
 
1. Preferred startup control center RCT-dashboard
   ```
   java -jar RCT-Dashboard-2.0.0.jar
   ```
2. Start the analyzer rct-analyze
   ```
   java -jar -Xmx1024m -Xms300m RCT-Analyze-2.0.0.jar
   ```

   Adjust the maximum heap size according to the RDB file size ( **be sure to limit the heap size to avoid a performance impact on the online machine** ), Rct-analyze is deployed on rdb-generated machines, or redis installation machines, with one instance deployed per machine.

3. Enter the system

   In the browser to access ``` http://127.0.0.1:8080 ```, enter account and password, the default password for **rct/rct**
 
 ### docker（only Linux platform） 
1. Preferred startup control center RCT-dashboard
  - Default Settings
    ```
    docker run -d  --net=host xaecbd/rct-dashboard:2.0.0
    ```
  - Custom configurations (before execution, please placed on the host config/application.properties db/data.db)
    ```
    docker run -d  -v /opt/app/rct/rct-dashboard/config:/opt/app/rct/rct-dashboard/config -v /opt/app/rct/rct-dashboard/db:/opt/app/rct/rct-dashboard/db --net=host xaecbd/rct-dashboard:2.0.0
    ```
2. Start the analyzer rct-analyze
  - Default Settings
    ```
     docker run -d -e "JAVA_OPTIONS=-Xmx1024m -Xms300m" --net=host xaecbd/rct-analyze:2.0.0
    ```
  - Custom configurations (before execution, please place the config/application.properties on the host)
    ```
    docker run -d -e "JAVA_OPTIONS=-Xmx1024m -Xms300m" -v /opt/app/rct/rct-analyze/config:/opt/app/rct/rct-analyze/config -v /data/redis/redis_cluster:/data/redis/redis_cluster --net=host xaecbd/rct-analyze:2.0.0
    ```    
   Adjust the maximum heap size appropriately based on the RDB size.

3. Enter the system   
    In the browser to access ``` http://127.0.0.1:8080 ```, enter account and password, the default password for **rct/rct**.
   
## Versions
At present, the support is limited to the following versions. As for the higher version, it is under development!

redis version|rct version
---|---
[2.6-5.0.3]|2.X
## The user manual
> The user manual mainly introduces the main functions of each module of RCT

1. [Chart module introduction](./doc/Chart_module.md)
2. [Introduction to RDB analysis module](./doc/Introduction_to_rdb_analysis_module.md)
3. [SlowLog module introduction](./doc/SlowLog_module_introduction.md)
4. [Introduction to ClientList module](./doc/Introduction_to_clientList_module.md)

> RCT usage tutorial
1. [Use RDB analysis tool for quick analysis](./doc/Use_rdb_analysis_tool_for_quick_analysis.md)
2. [How do I add an instance of redis](./doc/add_an_instance_of_redis.md)


## Product Design
> The design document mainly introduces the RCT architecture design and framework design

  1. [Code structure introduction](./doc/Code_structure_introduction.md) 
  2. [Design scheme](./doc/Design_scheme.md) 


## TODO
If you want to know more things, please see  [TODO](./doc/TODO.md) document.
