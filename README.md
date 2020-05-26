# CLD_Kubernetes

## Task 1 - Deliverables

- Document any difficulties you faced and how you overcame them.

  - We didn't know at first how to assign a value for the endpoint of the localhost. By trying things out we managed to find a solution.

- Copy the object descriptions into the lab report.

  - Description of the Pods:

    - pod-api

      ![](.\img\t1_pod_api.jpg)

    - pod-redis

      ![](.\img\t1_pod_redis.jpg)

    - pod-frontend

      ![](.\img\t1_pod_frontend.jpg)

  - Description of the Services:

    -  service-api

      ![](.\img\t1_svc_api.jpg)

    - service-redis

      ![](.\img\t1_svc_redis.jpg)

    - service-kubernetes

      ![](.\img\t1_svc_kubernetes.jpg)

## Task 2 - Deliverables

- Document any difficulties you faced and how you overcame them.

  - The first difficulty was finding what was a target port and how to use it. Then we had to correctly map the ip addresses and ports of the different pods/services so that everything matches. We found the details in the download files about how to do it.
  - The second problem was connecting the pod to the service when creating it. It said the cluster had not enough nodes. We had to modify the default pool in the cluster details at the bottom of the page.
  - We couldn't connect to the frontend service so we had to increase the number of nodes again. We used the clusterIP instead of the load-balancer so this was also something wrong we did

-  Copy the object descriptions into the lab report (if they are unchanged from the previous task just say so).

  - Pods Descriptions:

    - frontend pod

      ![](.\img\t2_pod_frontend.jpg)

    - api pod

      ![](.\img\t2_pod_api.jpg)

    - Pod Redis

      ![](.\img\t2_pod_redis.jpg)

      

  - Services Descriptions:

    - Service Kubernetes

      ![](.\img\t2_svc_kubernetes.jpg)

    - Service Api

      ![](.\img\t2_svc_api.jpg)

    - Service Redis

      ![](.\img\t2_svc_redis.jpg)

- Take a screenshot of the cluster details from the GKE console.

  ![](.\img\t2_cluster_a.jpg)

  ![](.\img\t2_cluster_b.jpg)

  ![](.\img\t2_cluster_c.jpg)

- Copy the output of the `kubectl describe` command to describe your load balancer once completely initialized.

  - It's located in the svc-frontend

    ![](.\img\t2_svc_frontend.jpg)

## Task 3 - Deliverables

### Subtask 3.1

- Use only 1 instance for the Redis-Server. Why?
  - While using a redis cluster, it is important that we map the Pods to only 1 port on the same server.
- Other observations

### Subtask 3.2

- What happens if you delete a Frontend or API Pod? How long does it take for the system to react?

- What happens when you delete the Redis Pod?

- How can you change the number of instances temporarily to 3? Hint: look for scaling in the deployment documentation

  - ```shell
    kubectl scale deployment.v1.apps/nginx-deployment --replicas=3
    ```

- What autoscaling features are available? Which metrics are used?

  - We can use [horizontal Pod autoscaling](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/) where we specify the minimum and maximum number of pods in our cluster and it is based on the CPU utilization of our existing Pods.

- How can you update a component? (see "Updating a Deployment" in the deployment documentation)

  

### Other Deliverables

- Document any difficulties you faced and how you overcame them.
- Copy the object descriptions into the lab report.
  - Every other Pod/Service are the same as they were previously on Task 2