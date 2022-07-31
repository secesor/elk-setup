# Disclaimer
This guide is not intended to be a comprehensive reference nor an in-depth tutorial. It's a beginners guide from a beginner. I'll do my best to keep it as formal and well structured as possible so apologies if it doesn't fulfill your expectations.

# Pre-requisites
- General knowledge of Unix command line.
- Basic usage of Docker and Docker Compose.

# Background
ELK is a stack comprised of a set of tools which provide the ability to collect information from multiple sources, aggregate this information and display it on different layouts like dashboards or historical view. It also gives you the ability to query and correlate data.

ELK stands for ElasticSearch, Logstash and Kibana which are the three tools that conform the stack.

Although ELK is one of the most popular stacks, it isn't the only one and even some parts of the stack might be replaced by other tooling according to your needs and/or preferences.

# Infrastructure overview
We'll start with a single ELK node which will cover basic needs but always having in mind that we might need to scale up at any point in time as our infrastructure grows.

We'll setup ELK on a compute instance with 12GB of RAM which should be enough to cover our initial needs of keeping track of half a dozen servers.

## Specific context
You might find many different guides to install and configure ELK stack but this guide aims at the setup of ELK inside OracleCloud environment. It should, however, serve as reference for any other platform since there are only a few steps specific to OracleCloud.

# References
- [Elastic](https://www.elastic.co/)
- [sebp elk docker](https://elk-docker.readthedocs.io/)
- [Complete guide ELK stack](https://logz.io/learn/complete-guide-elk-stack/)
- [Docker](https://docker.com/)
- [Oracle Cloud](https://www.oracle.com/cloud/)