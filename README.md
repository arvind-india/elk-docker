# Elasticsearch, Logstash, Kibana (ELK) and Watcher Docker image

I forked this Docker image and modified to work with **ELK and Watcher**.
I remove all the unnecessary files for my purpose and added new configuration
files. For [Logstash](https://github.com/lcostantini/elk-docker/blob/master/logstash.conf)
and Watcher to detect multiple [HTTP 500](https://github.com/lcostantini/elk-docker/blob/master/500_watch)
and [slow responses](https://github.com/lcostantini/elk-docker/blob/master/slow_requests_watch).

The image is used with [this](https://github.com/lcostantini/anomaly-detection) application to work in Bluemix.

# Using Docker image in localhost
First you need to clone this repository.
Then build the image
```
docker build -t lcostantini/elk .
```

And tested locally
```
docker run -p 5601:5601 -p 9200:9200 -p 5000:5000 -it --name elk lcostantini/elk
```

# Using Docker image in Bluemix
First you need to install the IBM Containers plug-in for Cloud Foundry, you can see
[here](https://console.ng.bluemix.net/docs/containers/container_cli_ov.html#container_cli_cfic_install)
how to install.
Then you need to build the image in Bluemix with the command:
```
cf ic build -t registry.ng.bluemix.net/NAMESPACE/elk .
```

You can see the image in Bluemix with
```
cf ic images
```

Now in the Bluemix dashboard you can see how to start a new container and follow the instructions there.

### About
Written by [Sébastien Pujadas](https://pujadas.net), released under the [Apache 2 license](https://www.apache.org/licenses/LICENSE-2.0).
