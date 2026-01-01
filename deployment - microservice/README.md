cd ~/environment/workshop-1/app/like-service
LIKE_ECR_REPOSITORY_URI=$(aws ecr describe-repositories | jq -r .repositories[].repositoryUri | grep like)
docker build -t like-service .
docker tag like-service:latest 716713632458.dkr.ecr.us-east-1.amazonaws.com/like-service:latest
docker push 716713632458.dkr.ecr.us-east-1.amazonaws.com/like-service:latest

docker tag like-service:latest \
716713632458.dkr.ecr.us-east-1.amazonaws.com/like-service:latest


# Manifests file for like-app 

kubectl apply -f likeservice-app.yaml

![likeservice](<../architecture/like service.png>)


kubectl logs deployments/mythical-mysfits-like
