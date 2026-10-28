## Kubernetes YAML Configuration Files

This repository contains separate Kubernetes YAML configuration files for hands-on practice.

| File Name | Description |
|---|---|
| `nginx-deployment.yaml` | Creates three Nginx Pods using a Deployment. |
| `nginx-headless-service.yaml` | Creates a Headless Service for direct Nginx Pod discovery. |
| `mysql-headless-service.yaml` | Provides DNS discovery for MySQL StatefulSet Pods. |
| `mysql-statefulset.yaml` | Creates three MySQL Pods with stable identities. |
| `mysql-persistent-storage.yaml` | Alternative MySQL StatefulSet configuration with persistent storage. |

### Hands-on Practice

In this exercise, I practiced creating Kubernetes Deployments, Headless Services, and StatefulSets using YAML configuration files.

I also learned how to verify Kubernetes resources, check Pod IP addresses, resolve DNS names using BusyBox, and understand how StatefulSets maintain stable Pod identities.

### Key Learnings

- Deployments manage interchangeable application Pods.
- Headless Services enable direct Pod discovery using DNS.
- StatefulSets maintain stable Pod names and network identities.
- PersistentVolumeClaims help preserve application data.
- Kubernetes DNS allows applications to discover individual Pods.
- Database replication and failover require additional application-level configuration.

**Note:** The MySQL YAML examples are for learning and demonstration. They are not production-ready database cluster configurations.
