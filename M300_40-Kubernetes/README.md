Apache-Server
===

Die .yaml-Datei ist eine Konfiguration für eine Kubernetes-Deployment und Service für eine Apache-Webanwendung. Das Deployment verwendet ein httpd:latest-Image auf Port 80 mit dem Label app: apache, während der Service den eingehenden Traffic auf Port 80 an das Deployment weiterleitet und einen Node-Port auf 30080 öffnet.

Cluster
===
Diese YAML-Datei definiert eine Kubernetes-Deploymentkonfiguration mit einem "master"- und zwei "worker"-Pods, die die nginx-Image verwenden. Jeder Pod hört auf Port 80 und hat spezifische CPU- und RAM-Ressourcenlimits. Es gibt auch zwei Services, "master-service" und "worker-service", die ClusterIP-Typ sind und auf Port 80 hören. Der "master-service" ist mit dem "master"-Pod und der "worker-service" ist mit den "worker"-Pods verbunden.