
#BUILD Phase
#1 Use an existing docker image as a base
# FROM node:alpine as builder
FROM node:alpine

#2 Set work directory and coppy package.json
WORKDIR '/app'
COPY package*.json ./

#3 Download and install a dependencies
RUN npm install

#4 Copy all source code into the container
COPY . .

#5 Tell the image what to do when it starts as a container
RUN npm run build


#PRODUCTION Phase
#1 Use an existing docker image as a base
FROM nginx 
EXPOSE 3000

#2 Copy the custom configuration file to the container
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

#3 Copy everything from builder (/app/builder) phase to working directory of Nginx
# COPY --from=builder /app/build /usr/share/nginx/html
COPY --from=0 /app/build /usr/share/nginx/html