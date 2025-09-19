FROM node:22.19.0

WORKDIR /app

# Install Newman
RUN npm install -g newman

# Install Newman Html Report
RUN npm install -g newman-reporter-html

# Install Newman Html Extra Report
RUN npm install -g newman-reporter-htmlextra

# Create results folder
RUN mkdir -p /app/results

# Copy your collection + data file
COPY RunTestsMultipleTimesUsingFilesCol.json /app/
COPY csvfile.csv /app/

# Set the command to run Newman with data-driven testing
CMD ["newman", "run", "/app/RunTestsMultipleTimesUsingFilesCol.json", "-d", "/app/csvfile.csv", "-r", "cli,html,htmlextra", "--reporter-htmlextra-export", "/app/results/datadriventest.html"]