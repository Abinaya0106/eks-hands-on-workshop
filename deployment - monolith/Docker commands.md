project-root/
│
├── Dockerfile
└── service/
    ├── requirements.txt -> flask
    └── mythicalMysfitsService.py

# Docker Installation 
1. Update system
sudo dnf update -y
2. Install Docker
sudo dnf install docker -y
3. Start Docker
sudo systemctl start docker
4. Enable Docker on boot
sudo systemctl enable docker
5. Add user to docker group
sudo usermod -aG docker ec2-user/ next do reboot/verify “groups” / You should see docker

# requirements.txt
Flask==2.2.5
flask-cors==3.0.10
boto3==1.34.41
markupsafe==2.1.3

# Docker build : docker build -t monolith-service .
# Docker run : docker run -d -p 8081:80 \
  -e AWS_DEFAULT_REGION=us-east-1 \
  -e DDB_TABLE_NAME=$TABLE_NAME \
  monolith-service

# To get inside container : docker exec -it 67ff4c120fcb sh

docker run -d -p 8081:80 \
  -e AWS_DEFAULT_REGION=us-east-1 \
  -e DDB_TABLE_NAME=MysfitsTable \
  -e AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID \
  -e AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY \
  monolith-service

  # RESTART CONTAINER
docker stop $(docker ps -q)
docker rm $(docker ps -aq)

docker run -d -p 8081:80 \
  -e AWS_DEFAULT_REGION=us-east-1 \
  -e DDB_TABLE_NAME=MysfitsTable \
  -e AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID \
  -e AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY \
  monolith-service


