# Trainer Tasks

```
sudo apt -y update
sudo apt -y install tree git openssl software-properties-common curl wget
```

## Setup multiple users in Ubuntu
- For each participant, we need to setup login accounts
```
sudo groupadd docker
for ((i=1;i<=50;i++)); do
	export username="u$i"
	sudo useradd -m -p "p2" $username;sudo usermod -aG sudo $username;sudo usermod -aG docker $username;echo $username:p | sudo /usr/sbin/chpasswd;sudo chown -R  $username:root /home/$username
done
```

-  Clone Git Repo
```
cd
git clone
cd
```

- Customize linux prompt
```
cat ~/.bashrc
echo 'export PS1="\e[0;31m\e[50m\u@\h\n\w \e[m\n$ "'   >> ~/.bashrc
cat ~/.bashrc
exit
```

### Setup Python
```
sudo add-apt-repository ppa:deadsnakes/ppa -y
sudo apt install -y python3.10
python3.10 --version
sudo apt install -y python3-pip
sudo apt install -y python3-venv
mkdir python_venv
cd python_venv/
python3 -m venv .
source  bin/activate
python -V
deactivate
cd ~
```

### Setup Jupyter Lab
```
#sudo apt install -y python3-dev
curl -L https://tljh.jupyter.org/bootstrap.py | sudo -E python3 - --admin $USER
curl http://vmpyspark.eastus.cloudapp.azure.com/
```
- Login to Jupyter Lab and create users
  - Login ID: atingupta2005
- Open
  - http://vmpyspark.eastus.cloudapp.azure.com/hub/login
  - Login Details: u? / Training@123456

## Install PySpark in Jupyter Lab
- Open Jupyer Lab Terminal from the New -> Terminal
- Run below commands
```
sudo conda update -n base conda
sudo conda update -n base -c defaults conda
sudo conda install --channel defaults openjdk pyspark findspark
```

- Test PySpark
```
pyspark
```

## Test by running code in Jupyter notebook
- Create new Jupyter notebook
- Paste below commands in each cell
```
import findspark
findspark.init()
findspark.find()
```


```
# Import PySpark
from pyspark.sql import SparkSession
```

```
#Create SparkSession
spark = SparkSession.builder.appName('SparkByExamples.com').getOrCreate()
```

```
# Data
data = [("Java", "20000"), ("Python", "100000"), ("Scala", "3000")]
```

```
# Columns
columns = ["language","users_count"]
```

```
# Create DataFrame
df = spark.createDataFrame(data).toDF(*columns)
```

```
# Print DataFrame
df.show()
```
