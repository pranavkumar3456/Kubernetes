# Kubernetes
This will include all the kubenetes related components.

![image](https://github.com/pranavkumar3456/Kubernetes/assets/166939027/3666c591-cf42-4ea4-b156-19dfe5207865)

Components of Master Plane
1. API Server
2. ETCD
3. Kube Scheduler
4. Controller Manager

**API Server**
User Interaction: Acts as the primary point of interaction for administrators and users, exposing the Kubernetes API.
Scalability: Designed to scale horizontally to handle varying loads and request volumes efficiently.
Control Plane Front End: Serves as the front end of the Kubernetes control plane, handling REST operations and coordinating cluster activities.

**ETCD**
Metadata Storage: Stores all cluster state and configuration data, including metadata and status information.
Consistency and Availability: Ensures data consistency and high availability through a distributed key-value store model.
Key-Value Data Store: Utilizes a key-value storage format to manage cluster data.
Replication: Fully replicates the entire state across all nodes, ensuring the cluster state is always available.
Security: Implements Transport Layer Security (TLS) with optional client-certificate authentication for secure communication.
Performance: Capable of handling high write loads, benchmarked at 10,000 writes per second.

**Kube Scheduler**
Pod Management: Takes action on user requests for pod creation and management, ensuring that pods are scheduled onto appropriate nodes.
Desired State Maintenance: Ensures the actual number of running pods matches the desired state specified by the user; corrects discrepancies as they occur.
Node Selection: Automatically selects the optimal node for pod placement based on resource availability and constraints; users can specify a node in the pod manifest if needed.
Hardware Configuration: Utilizes hardware and resource information from ETCD to make informed decisions about node selection for pod deployment.

**Controller Manager**
State Reconciliation: Continuously monitors and ensures the actual state of the cluster matches the desired state defined by the cluster configuration.
Environment-Specific Controllers:
  Cloud Controller Manager: Manages cloud-specific control logic, interacting with cloud provider APIs.
  Kube-Controller Manager: Manages generic Kubernetes control logic applicable to non-cloud environments.

Types of Controllers:
Node Controller: Monitors the status of nodes, handling nodes that stop responding or are removed from the cluster.
Route Controller: Manages network routes within the cluster, ensuring proper network setup and connectivity.
Service Controller: Responsible for maintaining service endpoints and managing load balancing for services.
Volume Controller: Oversees the lifecycle of volumes, ensuring that volumes are correctly attached, detached, and managed.
  



