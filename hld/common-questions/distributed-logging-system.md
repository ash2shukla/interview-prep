# Distributed Logging System

### Requirements

1. Collect logs for system metrics
2. Collect service logs
3. Logs should be searchable
4. Fault tolerant and highly available system

### Solution

Put a kafka for queueing log events sent by file beats and prometheus, save metric logs to a TSDB and service logs to Elastic Search. Expose the whole thing on Kibana or Grafana.

![](<../../.gitbook/assets/image (10).png>)

### Read This

{% content-ref url="notification-system.md" %}
[notification-system.md](notification-system.md)
{% endcontent-ref %}
