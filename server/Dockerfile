#1 Use an existing docker image as abase
FROM node:alpine

WORKDIR "/app"

#2 Download and install a dependencies
COPY ./package.json ./
RUN npm install
COPY ./ ./

#3 Tell the image what to do when it starts as a container
CMD ["npm","run","start"]