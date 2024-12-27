### On two nodes, installing several services and connecting them to monitoring.
#### On node1:
- **Install Docker and Docker Compose, and Deploy Services:**
  - Use the playbook `node.yml` to install Docker and Docker Compose, and deploy all necessary services (WordPress, cAdvisor, MySQL Exporter, and Node Exporter) on Node1.
  - Playbook:
    ```bash
    ansible-playbook -i inventory.yml node.yml
    ```

#### On node2:

- **Install Prometheus and Grafana:**
  - Use the playbook `prometheus.yml` to install Prometheus and Grafana on Node2.
  - The `prometheus.yml` configuration file is generated from the `prometheus/templates/prometheus.yml.j2` template.
  - Playbook:
    ```bash
    ansible-playbook -i inventory.yml prometheus.yml
    ```

- **Set up Metric Collection from Node1 Exporters:**
  - Metrics from `node_exporter`, `mysqld_exporter`, and `cAdvisor` running on Node1 are configured in the Prometheus setup.
  - This configuration is applied during the Prometheus role execution.

- **Access Grafana:**
  - Grafana is available on port 3000 with default admin credentials (`admin:admin`). Use the following dashboard IDs to import predefined dashboards:
    - **1860** - Node Exporter Dashboard
    - **193** - cAdvisor Dashboard
