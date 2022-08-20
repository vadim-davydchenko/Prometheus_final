### On two nodes, installing several services and connecting them to monitoring.
#### On node1: 
- Install docker
- Install docker-compose
- Launch `wordpress` in docker-compose:

  `docker-compose -f docker-compose-wordpress.yml up -d`
- Launch `cadvisor` in docker-compose:
  
  `docker-compose -f docker-compose-cadvisor.yml up -d`
  
- Launch `mysql_exporter` in docker-compose:
  
   `docker-compose -f docker-compose-mysqlexporter.yml up -d`
 
- Install `node_exporter` and setting `systemd service` from him

#### On node2:

- Install Prometheus
- Setting `systemd service` Prometheus
- Setting up the collection of metrics from exporters running on node1 in `/opt/prometheus/prometheus.yml`
- Installing Grafana and Connecting Dashboard ID Exporters
