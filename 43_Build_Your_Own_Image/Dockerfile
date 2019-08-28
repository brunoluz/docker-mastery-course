# NOTE: this example is taken from the default Dockerfile for the official nginx Docker Hub Repo
# https://hub.docker.com/_/nginx/
# NOTE: This file is slightly different than the video, because nginx versions have been updated 
#       to match the latest standards from docker hub... but it's doing the same thing as the video
#       describes
FROM node:6-alpine
# all images must have a FROM
# usually from a minimal Linux distribution like debian or (even better) alpine
# if you truly want to start with an empty container, use FROM scratch

EXPOSE 3000
# expose these ports on the docker virtual network
# you still need to use -p or -P to open/forward these ports on host

RUN apk add --update tini

RUN mkdir -p /opt/apl/mynodejsapp

WORKDIR /opt/apl/mynodejsapp

COPY BasicExpressSite-master/. /opt/apl/mynodejsapp/

RUN npm install

# CMD ["node", "app.py"]
CMD ["tini", "--", "node", "app.js"]
# required: run this command when container is launched
# only one CMD allowed, so if there are multiple, last one wins
