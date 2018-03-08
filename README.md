Logz.io Docker Log Shipping Reference Architecture

The recommended approach for shipping logs from Docker containers to utilize the Docker JSON File logging driver and FluentD. Logz.io accepts many different methods of shipping, but provides more extended configuration references for the recommended approach below.

Requirements

Docker (some version)

Getting Started
1 - Make sure the JSON-file logging driver is enabled (this is the default Docker logging driver):
https://docs.docker.com/config/containers/logging/json-file/
2 - Docker build to build the package:
docker build -t fluentd_logzio_docker:1.0 .
3 - Docker run with a volume mount to the container log directory:
docker run -v /var/lib/docker/containers:/var/lib/docker/containers fluentd_logzio_docker:1.0

Configuration
The fluent.conf file contains configuration and comments which accomplish the following:
1 - Pulls sufficient metadata from config.v2.json in the container logging directory to identify logs and tag them with new fields
2 - Chooses a field (in this case Docker image, but is customizable) to take the place of the required 'type' field
3 - Copies the contents of the 'log' field to 'message' in order for enhanced visibility in Kibana discover page
4 - Drops unnecessary fields (including the log field and unnecessary container metadata)

TODO
1 - Route to different sub-accounts
2 - Setup and test multi-line messages
3 - Clean up cont_meta_data json parsing

