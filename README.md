# Prometheus Docker Hub Exporter

Exposes metrics of container pulls and stars from the Docker Hub API, to a Prometheus compatible endpoint. The exporter is capable of pulling down stats for individual images, or for orgs or users from DockerHub. This is based on the un-documented V2 Docker Hub API.

## Configuration

The image is setup to take parameters from environment variables or flags:

The available environment variables are:

* `BIND_PORT` The port you wish to run the container on, defaults to 9170
* `ORGS` The docker hub organizations you wish to monitor, expected in the format "org1, org2" (Also works for users)
* `IMAGES` The images you wish to monitor, expected in the format "user/image1, user/image2". Can be across different dockerhub users.


Below is a list of the available flags. You can also find this list by using the `--help` flag.

* `images` Images you wish to monitor: expected format 'user/image1,user/image2'
* `listen-address` Address on which to expose metrics and web interface. (default ":9170")
* `organisations` Organisations/Users you wish to monitor: expected format 'org1,org2'
* `telemetry-path` Path under which to expose metrics. (default "/metrics") 

## Install and deploy

Run manually from Docker Hub:
```
docker run -d --restart=always -p 9170:9170 filecoin/docker-hub-exporter -listen-address=:9170
```

Build a docker image:
```
docker build -t <image-name> .
docker run -d --restart=always -p 9170:9170 <image-name> -listen-address=:9170 -images="filecoin/lotus,filecoin/docker-hub-exporter" -organisations="filecoin"
```

## Known Issues

Currently there is a known issue with this build where if you provide a image or list of images belonging to an organisation
that has also been passed into the application then Prometheus will error during metrics gathering reporting that the metric was already collected with the same name and labels.

## Metrics

Metrics will be made available on port 8080 by default
An example of these metrics can be found in the `METRICS.md` markdown file in the root of this repository
