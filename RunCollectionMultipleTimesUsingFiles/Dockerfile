FROM node:22.19.0

WORKDIR /app

# Install Newman + reporters
RUN npm install -g newman newman-reporter-html newman-reporter-htmlextra

# Create results folder
RUN mkdir -p /app/results

# Copy your collection + data file
COPY RunTestsMultipleTimesUsingFilesCol.json .
COPY csvfile.csv .

# Run Newman and always export report to /app/results/datadriventest.html
CMD ["newman", "run", "RunTestsMultipleTimesUsingFilesCol.json", "-d", "csvfile.csv", "-r", "cli,html,htmlextra", "--reporter-htmlextra-export", "/app/results/datadriventest.html"]