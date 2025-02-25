---
icon: elementor
---

# Docker Swarm

Docker is one of the applications which makes creation,publishing, and running of the containers easy

Docker Swarm makes sure, at any point of time, we have the defined state of the application

* When a container health-check fails for n times, swarm restarts the container
* If a node become unresponsive swarm will reschedule the containers in active nodes
* Networking via iptables, called overlay network
* **packets travel:** container → docker bridge network → iptables → ipvs → second host ...

&#x20;&#x20;

<figure><img src="../../../../../.gitbook/assets/swarm_arch.png" alt=""><figcaption></figcaption></figure>

*   **Creating a service in Docker Swarm**

    telemetry-service.yml

    ```
    version: "3.3"
    services:
        telemetry:
            image: subird/telemetry-service:2.0.0
            ports:
                - "9001:9001"
            deploy:
                replicas: 2
                resources:
                  reservations:
                    memory: "50M"
                  limits:
                    memory: "100M"
    ```





<figure><img src="../../../../../.gitbook/assets/telemetry-service.png" alt=""><figcaption></figcaption></figure>
