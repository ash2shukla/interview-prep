# Notification System

### Types of Notifications

* **Pub Sub Based**
  * 1 source to many
  * Broadcast
  * Redis, Rabbitmq
* **Pull Based**
  * **Client has control to close connection**
  * Not realtime very sparse notifications
  * Used in RSS feed&#x20;
  * Causes too much burden on server
  * Long polling
*   **Push Based**

    * **Server has control to close connection**
    * Server sends something on an open socket
    * Light on server but hard to scale due to multiple open socket connections
    * Websockets (Bidirectional), Server Sent Events(Unidirectional - from server side)



### Requirements

* **Functional Requirements**
  * Send notifications
  * Single / Bulk notifications
  * No same notification twice
  * Log notification events ( dispatched / delivered / cancelled / failed / seen )
* **Non Functional Requirements**
  * Durable - No Loss
  * Real time
  * High availability
  * Pluggable ( Open to integrate with other services through API )

### Solution

**Notification REST Service:** For rest clients to initiate a notification request and publishes the event on _svc.notifications.raw_

**Notification Validator and Prioritizer:** Talks to an elastic search cluster for quick look up of information of the notifier, validates and prioritizes the request as per the looked up data. publishes  on _svc.notifications.validated.\*,_ based on the priority the prioritizer will publish on _svc.notifications.validated.low, svc.notifications.validated.medium or svc.notifications.validated.high_ the consumers will then consume from all three topics based on the priority.&#x20;

**Rate Limiter:** Consume from notification validator and prioritizer and limit the incoming using kafka quotas.

**Notification Payload and Preference Handler:** Lookup the payload user data and create separate events for each user in the notification service. Talks to user db to do this eg. MySQL, MongoDB etc. after creating the request publishes the events on _svc.notifications.dispatchable_ topic.\
If the event is of type inbound event then sends to _svc.notifications.inbound_ topic.

**Notification Tracker:** Listens on _svc.notifications.track_ and keeps the status of a notification in a nosql db updated for logging notification events. From this nosql db other analytics tools can consume.

**Notification Adapters and Dispatchers:** Protocol specific handlers that consume from _svc.notifications.dispatchable_ and transform the payload to SMS / Email / SSE / Websocket / Firebase etc. This component will be interfaced with other services.

**Inbound Notification Event Handler:** Consumes from _svc.notifications.inbound_ topic and sets the "seen" / "failed" etc. for notification tracker.

![](<../../.gitbook/assets/image (4).png>)

### **Read this**

{% embed url="https://stackoverflow.com/questions/30655361/does-kafka-support-priority-for-topic-or-message" %}

{% embed url="https://www.codekarle.com/system-design/Notification-system-design.html" %}

### Watch this

{% embed url="https://www.youtube.com/watch?v=R873BlNVUB4" %}
