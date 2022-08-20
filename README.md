### On two nodes, installing several services and connecting them to monitoring.
#### On node1: 
- Install docker
- Install docker-compose
- Launch [wordpress](https://github.com/vadim-davydchenko/prometheus_final/blob/master/docker-compose-wordpress.yml) in docker-compose:

  `docker-compose -f docker-compose-wordpress.yml up -d`
- Launch [cadvisor](https://github.com/vadim-davydchenko/prometheus_final/blob/master/docker-compose-cadvisor.yml) in docker-compose:
  
  `docker-compose -f docker-compose-cadvisor.yml up -d`
  
- Launch [mysql_exporter](https://github.com/vadim-davydchenko/prometheus_final/blob/master/docker-compose-mysqlexporter.yml) in docker-compose:
  
   `docker-compose -f docker-compose-mysqlexporter.yml up -d`
 
- Install `node_exporter` and setting [systemd service](https://github.com/vadim-davydchenko/prometheus_final/blob/master/node_exporter.service) for him

#### On node2:

- Install Prometheus
- Setting [systemd service](https://github.com/vadim-davydchenko/prometheus_final/blob/master/prometheus.service) Prometheus
- Setting up the collection of metrics from exporters running on node1 in [/opt/prometheus/prometheus.yml](https://github.com/vadim-davydchenko/prometheus_final/blob/master/prometheus.yml)
- Installing Grafana and Connecting Dashboard ID Exporters
