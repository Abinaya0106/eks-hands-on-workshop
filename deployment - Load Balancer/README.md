# Deploy AWS Load Balancer Controller using its Helm Chart:

a. Add the EKS repository to Helm:
helm repo add eks https://aws.github.io/eks-charts

b. Install the TargetGroupBinding CRDs: kubectl apply -f https://raw.githubusercontent.com/aws/eks-charts/master/stable/aws-load-balancer-controller/crds/crds.yaml

c. Install the AWS Load Balancer controller using the previously created service account :
helm upgrade -i aws-load-balancer-controller eks/aws-load-balancer-controller \
  -n kube-system \
  --set clusterName=mythicaleks-eksctl-dev \
  --set serviceAccount.create=false \
  --set enableServiceMutatorWebhook=false \
  --set serviceAccount.name=aws-load-balancer-controller

  d. Verify that the deployment was successful and the controller started:

  # kubectl logs -n kube-system deployments/aws-load-balancer-controller
  To Check :
  1.Controller started successfully
  "starting server","name":"health probe","addr":"[::]:61779"
✔ Health probe server started
✔ Pod is alive and responding

  2. Registering webhook
"path":"/mutate-v1-pod"
"path":"/mutate-v1-service"
"path":"/validate-elbv2-k8s-aws-v1beta1-ingressclassparams"
"path":"/validate-networking-v1-ingress"
✔ This means:

Controller can intercept & validate Ingress

ALB resources will be created correctly

Kubernetes ↔ AWS integration is working

👉 If this was broken, Ingress would never work

 3. Metric Server Started : "Starting metrics server","bindAddress":":8080"
✔ Prometheus-style metrics enabled
✔ Shows production-readiness

4. Leader Election Started :
attempting to acquire leader lease kube-system/aws-load-balancer-controller-leader
✔ Correct behavior
✔ Ensures only one controller manages ALBs even if replicas > 1

  # kubectl -n kube-system get deployments
