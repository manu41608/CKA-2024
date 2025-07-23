## Check out the task.md file for the hands-on exercises

## Cheatsheet for Kubernetes commands:
https://kubernetes.io/docs/reference/kubectl/quick-reference/

### Replicaset
https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/

![image](https://github.com/piyushsachdeva/CKA-2024/assets/40286378/3e9792d4-1127-44b4-a6ec-cdc2a82219e3)


### Deployment
https://kubernetes.io/docs/concepts/workloads/controllers/deployment/

![image](https://github.com/piyushsachdeva/CKA-2024/assets/40286378/b888d272-c623-4a00-8381-45c25ce9d9c0)


### Replication Controller
https://kubernetes.io/docs/concepts/workloads/controllers/replicationcontroller/


✅ Full Corrected and Annotated YAML

apiVersion: apps/v1

apiVersion: Specifies the version of the Kubernetes API to use.
apps/v1 is used for resources like Deployments, StatefulSets, ReplicaSets, etc.


kind: ReplicaSet

kind: Indicates the type of Kubernetes object you are creating.
Here, it's a ReplicaSet, which ensures a specified number of pod replicas are running at any given time.


metadata:
  name: frontend
  labels:
    app: guestbook
    tier: frontend

metadata: Provides metadata about the ReplicaSet like its name and labels.

name: The name of this ReplicaSet (frontend).

labels: Key-value pairs attached to this ReplicaSet. Labels help identify and group resources.

app: guestbook – This ReplicaSet is part of the "guestbook" app.

tier: frontend – This indicates that this is the frontend tier.




spec:
  replicas: 3  # Modify as needed (number of pods you want)

spec: This section defines the desired behavior of the ReplicaSet.

replicas: Number of pod replicas to maintain (3 in this case). ReplicaSet ensures this number is always running.



selector:
    matchLabels:
      tier: frontend

selector: Defines how the ReplicaSet finds which Pods to manage.

matchLabels: The ReplicaSet will manage all Pods with the label tier: frontend.



template:
    metadata:
      labels:
        tier: frontend

template: This is the Pod template that ReplicaSet will use to create new pods.

metadata.labels: These labels must match the selector above so ReplicaSet can track the pods it creates.



spec:
      containers:
        - name: php-redis
          image: us-docker.pkg.dev/google-samples/containers/gke/gb-frontend:v5

spec.containers: Defines the container(s) that will run in each Pod.

name: Name of the container (php-redis).

image: The Docker image used to run the container.

In this case, the image is gb-frontend:v5 hosted on Google Container Registry.





---

📝 Summary

This ReplicaSet will:

Create 3 Pods.

Each Pod will run a single container using the gb-frontend:v5 image.

The Pods will be labeled tier: frontend.

The ReplicaSet will manage any Pod with tier: frontend label.



---





