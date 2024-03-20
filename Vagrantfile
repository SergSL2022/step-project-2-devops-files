# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: "echo Hello"

# =============================================== JENKINS SERVER =====================================

  config.vm.define "jenkins-server" do |vm1|
    vm1.vm.box = "bento/ubuntu-22.04"
    vm1.vm.hostname = "jenkins-server"
    vm1.vm.network "public_network", ip: "192.168.1.175"
    vm1.vm.provider "virtualbox" do |v|
      v.memory = "8192"
      v.cpus = 1
    end

    vm1.vm.provision "shell", inline: <<-SHELL
  echo hello Jenkins server
  apt-get update

  # Встановлення Prometheus Node Exporter
  wget https://github.com/prometheus/node_exporter/releases/download/v1.2.2/node_exporter-1.2.2.linux-amd64.tar.gz
  tar xvf node_exporter-1.2.2.linux-amd64.tar.gz
  cp node_exporter-1.2.2.linux-amd64/node_exporter /usr/local/bin/
  rm -rf node_exporter-1.2.2.linux-amd64.tar.gz node_exporter-1.2.2.linux-amd64

  cat <<EOL > /etc/systemd/system/node_exporter.service
[Unit]
Description=Node Exporter
After=network.target

[Service]
ExecStart=/usr/local/bin/node_exporter
User=root
Restart=always

[Install]
WantedBy=default.target
EOL

  systemctl daemon-reload
  systemctl start node_exporter
  systemctl enable node_exporter

   #Встановлення і налаштування Prometheus
      sudo apt-get install -y prometheus
      sudo cp /vagrant/prometheus.yml /etc/prometheus/prometheus.yml

      cat <<EOL > /etc/prometheus/prometheus.yml
# Sample config for Prometheus.

global:
  scrape_interval:     15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
  evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
  # scrape_timeout is set to the global default (10s).

  # Attach these labels to any time series or alerts when communicating with
  # external systems (federation, remote storage, Alertmanager).
  external_labels:
      monitor: 'example'

# A scrape configuration containing exactly one endpoint to scrape:
# Here it's Prometheus itself.
scrape_configs:
 
  - job_name: 'prometheus'
    scrape_interval: 5s
    scrape_timeout: 5s
    static_configs:
      - targets: ['localhost:9090']

  - job_name: node
    static_configs:
      - targets: ['localhost:9100']

  - job_name: 'jenkins_server_node_exporter'
    static_configs:
      - targets: ['192.168.1.175:9100']
      
  - job_name: 'jenkins_worker_node_exporter'
    static_configs:
      - targets: ['192.168.1.177:9100']

EOL
      sudo systemctl daemon-reload
      sudo systemctl enable prometheus
      sudo systemctl restart prometheus

  #Install Grafana-server
      apt-get install -y vim adduser libfontconfig1
      wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
      sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
      sudo apt-get update
      sudo apt-get install -y grafana
      sudo systemctl start grafana-server
      sudo systemctl enable grafana-server

  #Install Docker
      sudo apt-get install -y ca-certificates curl
      sudo install -y -m 0755 -d /etc/apt/keyrings
      sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
      sudo chmod a+r /etc/apt/keyrings/docker.asc
      echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

      sudo apt-get update
      sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
      sudo usermod -aG docker vagrant

SHELL
  end

# =============================================== JENKINS WORKER =====================================

config.vm.define "jenkins-worker" do |vm2|
    vm2.vm.box = "bento/ubuntu-22.04"
    vm2.vm.hostname = "jenkins-worker"
    vm2.vm.network "public_network", ip: "192.168.1.177"
    vm2.vm.provider "virtualbox" do |v|
      v.memory = "4096"
      v.cpus = 1
    end

    vm2.vm.provision "shell", inline: <<-SHELL
      echo hello Jenkins worker
      apt-get update

      # Встановлення Prometheus Node Exporter
      wget https://github.com/prometheus/node_exporter/releases/download/v1.2.2/node_exporter-1.2.2.linux-amd64.tar.gz
      tar xvf node_exporter-1.2.2.linux-amd64.tar.gz
      cp node_exporter-1.2.2.linux-amd64/node_exporter /usr/local/bin/
      rm -rf node_exporter-1.2.2.linux-amd64.tar.gz node_exporter-1.2.2.linux-amd64
      cat <<EOL > /etc/systemd/system/node_exporter.service
[Unit]
Description=Node Exporter
After=network.target

[Service]
ExecStart=/usr/local/bin/node_exporter
User=root
Restart=always

[Install]
WantedBy=default.target
EOL
      systemctl daemon-reload
      systemctl start node_exporter
      systemctl enable node_exporter


    #Install Docker
      sudo apt-get install -y ca-certificates curl
      sudo install -y -m 0755 -d /etc/apt/keyrings
      sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
      sudo chmod a+r /etc/apt/keyrings/docker.asc
      echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

      sudo apt-get update
      sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
      sudo usermod -aG docker vagrant


    # Install Java
      sudo apt install -y default-jre
    SHELL
  end
end