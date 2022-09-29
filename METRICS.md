# Metrics

Below are an example of the metrics as exposed by this exporter. 

```
# HELP docker_hub_image_last_updated last_updated
# TYPE docker_hub_image_last_updated gauge
docker_hub_image_last_updated{image="docker-hub-exporter",user="filecoin"} 1472731040.0
# HELP docker_hub_image_pulls_total pulls_total
# TYPE docker_hub_image_pulls_total counter
docker_hub_image_pulls_total{image="docker-hub-exporter",user="filecoin"} 188672.0
# HELP docker_hub_image_stars stars
# TYPE docker_hub_image_stars gauge
docker_hub_image_stars{image="docker-hub-exporter",user="filecoin"} 3.0
# HELP docker_hub_image_is_automated is_automated
# TYPE docker_hub_image_is_automated gauge
docker_hub_image_is_automated{image="docker-hub-exporter",user="filecoin"} 1.0
```
