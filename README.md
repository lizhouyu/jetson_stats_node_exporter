# Customized Nvidia Jetson Prometheus Node Exporter

This is a cutomized version of Nvidia Jetson Prometheus Node Exporter forked from [laminair/jetson_stats_node_exporter](https://github.com/laminair/jetson_stats_node_exporter).

# Build for Jetson Stats
This exporter is dependent on the [jetson_stats](https://github.com/rbonghi/jetson_stats). The version used for the Docker build should be the same as the one installed on the Jetson device.
To accomodate different versions of jetson_stats, following the steps below to rebuild the Docker image:
1. In jetson_stats_node_exporter/requirements.txt, change the line with `jetson-stats==x.y.z` to the version installed on your Jetson device.
2. Build the Docker image with the command:
   ```bash
   docker build -t jetson_stats_node_exporter:jtop.x.y.z .  
   ```
3. To start the exporter container, change the image tag in `compose.yml` accordingly:
   ```
    image: jetson_stats_node_exporter:jtop.x.y.z
    ```
4. Start the container with:
   ```bash
    docker-compose -f compose.yml up -d
    ```

# Usage
You can run the exporter using Docker or Docker Compose. The exporter exposes metrics on port `9100` by default.