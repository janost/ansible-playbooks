## A playbook to deploy prometheus, node_exporter and ping_exporter

### Purpose
This playbook can be used to deploy and update prometheus, node_exporter and ping_exporter to a machine running a systemd-based GNU/Linux distribution. Currently only amd64 and arm64 architectures are supported, but support for other architectures can be easily added via configuration (and cross-compiling ping_exporter).

### Why?
I'm using this stack to get basic metrics from a few servers. Prometheus instances on nodes are pushing metrics gathered from localhost to a remote InfluxDB instance through a Wireguard VPN connection.

### Software used
[Prometheus][prometheus]  
[node_exporter][node_exporter]  
[ping_exporter][ping_exporter]

### Note about ping_exporter binaries
This playbook ships its own ping_exporter binaries in the `files` directory. The reason for this is the upstream project doesn't ship arm64 binaries currently, so I cross-compiled it for my own use. If you don't trust these binaries, I suggest compiling your own.

### How to use
Edit `config/config.yaml` and run the playbook on your machines. You might also want to take a look on the rest of the configuration in the `templates` directory.


[prometheus]:    https://github.com/prometheus/prometheus
[node_exporter]: https://github.com/prometheus/node_exporter
[ping_exporter]: https://github.com/czerwonk/ping_exporter
