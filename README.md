# Lesson 4
***Docker.***

- create dir for agent  
mkdir -p teamcity-build-agent/conf  
- create dir for server  
mkdir -p teamcity-server/data  
mkdir -p teamcity-server/log  

- run teamcity-server container
docker run -it --name teamcity-server-instance  \
    -v /home/max/teamcity-server/data:/data/teamcity_server/datadir \
    -v /home/max/teamcity-server/log:/opt/teamcity/logs  \
    -p 8111:8111 \
    jetbrains/teamcity-server

- run teamcity-agent container
docker run -it -e SERVER_URL="172.17.0.1:8111"  \
    -v /home/max/teamcity-build-agent/conf:/data/teamcity_agent/conf  \
-v /var/run/docker.sock:/var/run/docker.sock  \
    jetbrains/teamcity-agent
