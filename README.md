# Kubernetes
This will include all the kubenetes related components..

![image](https://github.com/pranavkumar3456/Kubernetes/assets/166939027/3666c591-cf42-4ea4-b156-19dfe5207865)

**Components of Master Plane**
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



**Components of Worker Plane**
1. Kube Proxy
2. Kubelet
3. Pods
4. Container Engine


**Kube Proxy**

Networking: Manages networking rules on nodes, responsible for service discovery and load balancing.

IP Allocation: Allocates IP addresses to pods, ensuring proper network communication within the cluster.

Node Deployment: Runs on each node in the cluster to maintain network rules.

API Communication: Communicates with the Kubernetes master node via the API Server to maintain network configuration and routing rules.


**Kublet**

Node Agent: Acts as an agent running on each node, responsible for managing the node's lifecycle.

Pod Management: Listens to the Kubernetes master for pod creation requests and ensures that containers are running as specified.

State Reporting: Provides pod status and node information to ETCD via the API Server.

Communication Port: Uses port 10255 for health checks and status reporting.

Status Updates: Sends success or failure statuses of pod operations to the control plane.


**Pods**

Basic Unit: The smallest deployable unit in Kubernetes, encapsulating one or more containers.

Container Management: While a pod can contain multiple containers, it is recommended to have one container per pod for simplicity and efficiency.

IP Addressing: Each pod has its own IP address, but the containers within share the pod's network namespace.

Cluster Composition: A Kubernetes cluster consists of at least one master node and multiple worker nodes.

Dependency: Kubernetes cannot run containers outside of pods; all container operations are managed through pods.

Scaling and Healing: Pods do not provide auto-scaling and auto-healing by default; higher-level Kubernetes objects like Deployments, ReplicaSets, and StatefulSets provide these features.

Crash Recovery: Pod crashes are handled by higher-level objects which ensure that failed pods are automatically replaced or restarted.


**Container Engine**

Kubelet Interaction: Works in conjunction with the Kubelet to manage container operations.

Image Management: Responsible for pulling container images from registries.

Container Lifecycle: Manages the start and stop operations of containers based on the instructions provided in the pod manifest.

Port Exposure: Exposes ports specified in the manifest, allowing external access to containerized applications.





**Kubernetes Objects**




**Pod:**

Explanation: The smallest and simplest Kubernetes object. A pod is a thin wrapper around one or more containers, sharing the same network namespace and storage.

Simpler: A pod is like a small, basic unit in Kubernetes that runs your containers together.

**Service:**

Explanation: An abstraction that defines a logical set of pods and a policy to access them. Services provide a stable IP address and DNS name to access a group of pods.

Simpler: A service gives a fixed IP address and name to a group of pods so they can be accessed easily.

**Volume:**

Explanation: A directory accessible to containers in a pod. Volumes enable data to be shared and persist across container restarts.

Simpler: A volume is shared storage for the containers in a pod.

**Namespace:**

Explanation: A mechanism to divide cluster resources between multiple users. Namespaces provide a way to organize resources into virtual clusters.

Simpler: Namespaces are like folders that organize resources in a cluster.

**ReplicaSets:**

Explanation: Ensures a specified number of pod replicas are running at any given time. ReplicaSets are often used by Deployments for scaling purposes.

Simpler: A ReplicaSet keeps a certain number of identical pods running.

**Replication Controller:**

Explanation: Similar to ReplicaSets, it ensures a specified number of pod replicas are running. ReplicaSets have mostly replaced Replication Controllers.

Simpler: Like a ReplicaSet, but older and less commonly used.

**Secrets:**

Explanation: An object that contains a small amount of sensitive data, such as passwords, tokens, or keys. Secrets help manage sensitive information securely.

Simpler: Secrets store sensitive information like passwords securely.

**ConfigMaps:**

Explanation: An API object used to store non-confidential data in key-value pairs. ConfigMaps allow configuration data to be separated from container images.

Simpler: ConfigMaps store configuration settings for your applications.

**Deployments:**

Explanation: Manages the deployment of ReplicaSets and provides declarative updates to applications. Deployments allow rolling updates and rollbacks.

Simpler: Deployments manage updates and versions of your applications.

**StatefulSets:**

Explanation: Manages stateful applications, providing unique identities, stable network identities, and persistent storage for each pod.

Simpler: StatefulSets manage applications that need stable, persistent storage and network IDs.

**Jobs:**

Explanation: Ensures that a pod runs to completion, executing a specified task. Jobs are used for short-lived, batch processing tasks.

Simpler: Jobs run tasks to completion and then stop.

**DaemonSets:**

Explanation: Ensures that all (or some) nodes run a copy of a pod. DaemonSets are used for tasks like logging and monitoring that need to run on every node.

Simpler: DaemonSets run the same pod on all or some nodes in the cluster.

**Label:**

Explanation: Key-value pairs attached to objects, used for organization and selection purposes. Labels are used to identify and organize resources.

Simpler: Labels are tags used to identify and filter resources in the cluster.


