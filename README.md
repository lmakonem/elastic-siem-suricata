<p align="center">
    <img src="https://i2.wp.com/newtonpaul.com/wp-content/uploads/2020/12/Elastic_Siem_Blog.jpg?fit=1280%2C720&ssl=1" width="30%" alt="Elastic-SIEM"/>
</p>
<!-- Image source: https://newtonpaul.com/how-to-install-elastic-siem-and-elastic-edr/ -->

<h1 align="center">Elastic SIEM</h1>
<p align="center">Elastic-SIEM is a docker compose template to experiment with Elastic Security features such as SIEM and Elastic Endpoint Security.<br>
   <a href="https://www.elastic.co/security" title="Overview">Official Overview</a>
</p>  

## Docker compose

Bringing up the stack: `sudo docker-compose up -d`  

As soon as the containers are ready, navigate to http://localhost:5601 and login with the following credentials  
**elastic : password**  

Cleanup: `sudo docker-compose down`  

## Beats

> "Beats is a free and open platform for single-purpose data shippers. They send data from hundreds or thousands of machines and systems to Logstash or Elasticsearch."
<p align="center">
<img src="https://www.elastic.co/guide/en/beats/libbeat/master/images/beats-platform.png" width="60%">
</p>

Here are two examples for Filebeat and Auditbeat.

### Filebeat

> "Filebeat is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing."  

- [Overview](https://www.elastic.co/guide/en/beats/filebeat/current/filebeat-overview.html)
- [Download Filebeat client](https://www.elastic.co/downloads/beats/filebeat)
- [Install and configure Filebeat](https://www.elastic.co/guide/en/beats/filebeat/current/filebeat-installation-configuration.html)
- [List of available modules](https://www.elastic.co/guide/en/beats/filebeat/7.11/filebeat-modules.html)

**TL;DR (short version)**
1) [Download client](https://www.elastic.co/downloads/beats/filebeat) (depending on the OS)
2) Enable modules `sudo ./filebeat modules enable auditd system`
3) Set up assets
   ```
   sudo chown root filebeat.yml \
   sudo chown -R root modules.d/ \
   sudo chown -R root modules/ \
   sudo ./filebeat setup -e
   ```  
4) Start Filebeat `sudo ./filebeat -e`
5) **Info**: Check the host, username and password configuration in the .yml file)

***

### Auditbeat

> "Auditbeat is a lightweight shipper that you can install on your servers to audit the activities of users and processes on your systems."  

- [Overview](https://www.elastic.co/guide/en/beats/auditbeat/current/auditbeat-overview.html)
- [Download Auditbeat client](https://www.elastic.co/downloads/beats/auditbeat)
- [Install and configure Auditbeat](https://www.elastic.co/guide/en/beats/auditbeat/current/auditbeat-installation-configuration.html)
- [List of available modules](https://www.elastic.co/guide/en/beats/auditbeat/current/auditbeat-modules.html)

**TL;DR (short version)**
1) [Download client](https://www.elastic.co/downloads/beats/auditbeat) (depending on the OS)
2) Set up assets
   ```
   sudo chown root auditbeat.yml \
   sudo ./auditbeat setup -e
   ```
3) Start Auditbeat `sudo ./auditbeat -e`
4) **Info**: Check the host, username and password configuration in the .yml file)

## Elastic Agents with Endpoint Protection

> "Elastic Agent is a single, unified way to add monitoring for logs, metrics, and other types of data to each host."

> "Fleet provides a web-based UI in Kibana to add and manage integrations for popular services and platforms, as well as manage a fleet of Elastic Agents."

[Overview of the endpoint security feature](https://www.elastic.co/endpoint-security/)  
[Install Elastic Endpoint integration](https://www.elastic.co/guide/en/security/current/install-endpoint.html)  

[Download Elastic Agent](https://www.elastic.co/downloads/elastic-agent)  
[Install Elastic Agent and enroll in Fleet](https://www.elastic.co/guide/en/fleet/current/elastic-agent-installation.html)

## Next configuration steps on the stack
- [Configure TLS](https://www.elastic.co/guide/en/elasticsearch/reference/current/configuring-tls.html#tls-http)
- [User authorization](https://www.elastic.co/guide/en/elasticsearch/reference/current/authorization.html)
- [API keys](https://www.elastic.co/guide/en/kibana/master/api-keys.html)

## Licence

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
