# How to Setup / Install an Apache Spark 3.1.1 Cluster on Ubuntu
- Refer: https://www.linkedin.com/pulse/how-setup-install-apache-spark-311-cluster-ubuntu-shrivastava/?trk=pulse-article_more-articles_related-content-card

- Create Azure VMs and allow all ports in NSG

## On Master and Slaves
```
sudo apt update -y
sudo apt install scala -y
sudo apt install sshpass -y
```

## (On all the Virtual Machines – Master and workers)
```
wget https://archive.apache.org/dist/spark/spark-3.1.1/spark-3.1.1-bin-hadoop3.2.tgz
tar xvf spark-3.1.1-bin-hadoop3.2.tgz
sudo rm -rf /usr/local/spark
sudo mv spark-3.1.1-bin-hadoop3.2 /usr/local/spark
ls /usr/local/spark
```

```
sudo nano ~/.bashrc
```

```
export SPARK_HOME=/usr/local/spark
export PATH=$PATH:$SPARK_HOME/bin
```

```
source ~/.bashrc
echo $SPARK_HOME
ls $SPARK_HOME
echo $PATH
```


## (On Master only)
```
cp $SPARK_HOME/conf/spark-env.sh.template $SPARK_HOME/conf/spark-env.sh
sudo nano $SPARK_HOME/conf/spark-env.sh
```

- Add the following parameters (line of code) at the end of file, save and exit.
```
export SPARK_MASTER_HOST='<Master-IP>'export JAVA_HOME=<Path_of_JAVA_installation>
```

```
export SPARK_MASTER_HOST='10.0.0.5'
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
```

### Start Master
```
$SPARK_HOME/sbin/start-master.sh
```

```
tail  -f /usr/local/spark/logs/spark-atingupta2005-org.apache.spark.deploy.master.Master-1-vmspark-master.out
sudo apt install openjdk-11-jdk-headless -y
jps
```

- To see the Apache Spark cluster status in the browser (UI), go to your browser and type: https://<mater-Public-IP>:8080


- To stop services of Apache Spark cluster, run the following command:
```
$SPARK_HOME/sbin/stop-master.sh
jps
```

### Start the Workers
```
$SPARK_HOME/sbin/start-worker.sh spark://<public-ip-of-master>:7077
```

```
$SPARK_HOME/sbin/start-worker.sh spark://20.231.198.62:7077
```

```
tail -f /usr/local/spark/logs/spark-atingupta2005-org.apache.spark.deploy.worker.Worker-1-vmpyspark-w1.out
```

```
sudo apt install openjdk-11-jdk-headless -y
jps
```
