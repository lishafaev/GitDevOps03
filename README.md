# Lesson3
***Docker.***

1. create Dockerfile_Alpine 

FROM alpine:latest
RUN mkdir /home/TestAlpine
WORKDIR /home/TestApline
RUN apk add git
ENTRYPOINT ["git", "clone"]

execute:
docker build -f ./Dockerfile_Alpine -t my_test_apline:test_alpine_1 .

execute:
mkdir -p /home/max/Docker/TestAlpineLoc
docker run -v /home/max/Docker/TestAlpineLoc:/home/TestApline my_test_apline:test_alpine_1 https://github.com/lishafaev/SecondRepos.git

2. Create Dockerfile_nginx

FROM nginx
COPY nginx.conf /etc/nginx/nginx.conf
COPY index.html /etc/nginx/html/index.html
CMD nginx -g 'daemon off;'

- Copy default nginx.conf to custom dir:
cp /etc/nginx/nginx.conf /home/max/GitDevOps03
- edit nginx.conf, add in tag http:
        server {
                listen 8080;
        }

- Create custom index.html in custom dir.
- Create docker image:
docker build -f ./Dockerfile_nginx -t my_test_nginx:test_nginx_1 .
- Run docker with port forwarding:
docker run -it -p 83:8080 my_test_nginx:test_nginx_1
