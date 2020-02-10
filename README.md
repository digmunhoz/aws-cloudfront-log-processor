# AWS CloudFront Log Processor

This project was designed to help people to process logs from CloudFront (AWS CDN Service).

Using this project you can not only process logs locally to do some analysis by yourself but also implement this bundle on your production environment.

All you have here is a [docker-compose](https://docs.docker.com/compose/compose-file/) file which runs:

* Logstash to process all log files
* Elasticsearch to receive all logs processed by logstash
* Grafana to visualize processed data

## Prerequisites

You will need:

* [Docker](https://docs.docker.com/install/)
* [Docker Compose](https://docs.docker.com/compose/install/)

## Processing files locally

If you want to process a few files, you can run it locally.
Just copy gziped (from S3) files to the `./data/logstash/files` directory and then run the command `docker-compose up -d`.

After that, you can see, by using `docker-compose logs -f`, that the logstash has started processing the files.

Then you can access the Grafana (`http://localhost:3000`) with username `admin` and password `changeme` to see your data been generated.

There is a default dashboard created to help you to do your analysis.

> Notice: All processed files will be deleted after the process. The logs will be registered in ./data/logstash/logs

> If you need some help to enable CloudFront logs, please follow these [procedures](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/AccessLogs.html#ChangeSettings)