# Setup Spark using Docker Compose
- Refer: https://github.com/cluster-apps-on-docker/spark-standalone-cluster-on-docker

```
curl -fsSL https://test.docker.com -o test-docker.sh
sh test-docker.sh
```

```
sudo curl -L https://github.com/docker/compose/releases/download/1.29.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

```
git clone <current-repo-url>
cd <current-repo-folder>
cd Trainer-Env-Prep/setup-spark-using-docker-compose
```

```
sudo docker-compose up -d
```
