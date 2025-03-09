Q1: How would you design a CI/CD pipeline for a new microservices application?

A: I would set up a pipeline with stages for code checkout, build (compile or containerize the microservice), run unit tests, then package artifacts or Docker images. Next stages would deploy to a staging environment and run integration tests. If all tests pass, an approval or automated step would promote the build to production and deploy with minimal downtime.

Q2: Can you explain blue-green deployment and how to implement it in a CI/CD pipeline?

A: Blue-green deployment means having two production environments (blue and green) where one is live and the other is idle. I deploy the new version to the idle environment (for example, green) and test it while the old version (blue) is still serving users. Once the new version is confirmed good, I switch the traffic to green (making it live) and idle out blue. The CI/CD pipeline would automate deploying to the green environment and flipping the traffic, with the ability to roll back if needed.

Q3: How can you trigger a Jenkins job automatically when code is pushed to a repository?

A: The best way is to use a webhook from the source control system. For example, in GitHub or GitLab, I’d configure a webhook to notify Jenkins when a commit is pushed. Jenkins (with the appropriate plugin) then receives the hook and triggers the job immediately, instead of using periodic polling.

Q4: What is the difference between a Declarative pipeline and a Scripted pipeline in Jenkins?

A: A Declarative pipeline uses a simplified, predefined syntax in a Jenkinsfile (with a pipeline {} block) and is easier to write and maintain for most CI/CD needs. A Scripted pipeline is written in full Groovy code and offers more flexibility but is more complex. In short, Declarative is a higher-level syntax with built-in structure and error handling, whereas Scripted is lower-level and free-form.

Q5: How do you manage sensitive credentials (like passwords or API keys) in a Jenkins pipeline?

A: I never hard-code secrets in the pipeline. Instead, I store credentials in Jenkins Credentials store (or an external vault) and reference them in the pipeline. For example, using Jenkins' withCredentials step or environment variables that Jenkins injects, so the pipeline can use the secret values at runtime without exposing them in logs or code.

Q6: How does service discovery and load balancing work in Kubernetes for your applications?

A: Kubernetes uses Services to enable discovery and load balancing. Each Service gets a stable IP (ClusterIP for internal access) and DNS name, and it selects pods by labels. Internally, kube-proxy routes traffic from the Service IP to the pod IPs. For external access, you might use a Service of type LoadBalancer or NodePort, or an Ingress resource for HTTP routing, which directs outside traffic to the correct Service.

Q7: What is the difference between a Deployment and a StatefulSet in Kubernetes, and when would you use a StatefulSet?

A: A Deployment manages stateless applications – it treats all pods interchangeably and handles scaling and rolling updates for them. A StatefulSet is for stateful applications; it provides each pod a unique identity (stable hostname) and persistent storage. I’d use a StatefulSet for applications like databases or Kafka, where each instance needs a consistent identity or storage, whereas Deployments are fine for typical stateless web services.

Q8: One of your Kubernetes pods is stuck in a CrashLoopBackOff. How do you troubleshoot it?

A: First, I’d describe the pod (kubectl describe pod <name>) to see if there are any obvious errors or event messages. Then I’d check the pod’s logs using kubectl logs, possibly with -p flag to see logs from a previously crashed container. Those logs usually show the error causing the crash. Depending on the error, I might exec into a running container for deeper inspection or check if a misconfiguration (like a bad env variable or missing file) is causing the app to exit.

Q9: You need to update a configuration for a live application in Kubernetes and deploy a new version without downtime. How would you achieve this? (Assume it’s handles IoT devices connection via Socket/MQTT and 1000s of Devices are already connected)

A: I would perform a rolling update using a Deployment. I'd update the Deployment (or the image/tag if config is baked in, or mounted ConfigMap) so that Kubernetes creates new pods with the updated version. I’d ensure a readiness probe is set, so each new pod is marked ready only after it fully starts. Kubernetes will then gradually switch out old pods for new ones one by one, ensuring at least N-1 pods are always serving, achieving zero downtime deployment.

Q10: What AWS services can you use to implement a CI/CD pipeline without Jenkins?

A: AWS offers CodePipeline as the orchestration service for CI/CD. Along with it, I’d use CodeCommit or GitHub as the source, CodeBuild for building and testing, and CodeDeploy for deployment (if deploying to EC2 or on-prem servers). For containers, I might use AWS CodeBuild to build Docker images and then use CodeDeploy or Amazon ECS/EKS with maybe CodePipeline integration to deploy the containers. These services together provide a Jenkins-free CI/CD solution.

Q11: How would you design a highly available and scalable web application architecture on AWS?

A: I would use multiple Availability Zones for high availability. For example, put instances in an Auto Scaling group spread across AZs behind an Elastic Load Balancer, so if one AZ goes down, traffic goes to others. The database would be a managed service like RDS with Multi-AZ enabled or a distributed database. I’d also leverage scaling – Auto Scaling to add instances under load, and perhaps use stateless app servers so they can scale horizontally easily. For components like cache, use managed services like ElastiCache, also in multi-AZ where possible.

Q12: Why is Terraform state important, and how do you manage it in a team?

