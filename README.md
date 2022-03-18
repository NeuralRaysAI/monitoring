# A Prometheus & Grafana docker-compose stack
Here's a quick start to stand-up a [Prometheus](http://prometheus.io/) stack containing Prometheus, Grafana and Node scraper to monitor your Docker infrastructure. 

## Pre-requisites
Before we get started installing the Prometheus stack. Ensure you install the latest version of docker and [docker-compose](https://docs.docker.com/compose/install/) on your Docker host machine. This has also been tested with Docker for Mac and it works well.

## Installation & Configuration
Clone the project locally to your Docker host. 

If you would like to change which targets should be monitored or make configuration changes edit the [/prometheus/prometheus.yml](https://github.com/NeuralRaysAI/monitoring/blob/main/prometheus/prometheus.yml) file. The targets section is where you define what should be monitored by Prometheus. The names defined in this file are actually sourced from the service name in the docker-compose file. If you wish to change names of the services you can add the "container_name" parameter in the `docker-compose.yml` file.

Once configurations are done let's start it up. From the /monitoring project directory run the following command:

    $ docker-compose up -d


That's it. docker-compose builds the entire Grafana and Prometheus stack automatically. 

The Grafana Dashboard is now accessible via: `http://<Host IP Address>:3000` for example http://192.168.10.1:3000

username - admin
password - admin (Password is stored in the `.env` env file)

## Troubleshooting
It appears some people have reported no data appearing in Grafana. If this is happening to you be sure to check the time range being queried within Grafana to ensure it is using Today's date with current time.