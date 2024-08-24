sudo apt-get update
sudo apt-get upgrade -y

sudo apt-get install -y docker.io

sudo systemctl start docker
sudo systemctl enable docker

sudo usermod -aG docker $USER
newgrp docker

sudo docker pull prom/prometheus
sudo docker network create network
sudo docker volume create prometheus-data

nano prometheus.yml

sudo docker container run --name prometheus -v prometheus.yml -v prometheus-data:/prometheus -p 9090:9090  prom/prometheus

sudo docker pull grafana/grafana
sudo docker volume create grafana-data
sudo docker container run -v grafana-data -p 3000:3000 --name grafana --network network grafana/grafana



# <dns>:3000


# admin
# admin

# < rename as needed > 

# select data source <dns>:9090
# select metric: e.g.  go_memstats_alloc_bytes_total
# /metrics handler
# 'run queries'