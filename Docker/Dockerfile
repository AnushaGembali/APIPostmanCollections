#Use Official Node.js 22.19.0 as base image
FROM node:22.19.0

#Set the current working directory in container
WORKDIR /app

#Install Newman globally
RUN npm install -g newman

#Install Newman Html Report
RUN npm install -g newman-reporter-html

#Install newman Reporter Htmlextra
RUN npm install -g newman-reporter-htmlextra

#COPY postman collection.json and env.json files to the working directory
COPY GoRestApiWorkflowCollection.json .
COPY GoRestEnv.json .

#Set the command to run newman and execute postman collection
CMD ["newman", "run", "GoRestApiWorkflowCollection.json", "-e", "GoRestEnv.json", "-r", "cli,html,htmlextra"]