A: Terraform state tracks the real-world resources created by your configs. It’s important because Terraform uses it to determine what to add, change, or destroy. In a team, we store state remotely (for example, in an S3 bucket with DynamoDB for locking) so that everyone uses a single source of truth and we avoid collisions. Remote state also helps in collaboration by locking to prevent simultaneous runs and in maintaining backups of the state file.

Q13: How can you reuse Terraform configurations for multiple environments (like dev, staging, prod)?

A: One way is to use Terraform modules – encapsulate resource configs into modules and call them for each environment with different variables. Each environment can have its own variables (like sizes, counts) but reuse the same module code. Alternatively, use separate workspaces or separate state files for each environment but keep the configurations DRY by factoring common code. The key idea is to avoid duplicating code by parameterizing it for different environments.

Q14: If someone manually changes a cloud resource that is managed by Terraform (outside of Terraform), what happens when you run terraform plan next time?

A: The next terraform plan will detect that the actual state diverged from the expected state in the Terraform state file. It will show those differences as changes. For example, if someone changed a setting on AWS manually, Terraform might plan to change it back or flag it as a conflict. The proper approach is to import or adjust the state: either accept the change by updating Terraform code (or doing a terraform import if it was a new resource) or let Terraform overwrite it by applying the plan, depending on which outcome is desired.

Q15: How does Ansible ensure that running the same playbook multiple times won’t break the system (idempotence)?

A: Ansible modules are idempotent by design. That means each task checks the current state before making changes. For example, the apt module checks if a package is already installed before trying to install it. Because of this, running a playbook again will usually have no effect if everything is already as desired (tasks will report "ok" instead of "changed"). Ensuring to use the right modules and state=present/absent parameters keeps tasks idempotent.

Q16: An Ansible playbook works on most servers but fails on one particular server. How would you troubleshoot this?

I would run the playbook with increased verbosity (e.g., ansible-playbook -vvv) targeting that one host to get more details on the failure. The error might point to an environmental issue on that server (like missing packages, different OS, or permissions). I’d also check that the inventory and host variables for that server are correct. Once I identify the cause (say a package name is different on that distro or the user lacks sudo rights), I’d fix the environment or adjust the playbook to handle that difference, and then rerun the playbook.

Q17: What are the key differences between a Docker container and a virtual machine (VM)?

A: A Docker container is much lighter weight than a VM. Containers share the host’s operating system kernel, whereas a VM includes a full OS stack including its own kernel. This means containers use less resources and start up very quickly, but they are less isolated than VMs (since VMs are fully isolated by a hypervisor). In short, VMs emulate hardware completely, and containers isolate at the process level using the host OS.

Q18: What are some ways to reduce the size of a Docker image?

A: Use a lightweight base image (for example, alpine Linux) if possible. Clean up any temporary files or package caches in the Dockerfile (often by using --no-cache and removing apk/apt caches). Multi-stage builds are also a common technique: build your application in one stage and then copy only the necessary artifacts into a smaller runtime image. Also, ensure you’re not copying unnecessary files by using a .dockerignore file.

Q19: You run docker run -d myapp:latest to start a container, but it exits immediately. What could be the cause and how do you investigate?

If a container stops right away, it usually means the application process inside it crashed or exited. I would check the container’s logs (docker logs <container-id>) to see error output. It might be an application error, or perhaps the container’s CMD was misconfigured and the process ended. I could also run it in the foreground (remove -d) or with an interactive mode to see what’s happening. Often it’s an error like "file not found" for the entrypoint or some unhandled exception causing the app to quit.

Q20: What monitoring tools have you used, and what do they monitor?

A: I've used Prometheus for metrics monitoring (it collects time-series metrics like CPU, memory, request rates, etc., and we visualize those in Grafana). For logs, I have experience with the ELK/EFK stack (Elasticsearch, Logstash/Fluentd, Kibana) to aggregate and search application logs. I've also used cloud-specific tools like AWS CloudWatch to monitor AWS resource metrics and set up alarms.

Q21: How do you set up alerts for critical issues in a production environment?

A: We define alert rules on key metrics and logs. For example, using Prometheus/Alertmanager, I’d set thresholds on metrics like high CPU for prolonged time, error rates, or no heartbeat from an application. When conditions meet those thresholds, an alert is sent out (via email, Slack, or PagerDuty). The idea is to catch issues early, so I also set up alerts for things like high memory usage, disk nearly full, or important service down. Each alert is tuned to reduce noise (avoiding flapping) so that when it fires, it's actionable.

Q22: One microservice in production is responding slowly and throwing errors. How would you use monitoring and logs to identify the cause?

A: I would first check our monitoring dashboards for that service – look at its CPU, memory, and latency graphs to see if it's under high load or hitting resource limits. I’d also check if any dependency (like a database or external API) is showing issues at the same times (correlate metrics). Then, I'd dive into the logs for that service (via our centralized logging system) to see error messages or stack traces. If we have distributed tracing (like Jaeger or X-Ray), I'd use that to follow a sample request through the system to pinpoint where the slowdown or error occurs (for example, a slow database query or a timeout calling another service).