# HDFS on Kubernetes

```sh
docker run -d -ti --name hadoop-master -e HADOOP_MASTER_HOST=hadoop-master -e HADOOP_TYPE=master chrismin1202/hadoop-base:v0.0.1

docker run -d -ti --name hadoop-slave -e HADOOP_MASTER_HOST=hadoop-master --link hadoop-master:hadoop-master chrismin1202/hadoop-base:v0.0.1
```

## Credits
The Docker and Kubernetes scripts in this repository are based on the scripts in the following repositories:
* [U-Hopper's Hadoop Docker repository](https://bitbucket.org/uhopper/hadoop-docker)
* [longwuyuan's Hadoop Alpine GitHub repository](https://github.com/longwuyuan/hadoop-alpine)