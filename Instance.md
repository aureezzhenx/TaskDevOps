FRONTEND (wayshub-frontend): 172.31.48.93
DATABASE (mysql, sequlize): 172.31.50.114
BACKEND (wayshub-backend): 172.31.54.248

# FRONTEND PRIVATE
ssh jouziefrontend@172.31.48.93

# DATABASE PRIVATE
ssh jouziedatabase@172.31.50.114

# BACKEND PRIVATE
ssh jouziebackend@172.31.54.248

# REVERSE PROXY
ssh jouzie@jouzie.onlinecamp.id

# CICD PRIVATE
ssh jouziejenkins@cicdserver.jouzie.onlinecamp.id

# BELAJAR DOCKER
ssh aureezzdocker@docker.onlinecamp.id
ssh aureezzdb@database.onlinecamp.id

cd ~/.ssh && ssh-keygen
ssh-add ~/.ssh/namassh

wayshub-frontend/src/config/api.js
wayshub-backend/config/config.json

docker build -t aureezzhenx/backend:v1.0.0 .
docker container create --name aureezzbackend -p 5000:5000 aureezzhenx/backend:v1.0.0
